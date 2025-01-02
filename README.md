### Abstract
By examining around 5000 patients, I aim to classify cases based on factors such as BMI and average glucose levels to determine the risk of brain stroke. Using R, I am developing a predictive model, a logistic regression model, which seeks to identify high-risk patients and provide insights into which indicators are most likely to contribute to brain stroke.

## Background
A stroke is a serious medical condition caused by poor blood flow to the brain, leading to cell death. Symptoms include sudden weakness or numbness on one side of the body, difficulty speaking, dizziness, and vision loss. Early diagnosis and treatment are crucial, as long-term complications can include permanent disability or pneumonia. Risk factors such as high blood pressure, diabetes, and smoking highlight the importance of prevention strategies, including managing health conditions and lifestyle changes. In this project, I use the logistic regression to predict and identify high-risk patients.
 
## Getting the Dataset
Access data from Kaggle: 

[Brain Stroke Dataset on Kaggle](https://www.kaggle.com/datasets/jillanisofttech/brain-stroke-dataset/data)


## Data Description
I utilize a dataset focused on stroke prediction and risk factors. Strokes, a leading cause of morbidity,
are classified into ischemic and hemorrhagic types, each with distinct causes and outcomes. The dataset
I use includes demographic, lifestyle, and medical variables such as age, gender, hypertension, heart
disease, BMI, average glucose level, and smoking status. By analyzing these factors, I aim to explore
patterns and build predictive models for stroke occurrence, thus helping us to understand stroke risk
factors better.

1) gender: "Male", "Female" or "Other"

2) age: age of the patient

3) hypertension: 0 if the patient doesn't have hypertension, 1 if the patient has hypertension

4) heart disease: 0 if the patient doesn't have any heart diseases, 1 if the patient has a heart disease 5) Ever-married: "No" or "Yes"

6) work type: "children", "Govtjov", "Never worked", "Private" or "Self-employed"

7) Residencetype: "Rural" or "Urban"

8) avg glucose level: average glucose level in blood

9) BMI: body mass index

10) smoking_status: "formerly smoked", "never smoked", "smokes" or "Unknown"*

11) stroke: 1 if the patient had a stroke or 0 if not

## Conclusion
I fit the logistic regression models by using forward selection, backward elimination, and stepwise selection(both). They all have AIC = 1587.269 and they reach the same model. Thus I chose the backward selection model.

### Coefficients:

|                      | Estimate   | Std Error| P Value  |
|----------------------|------------|----------|----------|
|(Intercept)           | -7.454288  | 0.359226 | < 2e-16  |
| **Age**              | 0.068538   | 0.005162 | < 2e-16  |
| **Hypertension**     | 0.403676   | 0.163018 | 0.013276 |
| **Heart Disease**    | 0.318865   | 0.187915 | 0.089724 |
| **Avg_glucose_level**| 0.004111   | 0.001168 | 0.000431 |

The confusion matrix gets an accuracy of 0.75.

### Assumption Checking:

#### Assumption 1: Multicollinearity checking

| **Variable**       | **GVIF** | **Df** | **Adjusted VIF (GVIF^(1/(2*Df)))** |
|--------------------|----------|--------|------------------------------------|
| gender            | 1.046    | 1      | 1.023                              |
| age               | 1.452    | 1      | 1.205                              |
| hypertension      | 1.065    | 1      | 1.032                              |
| heart disease     | 1.091    | 1      | 1.044                              |
| ever married      | 1.109    | 1      | 1.053                              |
| work type         | 1.428    | 3      | 1.061                              |
| Residence type    | 1.009    | 1      | 1.005                              |
| avg glucose level | 1.117    | 1      | 1.057                              |
| bmi               | 1.116    | 1      | 1.056                              |
| smoking status    | 1.114    | 3      | 1.018                              |

Variance Inflation Factor (VIF) is used to detect multicollinearity among independent variables. A VIF
value below 2 indicates a low correlation. From the above table, since all variables from our dataset have VIF
values below the stricter threshold of 2, the multicollinearity is negligible for this dataset.

#### Assumption 2: Linearity checking

| **Variable**              | **Estimate**  | **Std. Error** | **z value** | **p value** |
|---------------------------|---------------|----------------|-------------|-------------|
| age_log                  | -0.074230     | 0.039161       | -1.895      | 0.05803     |
| avg glucose level_log    | 0.001876      | 0.007516       | 0.250       | 0.80286     |
| bmi_log                  | -0.036375     | 0.094335       | -0.386      | 0.69980     |

Using the Box-Tidwell test, we can observe that the log-transformed interaction terms are not significant for
age, average glucose level, and BMI, suggesting the linearity assumption holds.

#### Assumption 3: Independence checking

Positive autocorrelation detected since the Durbin-Watson statistic is 0.18026, which is close to 0. Also it
has a p value smaller than 2.2e-16. Thus the Durbin-Watson test violates the assumption that variables
are independent.

#### Assumption 4: Outliers and influential points checking



Since no observations with Cook’s Distance > 0.5 are found, no observations have a significant impact
on the model results. Thus, the outlier check is satisfied.

## Tools
<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/r/r-original.svg" title="R" alt="R" width="40" height="40"/>&nbsp;
 
</div>

