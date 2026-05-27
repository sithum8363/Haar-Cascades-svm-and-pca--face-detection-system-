# Face Recognition using PCA + SVM

This project is a simple **Face Recognition system** built with **OpenCV**, **PCA**, and **SVM**.

The workflow is:

1. Prepare face image data from folders.
2. Detect and crop faces using Haar Cascade.
3. Resize each face to `50 x 50`.
4. Save prepared data as NumPy arrays.
5. Train a PCA + SVM model.
6. Test the trained model on new images.

---

## Project Files

| File | Description |
|---|---|
| `data perpaering (1).ipynb` | Data preparation notebook. Detects faces, crops them, resizes them, and saves `data.npy`, `target.npy`, and `category_dict.npy`. |
| `ds(3).ipynb` | Model training notebook. Loads prepared data, applies PCA, trains SVM, checks accuracy, and saves the trained model. |
| `ds copy(1).ipynb` | Testing/prediction notebook. Loads saved PCA and SVM models and predicts faces from test images. |

---

## Technologies Used

- Python
- OpenCV
- NumPy
- Scikit-learn
- Joblib
- Matplotlib
- Jupyter Notebook

---

## Installation

First install Python packages:

```bash
pip install opencv-python numpy scikit-learn joblib matplotlib notebook
```

Then start Jupyter Notebook:

```bash
jupyter notebook
```

---

## Required Files and Folders

You need this project structure:

```text
Face-Recognition-Project/
│
├── data perpaering (1).ipynb
├── ds(3).ipynb
├── ds copy(1).ipynb
│
├── haarcascade_frontalface_default.xml
│
├── tainin data/
│   ├── person_1/
│   ├── person_2/
│   ├── person_3/
│   └── ...
│
└── testdata/
    ├── image1.jpg
    ├── image2.jpg
    └── ...
```

> Note: In the current code, the training folder name is written as `tainin data`. If your real folder is named `training data`, update the path in the notebooks.

---

## How It Works

### 1. Data Preparation

Notebook:

```text
data perpaering (1).ipynb
```

This notebook:

- Reads images from the training data folder.
- Converts images to grayscale.
- Detects faces using Haar Cascade.
- Crops detected faces.
- Resizes faces into `50 x 50`.
- Flattens each face image into a 1D array.
- Saves:
  - `data.npy`
  - `target.npy`
  - `category_dict.npy`

When a cropped face appears, press:

- `y` to accept/save the face.
- Any other key to skip it.

---

### 2. Model Training

Notebook:

```text
ds(3).ipynb
```

This notebook:

- Loads `data.npy` and `target.npy`.
- Splits the dataset into train and test sets.
- Uses PCA to reduce features.
- Trains an SVM classifier with RBF kernel.
- Prints accuracy and classification report.
- Saves trained files:

```text
SVM-Face Recognition.sav
pca-Face Recognition.sav
```

---

### 3. Face Prediction

Notebook:

```text
ds copy(1).ipynb
```

This notebook:

- Loads the trained SVM model.
- Loads the trained PCA model.
- Reads test images from `testdata`.
- Detects faces.
- Crops and resizes faces.
- Predicts the person name.
- Draws a rectangle and label on the image.

Current label dictionary in the testing notebook:

```python
category_dict = {
    0: 'anura kumara',
    1: 'gotabaya rajapaksa',
    2: 'mahinda rajapaksa',
    3: 'maithripala sirisena',
    4: 'ranil wickremesinghe',
}
```

Change these names according to your own dataset.

---

## How to Run

Run the notebooks in this order:

### Step 1: Prepare Data

Open and run:

```text
data perpaering (1).ipynb
```

This creates:

```text
data.npy
target.npy
category_dict.npy
```

### Step 2: Train Model

Open and run:

```text
ds(3).ipynb
```

This creates:

```text
SVM-Face Recognition.sav
pca-Face Recognition.sav
```

### Step 3: Test Prediction

Open and run:

```text
ds copy(1).ipynb
```

---

## Important Notes

- Make sure `haarcascade_frontalface_default.xml` is inside the project folder.
- Make sure folder paths match your actual folder names.
- Use clear face images for better accuracy.
- PCA `n_components=50` requires enough training samples. If you have very few images, reduce this value.
- OpenCV `cv2.imshow()` works best on local PC, not Google Colab.

---

## Common Errors

### 1. Folder not found

If you get an error like:

```text
FileNotFoundError
```

Check this line:

```python
p = r'tainin data'
```

Make sure the folder exists with the same spelling.

---

### 2. Haar Cascade not loading

Make sure this file exists:

```text
haarcascade_frontalface_default.xml
```

You can download it from OpenCV's official Haar Cascade files.

---

### 3. PCA component error

If you get an error about `n_components=50`, reduce it:

```python
pca = PCA(n_components=10, whiten=True)
```

---

## Future Improvements

- Add real-time webcam face recognition.
- Improve dataset size and quality.
- Use deep learning models like FaceNet or CNN.
- Save and load category labels automatically instead of manually writing them.
- Create a simple GUI for prediction.

---

## Author

Created by **Sithum Marasinghe**.
