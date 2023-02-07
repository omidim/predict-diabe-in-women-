# Performance-analysis-of-machine-learning-techniques-to-predict-diabe-in-women-
According to the Centers for Disease Control and Prevention (CDC), diabetes is a lifelong condition that causes a person's blood sugar level to become too high [1]. Diabetes increases the risk of heart disease by about four times in women (in comparison to men, it is about two times more), and women have worse outcomes after a heart attack. Women are also at higher risk of other diabetes-related complications such as blindness, kidney disease, and depression. Moreover, diabetes is different among women. For instance, white women are less likely to have diabetes than African Americans or Hispanic/Latina women [2]. Therefore, providing a simple algorithm to predict diabetes in women could be significantly helpful.  
## Preparing and Cleaning the Data
In this study, the Pima Indians Diabetes data set [3] was used to fit machine learning models and select an optimal model to predict diabetes in women. The dataset used for analysis and has 768 records with nine variables. The number of diabetic women in the data set is around 54%, and the remaining women are nondiabetic. This data set contains information about the number of times pregnant (Pregnancies), plasma glucose concentration (Glucose), diastolic blood pressure (BloodPressure), triceps skinfold thickness (SkinThickness), 2-hour serum insulin (Insulin), body mass index (BMI), age (Age), and diabetes pedigree function (DiabetesPedigreeFunction). Single decision trees and QDA models were fitted over these variables to select the optimal model to predict diabetes.  

In order to prepare the data set for the analysis, initially, the distribution of missing values in the data set is investigated. In this data set, the missing values were not clear. As it is clear,  Glucose, BloodPressure, SkinThickness, Insulin, and BMI can not be zero in humans. Therefore, these variables with zero values could be considered as the missing values in the data set. After replacing the zero with NA in the data set distribution of missing values for each variable was plotted (Fig. 1).
 
Fig. 1 distribution of missing values in the data set
The presence of too much missing data in the data set can negatively affect the precision and accuracy of the model. Generally, less than five percent missing values are an acceptable threshold. Fig. 1 shows about 49% and 30% of data in Insulin and SkinThickness are missing in the data set. The missing value in BloodPressure, BMI, and Glucose is less than five percent. 
 Due to the high missing value, the impute approach could not be efficient for Insulin and SkinThickness. Therefore we have to delete rows with missing values in the data set. 
The distribution of numeric variables is another important parameter that should be considered. The highly skewed distribution can have a negative influence on the model results.
Before logarithm transformations	After logarithm transformations
 	 
 	 
Fig. 2 distribution of Pregnancies, and Age variables before and after logarithm transformations 

 Among all numeric variables, Pregnancies, BMI, DiabetesPedigreeFunction, and Age variables are highly skewed. Logarithm transformations were used to modify the data (Fig. 2).  In the QDA model, multivariate normality is an essential assumption. Despite the transformations, the normality assumption for the Pregnancies and Age variables is not reasonable or close to reasonable. As a result, the optimal solution for the QDA could not be found using the Pregnancies and Age variables in the model.  
 
Fig. 3 The single-layer cross-validation accuracy for different models
## Fitting the models
First, a single layer of 10-fold cross-validation was conducted on a single decision tree and QDA. In the single decision tree model, the complexity parameter (cp) was selected to be optimized. The cp is used to control the decision tree's size and choose the optimal tree size. Lower cp values result in a more complex tree. To tune the QDA, three models with different combinations of variables were defined. The outer layer of 5-fold cross-validation was conducted on all models, which was defined previously. The results indicate that single decision trees with cp = 0.03 were the most accurate model among all models (Fig. 3). 
The final single decision trees model is presented in Fig. 4. The model could predict diabetes in women with 73.95% accuracy. In this model, plasma glucose concentration, 2-hour serum insulin, and age are the essential variables in the predicted diabetes in women, respectively. 
 
 
Fig. 4 The single-layer cross-validation accuracy for different models

## Interpreting the best model
The model predicted that women with low plasma glucose concentration (Glucose < 128) and low 2-hour serum insulin (insulin < 144) do not have diabetes. For the high 2-hour serum insulin (insulin > 144), age becomes an important parameter. If the woman is older than 32 years, she could have diabetes.   The model also predicted that women with high plasma glucose concentration (Glucose < 166) have diabetes. For the plasma glucose concentration in the range of 128 to 166 age again becomes an important parameter. For this glucose range, if the woman is older than 25 years, she could have diabetes. 
As mentioned above, plasma glucose concentration and 2-hour serum insulin are the most important predictors in the model. This result is not very surprising. The strong relation of these predictors with diabetes has been shown in the literature [4]. Balkau et al. provide a model based on logistic regression to predict later diabetes using variables available in the clinic setting and biological variables and polymorphisms [5]. The developed model indicates that plasma glucose concentration, insulin, BMI, triglycerides, and diabetes in the family for women are the most important predictors for predicting diabetes. On the other hand, the relation between plasma glucose concentration and diabetes is well known in public. For instance, the measurement of glucose concentration is one of the routine procedures in medical check-ups. 
The high missing data for the 2-hour serum insulin is an essential concern about this model. Here insulin is the second important predictor in the model. During model selection, we have to delete about 50% of data due to missing insulin data. Therefore concern about the accuracy of the model could be reasonable. 

## References
[1]	“Diabetes and Women | CDC.” https://www.cdc.gov/diabetes/library/features/diabetes-and-women.html (accessed Nov. 07, 2021).
[2]	A. Lapolla, M. G. Dalfrà, and D. Fedele, “Diabetes related autoimmunity in gestational diabetes mellitus: Is it important?,” Nutr. Metab. Cardiovasc. Dis., vol. 19, no. 9, pp. 674–682, Nov. 2009, doi: 10.1016/J.NUMECD.2009.04.004.
[3]	J. W. Smith, J. E. Everhart, W. C. Dickson, W. C. Knowler, and R. S. Johannes, “Using the ADAP Learning Algorithm to Forecast the Onset of Diabetes Mellitus,” Proc. Annu. Symp. Comput. Appl. Med. Care, p. 261, 1988, Accessed: Nov. 07, 2021. [Online]. Available: /pmc/articles/PMC2245318/?report=abstract.
[4]	G. K. Dowse et al., “Serum insulin distributions and reproducibility of the relationship between 2-hour insulin and plasma glucose levels in Asian Indian, Creole, and Chinese Mauritians. Mauritius NCD Study Group,” Metabolism., vol. 42, no. 10, pp. 1232–1241, 1993, doi: 10.1016/0026-0495(93)90119-9.
[5]	B. Balkau et al., “Predicting Diabetes: Clinical, Biological, and Genetic Approaches,” Diabetes Care, vol. 31, no. 10, pp. 2056–2061, Oct. 2008, doi: 10.2337/DC08-0368.
