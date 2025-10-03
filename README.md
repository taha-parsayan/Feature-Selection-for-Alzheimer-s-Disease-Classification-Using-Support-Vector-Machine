![GitHub release (latest by tag)](https://img.shields.io/github/v/tag/taha-parsayan/OPETIA?label=Release)
![Static Badge](https://img.shields.io/badge/Neuroimaging%20software-FF0000)
![Static Badge](https://img.shields.io/badge/Data%20Science-CC7722)
![Static Badge](https://img.shields.io/badge/Python-8A2BE2)
![Static Badge](https://img.shields.io/badge/FSL-8A2BE2)
![Static Badge](https://img.shields.io/badge/PET%20/%20MRI-4CAF50)

# Feature Selection for Alzheimer's Disease Classification Using Support Vector Machine

---
### [Publication in IEEE](https://ieeexplore.ieee.org/abstract/document/11165970)
---

This repository contains the code and data analysis pipeline for investigating the effect of feature selection on the classification of Alzheimer's Disease (AD), Mild Cognitive Impairment (MCI), and Normal Cognition (NC) using Support Vector Machines (SVM). The study focuses on leveraging regional cortical and subcortical SUVR (Standard Uptake Value Ratio) and volume features extracted from PET-MRI data.

## Overview

Early and accurate diagnosis of Alzheimer's Disease is critical for effective intervention. This project aims to evaluate the role of feature selection in improving the performance of machine learning models for differentiating between:
- **AD vs. MCI**
- **MCI vs. NC**

We apply statistical tests for feature selection and use SVM classifiers to assess the classification performance.

## Data
The dataset includes:
- **Regional SUVR:** From human brain FDG-PET images
- **Volume Features:** From human brain MRI T1-W images

## Database

This project uses data obtained from the [Alzheimer's Disease Neuroimaging Initiative (ADNI)](http://adni.loni.usc.edu/) database. ADNI is a longitudinal multicenter study designed to develop clinical, imaging, genetic, and biochemical biomarkers for the early detection and tracking of Alzheimer’s disease.

![Image](https://github.com/user-attachments/assets/586cd243-40fd-4011-842f-efd1fd09428a)

## Image processing

All the PET and MRI images were pre-processed using the SPM12 software. The pipeline included:
- Co-registeration of PET to T1 space
- Normalization to the MNI standard space
- Gray matter segmentation

Python was used for:
- Segmentation of 115 ROIs (according to the Harward-Oxford atlas)
- Calculating the average SUVR in every ROI
- Calculating the cerebral volume in every ROI

## Data manipulation
Data manipulation consisted of:
- Outlier handling: outliers were replaced by the group median
- Standard scaling: to remove bias from the dataset

## Feature Selection
Statistical tests such as Levene's test (for variance equality) and two-sample t-tests were used to identify significant regions of interest (ROIs) based on corrected p-values. These selected features were then used in the SVM model.

## Machine Learning
Support Vector Machine (SVM) was implemented with:
- Grid search for hyperparameter optimization.
- RobustScaler and StandardScaler for preprocessing.
- Performance metrics: Accuracy, F1-score, Recall, and Confusion Matrix.

## Visualization
- Plots of SUVR and volume distributions across groups.
- Boxplots comparing SUVR and volume by group.
- Region-wise mean and standard deviation visualizations.

![Image](https://github.com/user-attachments/assets/6be9c8b8-7e10-4689-a78b-fe8dcea4d8c3)

## Project Structure

```plaintext
.
├── Features-2.xlsx        # Input feature dataset
├── README.md              # Project documentation
├── feature_selection.py   # Statistical feature selection pipeline
├── classification.py      # SVM implementation for classification
├── plots.py               # Visualization scripts
└── utils.py               # Utility functions for preprocessing and analysis
```

## How to Use

1. **Setup**: Ensure you have Python 3.8+ and the required libraries installed:
   ```bash
   pip install -r requirements.txt
   ```
2. **Prepare Data**: Place the dataset (`Features-2.xlsx`) in the root directory.
3. **Run Feature Selection**:
   ```bash
   python feature_selection.py
   ```
4. **Train Classifier**:
   ```bash
   python classification.py
   ```
5. **Visualize Results**:
   ```bash
   python plots.py
   ```

## Key Results (will be updated when the paper is published)

### Feature Selection
- Significant ROIs were identified for both SUVR and volume features across AD vs. MCI and MCI vs. NC groups.

### Classification
- Performance metrics for AD vs. MCI and MCI vs. NC:
  - **Accuracy**: `XX%`
  - **F1-Score**: `XX%`
  - **Recall**: `XX%`

### Visualizations
- ROI-wise differences in SUVR and volume for AD, MCI, and NC groups.
- Impact of feature selection on SVM classification performance.

## License
This project is licensed under [Apache License](LICENSE).

## Acknowledgments
The dataset used in this study is sourced from the ADNI database. Special thanks to the research teams contributing to Alzheimer's Disease diagnostics and PET-MRI advancements.
