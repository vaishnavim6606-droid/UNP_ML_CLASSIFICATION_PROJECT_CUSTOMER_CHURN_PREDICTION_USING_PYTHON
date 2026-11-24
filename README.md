# UNP_ML_CLASSIFICATION_PROJECT_CUSTOMER_CHURN_PREDICTION_USING_PYTHON
This project was completed as part of the United Network of Professionals (UNP) Machine Learning Academic Internship Program.

UNP ML Classification Project: Customer Churn Prediction using Python

Predicts which telecom customers are likely to churn (stop using the service) using 9 machine learning classifiers and an Artificial Neural Network (ANN). Models are compared across five train–test splits, then tuned with GridSearchCV. The goal is to identify at-risk customers early so the business can act before they leave.

Dataset
Source: Customer Churn.xlsx, 3,150 rows × 14 columns, no missing values
After pre-processing: 2,850 rows × 13 columns (12 input features + Churn target)
Class balance: 2,404 non-churners (84.4%) vs 446 churners (15.6%), an imbalanced target, so SMOTE is applied to the training data
Features: Call Failure, Complains, Subscription Length, Charge Amount, Seconds of Use, Frequency of Use, Frequency of SMS, Distinct Called Numbers, Tariff Plan, Status, Age, Customer Value
Workflow
Pre-processing: removed 300 duplicate rows, dropped the redundant Age Group column, checked for constant columns, and recoded Tariff Plan and Status from 1/2 to binary 1/0
EDA: box plots, bar charts, histograms, line plots and pie charts, plus a correlation heatmap
ML models: Logistic Regression, KNN, Decision Tree, Random Forest, AdaBoost, Gradient Boosting, XGBoost, SVC, Naive Bayes
Pipeline (per split): stratified split → StandardScaler → SMOTE on training data → fit → evaluate (accuracy, precision, recall, F1, ROC-AUC, confusion matrix)
Splits: 60:40, 65:35, 70:30, 75:25, 80:20
ANN: Adam vs SGD compared first; the final model is 64→32→16→1 (ReLU, sigmoid output) with Adam (lr 0.0005), 150 epochs, batch size 16
Hyperparameter tuning: GridSearchCV (5-fold CV, scored on accuracy) for all 9 models across the 5 splits
Key Insights from EDA
Complains has the strongest positive correlation with churn (0.55): customers who complain are far more likely to leave.
Status (-0.49), Frequency of Use (-0.30), Seconds of Use (-0.30) and Customer Value (-0.29) correlate negatively: more active, higher-value customers churn less.
Call Failure, Age and Subscription Length show almost no linear relationship with churn.
Results

Best classical ML model (SMOTE pipeline, default settings)

Model	Split	Accuracy	F1 Score	ROC-AUC
Random Forest	65:35	96.29%	0.8825	0.9752

Best model after GridSearchCV

Model	Split	Best Parameters	Accuracy	F1 Score	ROC-AUC
Gradient Boosting	75:25	learning_rate 0.2, n_estimators 300	96.21%	0.8708	0.9757

Best overall: ANN (80:20 split)

Model	Accuracy	Precision	Recall	F1 Score	ROC-AUC
ANN (Adam, 64→32→16→1)	97.02%	0.8750	0.9438	0.9081	0.9916
Tree ensembles (Random Forest, XGBoost, Gradient Boosting) performed best among the classical models across splits.
Naive Bayes had very high recall but low precision and accuracy (about 70%), so it flags too many false churners.
Adam outperformed SGD in the optimizer comparison (accuracy 96.7% vs 94.9%).
Applications

Customer retention campaigns, high-risk customer identification, personalized offers, and proactive customer support.

Tech Stack

Python, Pandas, NumPy, Scikit-learn, imbalanced-learn (SMOTE), XGBoost, TensorFlow/Keras, Matplotlib, Seaborn

Acknowledgements

Thanks to UNP Education (United Network of Professionals) for the internship opportunity, the dataset and the guidance for this project.

Code Link : https://drive.google.com/file/d/1WRZMXKKdsfauBTUUSuE4ACi3wJohwLrn/view?usp=drive_link 

PPT Link : https://docs.google.com/presentation/d/1m6PQKkeaGrYLDzd_nHV74WCDuczpGmph/edit?usp=drive_link&ouid=113382930934840677528&rtpof=true&sd=true
