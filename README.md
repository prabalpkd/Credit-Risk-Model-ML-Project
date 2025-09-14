# Prudent Partners: Credit Risk Modelling

This project builds a **Credit Risk Modelling** system for *Prudent Partners* to assess the probability of loan default, assign credit scores, and classify borrower risk levels.  
It combines **data processing, feature engineering, machine learning, and a Streamlit app** for real-time predictions.

---

## 📸 Live Demo

Check out the live Streamlit app here: [Prudent Partners: Credit Risk Modelling](https://credit-risk-model-ml-project-02.streamlit.app/)

---

## 🖥️ Streamlit App Interface

![App Screenshot](https://github.com/prabalpkd/Credit-Risk-Model-ML-Project/blob/main/Real-Time-Prediction-Interface.png)

---

## 📌 Project Objective
To design and deploy a **machine learning model** that:
- Predicts **default probability** for a borrower.
- Generates a **credit score**.
- Classifies into **risk ratings** (Excellent, Good, Fair, Poor).
- Provides an interactive **Streamlit web interface**.

---

## 📊 Datasets Used

1. **customers.csv** – Demographic and income data:
   - Age, Gender, Marital Status, Employment Status
   - Income, Dependents, Residence Type, Location details

2. **loans.csv** – Loan details:
   - Loan Amount, Tenure, Purpose, Loan Type
   - Processing Fees, GST, Disbursement details

3. **bureau_data.csv** – Credit bureau history:
   - Delinquency Ratio, Days Past Due (DPD)
   - Credit Utilization, Number of Open Loan Accounts

---

## ⚙️ Methodology & Steps Performed

### **1. Data Loading**
- Imported all datasets using `pandas`.
- Checked shapes and previewed data using `.head()` and `.info()`.

### **2. Data Merging**
- Merged `customers.csv`, `loans.csv`, and `bureau_data.csv` on `cust_id` to form a single dataset.

### **3. Train-Test Split (Before Preprocessing)**
- Split the dataset into `df_train` and `df_test` to **prevent data leakage**.
- Used `train_test_split()` from scikit-learn.

### **4. Duplicate Removal**
- Checked for duplicates using `.duplicated().sum()`.
- Removed duplicate entries.

### **5. Exploratory Data Analysis (EDA)**
#### **Numeric Features**
- Summary statistics using `.describe()`.
- Visualized distributions using `seaborn` histograms and boxplots.

#### **Categorical Features**
- Value counts for categorical columns.
- Bar plots for category distributions.

### **6. Outlier Detection & Treatment**
Applied business rules to detect and treat outliers:
- **Processing Fees** > 3% of loan amount → treated as outlier.
- **GST** > 20% of loan amount → treated as outlier.
- **Net Disbursement** > loan amount → treated as anomaly.
- Handled anomalies using capping/replacement.

### **7. Missing Value Treatment**
- Checked missing values using `.isnull().sum()`.
- Imputed with median for numeric columns, mode for categorical.

### **8. Feature Engineering**
Created domain-specific credit risk metrics:
- **Loan to Income Ratio (LTI)** = Loan Amount / Income.
- **Delinquency Ratio** = (Months Delinquent / Total Months) × 100.
- **Avg DPD per Delinquent Month** = Total DPD / Delinquent Months.
- **Credit Utilization Ratio** from bureau data.
- **Open Loan Accounts** count.
- Encoded Residence Type, Loan Purpose, and Loan Type.

### **9. Encoding & Scaling**
- Used **One-Hot Encoding** for categorical variables.
- Applied **MinMaxScaler** for numeric features.

### **10. Class Imbalance Handling**
- Observed imbalance in default vs. non-default labels.
- Used **SMOTE Tomek** oversampling to balance classes.

### **11. Model Training**
Trained multiple models:
- **Logistic Regression**
- **Random Forest Classifier**
- Compared using metrics: Accuracy, Precision, Recall, F1-score, ROC-AUC.

### **12. Model Evaluation**
- ROC Curve plotting.
- Selected best-performing model for deployment.

### **13. Credit Scoring & Risk Rating**
- Converted predicted probabilities into credit scores (range 300–900).
- Risk ratings assigned:
  - **Excellent**: 800+
  - **Good**: 700–799
  - **Fair**: 600–699
  - **Poor**: < 600

### **14. Streamlit App Development**
- Built an interactive interface with input fields for borrower details.
- Calculates:
  - **Default Probability**
  - **Credit Score**
  - **Risk Rating**
- Designed clean UI with easy-to-read results.

---

**Inputs:**
- Age, Income, Loan Amount, Loan Tenure
- Avg DPD, Delinquency Ratio, Credit Utilization
- Open Loan Accounts, Residence Type, Loan Purpose, Loan Type

**Outputs:**
- **Default Probability** (e.g., 66.77%)
- **Credit Score** (e.g., 499)
- **Rating** (e.g., Poor)

---

👤 Author
Prabal Kumar Deka
