# Machine Learning Feature Selection Analysis

This project implements and analyzes feature selection algorithms for machine learning classification tasks. The goal is to determine which subset of features produces the highest classification accuracy for a given dataset.

The system evaluates feature subsets using **Forward Selection** and **Backward Elimination**, two classic greedy search strategies used in machine learning feature engineering.

The implementation tests these algorithms across multiple datasets and compares their performance using **Leave-One-Out Cross Validation (LOOCV)**.

---

## Overview

Feature selection plays an important role in machine learning. Large datasets often contain irrelevant or redundant features that reduce model performance and increase computation time.

This project investigates how selecting a subset of relevant features improves classification accuracy.

The system:

- Loads numerical datasets
- Normalizes feature values
- Evaluates feature subsets using nearest-neighbor classification
- Uses LOOCV to measure classification accuracy
- Searches for the optimal feature subset

---

## Implemented Algorithms

### Forward Selection

Forward Selection begins with an empty feature set and iteratively adds the feature that improves classification accuracy the most.

Process:

1. Start with no features
2. Add each remaining feature individually
3. Evaluate accuracy
4. Select the feature that improves accuracy the most
5. Repeat until no improvement occurs

---

### Backward Elimination

Backward Elimination begins with the full feature set and removes features one at a time.

Process:

1. Start with all features
2. Remove each feature individually
3. Evaluate accuracy
4. Remove the feature that improves accuracy the most
5. Repeat until accuracy decreases

---

## Data Normalization

Normalization significantly improves classifier performance.

Features such as **Age** or **Sex** in the Titanic dataset have different value ranges. Without normalization, features with larger numeric ranges dominate distance calculations.

This project applies **Z-score normalization**, which standardizes feature values based on their mean and standard deviation.

Without normalization, the small dataset achieved approximately **61% accuracy**, while normalization improved results to about **95% accuracy**. 

---

## Validation Method

The project evaluates feature subsets using **Leave-One-Out Cross Validation (LOOCV)**.

LOOCV works as follows:

1. Remove one data point from the dataset
2. Train on the remaining points
3. Test on the removed point
4. Repeat for every data point

The average classification accuracy across all runs determines the performance of the feature subset.

---

## Experimental Results

### Small Dataset

| Algorithm | Best Feature Subset | Accuracy |
|----------|--------------------|---------|
| Forward Selection | {3,5} | 92% |
| Backward Elimination | {2,4,5,7,10} | 82% |

---

### Large Dataset

| Algorithm | Best Feature Subset | Accuracy |
|----------|--------------------|---------|
| Forward Selection | {1,27} | 95.5% |
| Backward Elimination | {3–40} | 72.1% |

---

### Titanic Dataset

| Algorithm | Best Feature Subset | Accuracy |
|----------|--------------------|---------|
| Forward Selection | {2} | 78.01% |
| Backward Elimination | {2} | 78.01% |

These results demonstrate that a small number of carefully selected features can outperform large feature sets. 
---

## System Design

The implementation follows an object-oriented design.

Key abstractions include:

- Dataset class  
  Stores training data and metadata.

- DataPoint class  
  Represents individual observations.

- Feature Selection Algorithms  
  Implements forward and backward search strategies.

This modular structure makes the system easier to extend and maintain. 

---

## Challenges

Several technical challenges arose during development:

1. Part Integration  
Earlier algorithm components had to be refactored to support the final system design.

2. Flexible Dataset Parsing  
Datasets vary in feature count, requiring dynamic parsing of feature vectors.

3. Debugging Complexity  
Certain failures produced minimal debugging information, making root cause analysis time-consuming. 

---

## Optimization Opportunities

A potential optimization involves storing a **static training dataset instance**.

Instead of retraining the dataset during each LOOCV iteration, the algorithm could reuse the trained dataset and skip the current test instance. This would reduce computational overhead and improve runtime performance. 

## Repository

Project Repository  
https://github.com/notpandiafox/ML_algorithm_comparison/tree/V3.0

---

## Contributors

Terek Johnson  
Oscar La

---

## Academic Context

Course: Intro to Artificial Intelligence  
Instructor: Professor Neftali M. Watkinson  

University of California, Riverside
