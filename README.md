# 🌿 Plant Disease Detection using Deep Learning

An end-to-end image processing and deep learning project that detects plant diseases from leaf images. This project utilizes **Transfer Learning (MobileNetV2)** and **Data Augmentation** to achieve high accuracy on the PlantVillage dataset. It is optimized to run seamlessly in Google Colab with GPU acceleration.

## 🚀 Features
* **Transfer Learning:** Uses the pre-trained MobileNetV2 architecture for rapid, highly accurate feature extraction.
* **Real-time Data Augmentation:** Prevents overfitting by dynamically flipping and rotating images during training.
* **Automated Kaggle Integration:** Downloads and prepares the massive PlantVillage dataset directly via the Kaggle API.
* **Custom Inference Engine:** Uses OpenCV to process user-uploaded images and visually display the predicted disease and confidence score.

## 🛠️ Technologies & Libraries
* **Python 3.x**
* **TensorFlow / Keras** (Model creation and training)
* **OpenCV** (Image processing and visual output)
* **NumPy** (Matrix manipulations)
* **Google Colab API** (File uploading and image patching)

## 📊 Dataset
This project uses the official **PlantVillage Dataset** hosted on Kaggle. 
* Contains over 54,000 curated images of leaves.
* Covers 14 different crop species (Apple, Corn, Tomato, Potato, etc.).
* Categorized into **38 distinct classes** (Healthy and Diseased).

---

## ⚙️ Setup and Installation (Google Colab)

To run this project, we recommend using [Google Colab](https://colab.research.google.com/) for free GPU access.

### 1. Prerequisites (Kaggle API)
You will need a Kaggle account to download the dataset.
1. Go to [Kaggle](https://www.kaggle.com/) -> Profile -> Settings.
2. Click **Create New Token** to download your `kaggle.json` API key.

### 2. Environment Setup
1. Open a new Google Colab notebook.
2. Go to **Runtime > Change runtime type** and select **T4 GPU**.
3. Copy the code cells provided in this project into your notebook.

---

## 📖 Usage Instructions

Run the notebook cells sequentially:

1. **Setup & Imports:** Initializes TensorFlow and OpenCV.
2. **Dataset Preparation:** Upload your `kaggle.json` when prompted. The script will automatically download the dataset, unzip it, and split it into Training (80%) and Validation (20%) sets.
3. **Model Building:** Constructs the MobileNetV2 architecture and adds dense layers configured for 38 classes.
4. **Training:** Trains the model for 10 Epochs (takes ~5 minutes on a GPU).
5. **Prediction:** Run the inference cell to upload a custom leaf image (e.g., `.jpg` or `.png`). The model will analyze the image and output the predicted condition with a confidence score.

---

## ⚠️ Common Troubleshooting

If you run into issues on Google Colab, here is how to fix them:

* **`NameError: name 'train_dataset' is not defined`**
    * *Cause:* Google Colab wiped its memory after a restart or inactivity.
    * *Fix:* You must re-run the dataset loading cells before trying to train or predict. 
* **`AttributeError: '_PrefetchDataset' object has no attribute 'class_names'`**
    * *Cause:* TensorFlow strips class names when optimizing datasets for speed.
    * *Fix:* The prediction script uses `os.listdir()` to read the 38 class names directly from the extracted Kaggle folders instead. Ensure the dataset is unzipped in your Colab files.
* **`NameError: name 'files' is not defined`**
    * *Cause:* Missing library import for the Colab upload widget.
    * *Fix:* Ensure `from google.colab import files` is at the very top of your prediction cell.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.
