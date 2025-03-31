# ASL Gesture Classifier — Training Code

This folder contains the training pipeline, preprocessing utilities, and model export scripts for building a  ASL classifier using MediaPipe, MobileNetV2, and TensorFlow Lite.

---

### LINK TO WORKING LOCALHOST APP

[https://github.com/prxyn/ASL_Flask_TFLite](https://github.com/prxyn/ASL_Flask_TFLite)


---

## Dataset (Required)

Due to size limitations, the dataset is **not included in this repository**.

You can get the dataset from:

**Source:**
[https://www.kaggle.com/datasets/lexset/synthetic-asl-alphabet](https://www.kaggle.com/datasets/lexset/synthetic-asl-alphabet)

---

## Folder Setup

After downloading and unzipping the dataset:

1. Place the `Train_Alphabet`and `Test_Alphabet` folder into the `/archive` folder
2. Delete the 'blank' class folder from the dataset

## Model Details

- Base model: `MobileNetV2` with top layer removed
- Fine-tuning via unfreezing top layers
- Post-training quantisation → `.tflite`
- Preprocessing preserves **224×224** aspect ratio

## Installation

Install required packages:

```pip install -r requirements.txt```

## Usage
Each jupyter file outputs its own `.keras` file.
Quantisation converts the final model to `.tflite`

## Notes
- All static gestures are included — including "J" and "Z" — based on the dataset’s representation. (Please refer to the dataset visuals for gesture positioning).
- Model is intended for real-time use with the accompanying inference app.
- The training process was conducted in **multiple iterations**, with each Jupyter notebook representing a key stage:
  1. **Initial prototype** (basic model on a subset of the data)
  2. **Full dataset training**
  3. **Fine-tuning by unfreezing layers**
  4. **Unfreezing + Data augmentation**
  5. **Post-training quantisation and `.tflite` export**

  Each stage outputs its own `.keras` model file for comparison and benchmarking.