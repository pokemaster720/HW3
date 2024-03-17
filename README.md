# Question 2

### 1. Loading and Preparing the Data:
- Loading ARFF File:** It uses `scipy.io.arff.loadarff` to load data from an ARFF file
- DataFrame Creation:** The data loaded is then converted into a pandas DataFrame for easier manipulation.
- Reclassification:** The class labels are reclassified from binary strings to numeric (0 and 1), which is needed for numerical computations downstream.

### 2. Implementing Pearson Correlation Coefficient (PCC):
- Calculation:** `pearson` is defined to calculate the Pearson Correlation Coefficient between two variables. This calculation involves mean normalization and scaling by the standard deviations, reflecting the covariance of the two variables normalized by their standard deviations.
- Purpose:** Pearson Correlation helps in determining the linear relationship between two variables. The closer the coefficient is to 1 or -1, the stronger the correlation. 

### 3. Feature Ranking Based on Pearson Correlation:
- Analysis:** For each feature, it computes the Pearson Correlation with the class labels (Y, 'CLASS'). 
- Ranking:** Features are then ranked based on their absolute correlation values, suggesting that features with higher correlations (closer to 1) might be more influential in predicting the class label.

### 4. LOOCV with KNN Classification:
- KNN_LOOCV Function:** Implements the k-Nearest Neighbors algorithm combined with Leave-One-Out Cross-Validation. This means for each instance in the dataset, the function uses all other instances as training data, predicts the class for the left-out instance, then compares it to its actual class. 
- Accuracy Calculation:** For every subset of features, it calculates the accuracy of classification to find out which subset yields the best performance when used in the KNN classifier.

### 5. Analysis and Results:
- The script aims to answer two questions:
  - (a)** Which features when considered individually, have the greatest absolute Pearson correlation with the class label
  - (b)** When restricting the dataset to these top features, what is the optimal subset size that achieves the highest classification accuracy using KNN with LOOCV?

**Execution and Timing**: The script measures the time taken to perform KNN LOOCV across the selected features, providing insights into the computational cost.

**Results Presentation**: The accuracies for different numbers of top features (`m`) used in classification are tabulated and displayed
