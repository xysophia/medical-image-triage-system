# Explainable Medical Image Triage System

This project is an interactive chest X-ray triage demo that compares a baseline CNN and a fine-tuned ResNet18 model for PneumoniaMNIST classification. The system predicts whether an uploaded chest X-ray image is normal or pneumonia, estimates prediction confidence, assigns a triage-style risk level, and generates Grad-CAM visual explanations.

## Project Overview

The goal of this project is to demonstrate how machine learning can support medical image triage. It is designed as a decision-support prototype, not as an autonomous diagnostic system.

The application allows users to:

* Upload a chest X-ray image
* Select either the baseline CNN or fine-tuned ResNet18 model
* View the predicted class: Normal or Pneumonia
* View the model confidence score
* Receive a confidence-based triage recommendation
* Inspect Grad-CAM heatmap and overlay explanations

## Models

This project compares two models:

1. **Baseline CNN**
   A convolutional neural network trained from scratch as a benchmark model.

2. **Fine-Tuned ResNet18**
   A transfer learning model adapted for binary PneumoniaMNIST classification.

## Dataset

The project uses PneumoniaMNIST from MedMNIST.

* Task: Normal vs. Pneumonia classification
* Image type: grayscale chest X-ray images
* Preprocessing:

  * Resize images to 224 × 224
  * Convert grayscale images to 3-channel format
  * Normalize images for model input

## Model Performance

| Model               | Accuracy | Precision | Recall / Sensitivity |     F1 | False Positives | False Negatives |
| ------------------- | -------: | --------: | -------------------: | -----: | --------------: | --------------: |
| Baseline CNN        |   0.8077 |    0.7722 |               0.9821 | 0.8646 |             113 |               7 |
| Fine-Tuned ResNet18 |   0.8974 |    0.8606 |               0.9974 | 0.9240 |              63 |               1 |

The fine-tuned ResNet18 achieved stronger overall performance and reduced false negatives, which is especially important in a triage-oriented medical imaging task.

## Demo Application

The Gradio app integrates model prediction, confidence scoring, triage logic, and Grad-CAM explainability. For each uploaded image, the app returns:

* Prediction summary
* Confidence score
* Risk level
* Triage recommendation
* Grad-CAM heatmap
* Grad-CAM overlay

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the app:

```bash
python app/app.py
```

Then open the local Gradio URL in your browser.

## Repository Structure

```text
app/              Gradio demo application
assets/           Demo screenshots and representative Grad-CAM results
models/           Trained model checkpoint files
notebooks/        Data processing, baseline CNN, and transfer learning notebooks
requirements.txt  Python dependencies
presentation.pdf  Final project presentation
```

## Limitations

This project is a course project and prototype. It is not intended for real clinical deployment. PneumoniaMNIST images are low-resolution, so Grad-CAM should be interpreted as a general model attention visualization rather than precise clinical localization. The system is intended to support clinical review workflows, not replace doctors or radiologists.

## My Contributions

* Prepared the dataset and preprocessing pipeline
* Built and evaluated the baseline CNN model
* Compared baseline CNN performance with the fine-tuned ResNet18 model
* Reported triage-relevant evaluation metrics including precision, recall, F1-score, false positives, and false negatives
* Integrated model outputs into an interactive Gradio demo structure
