# 《STATISTICAL-PREDICTION-AND-MACHINE-LEARNING》
- Project 4 – Wave Dataset Binary Classification Analysis
- 2024/6/7

---

## **Project Overview**

This project employs the renowned Wave dataset, originally introduced by Breiman et al. in 1984 and later modified by Rakotomalala in 2005. The objective is to tackle a binary classification problem using regression-based approaches combined with variable selection methods, namely Stepwise Variable Selection (including Forward Selection and Backward Elimination) and LASSO. The study aims to identify the most relevant variables and evaluate classification performance using a test dataset.

---

## **Dataset Background**
- **Original Design:** Introduced in 1984 with 3 classes and 21 variables.
- **Wave Generation:** Variables were generated from random combinations of two of three waveforms, with added noise to simulate real-world conditions.
- **Modifications by Rakotomalala (2005):**
  - Increased to 33,334 samples.
  - Added 100 noise features unrelated to the classification task.
  - Simplified to a binary classification task using the first two of the original three classes.

---

## **Dataset Structure**
- **Training Samples:** 10,000
- **Testing Samples:** 10,000
- **Total Features:** 121
  - **Active Variables:** 21 features associated with the waveforms.
  - **Noise Variables:** 100 irrelevant features.
- **Target Variable (y):** Binary class label

---

## **Methodology**

### **Objectives:**
- Apply regression models for binary classification.
- Perform variable selection and evaluate model performance on test data.
- Compare the effectiveness of Stepwise Variable Selection and LASSO.

### **Approaches:**
1. **Stepwise Variable Selection**  
   - **Forward Selection:** Starts with no variables, adds the most significant one step-by-step.
   - **Backward Elimination:** Starts with all variables, removes the least significant ones iteratively.
   - **Criterion:** Significance level (e.g., 1%).

2. **LASSO (Least Absolute Shrinkage and Selection Operator)**  
   - Uses L1 regularization to shrink coefficients and eliminate irrelevant variables.

3. **Model Training and Evaluation**  
   - Fit models on 10,000 training samples.
   - Evaluate classification error on 10,000 test samples.

### **Evaluation Focus:**
- Key variables selected by each method.
- Comparative effectiveness in removing noise and retaining active features.
- Impact on classification error and model generalization.

---

## **Results and Analysis**

### **Models Compared:**
- **Model 1:** Trained on all 121 features.
- **Model 2:** Trained on 15 selected features using feature selection.

### **Key Findings:**
- **Effective Feature Reduction:**
  - Model 2 (15 features) achieved nearly identical or slightly better metrics compared to Model 1 (121 features).
  - Feature count reduced by 87.6% (106 features), indicating many features may be redundant or noise.

- **Improved Computational Efficiency:**
  - Model 2 is lightweight and faster to train/predict.
  - Suitable for large-scale or real-time applications.
  - Significantly lower memory/storage requirements, ideal for constrained environments.

### **Performance Metrics:**
| Metric        | Model 1 (121 Features) | Model 2 (15 Features) | Difference  |
|---------------|-------------------------|------------------------|-------------|
| Accuracy      | 0.9221                  | 0.9238                 | **+0.0017** ↑ |
| Precision     | 0.9135                  | 0.9152                 | **+0.0017** ↑ |
| Recall        | 0.9311                  | 0.9327                 | **+0.0016** ↑ |
| F1 Score      | 0.9222                  | 0.9239                 | **+0.0017** ↑ |
| AUC-ROC       | 0.9803                  | 0.9812                 | **+0.0009** ↑ |

### **Why Model 2 Performs Well with Fewer Features:**
1. **Overfitting Risk with Too Many Features:**
   - Many features may have low relevance or multicollinearity, hurting generalization.
   - Feature selection (LASSO, Stepwise) removes noisy variables and improves robustness.

2. **High Dimensionality Challenges:**
   - In high dimensions (121 features), models struggle to isolate truly influential variables.
   - Dimensionality reduction clarifies important patterns and can improve performance.

3. **Sufficiency of Core Features:**
   - A small set of powerful features may capture most classification-relevant information.
   - Additional features offer diminishing returns and may introduce noise.


