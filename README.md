# UoL_Coursework
## Part 1

In the first part you will be given data collected from various individuals on several variables. The goal will be to use unsupervised learning techniques such as Principal Component Analysis or Cluster Analysis to summarise the information in the data by appropriate tables and/or plots.

Description for the EWCS dataset
Task:

Visualise and describe the data via unsupervised learning methods.

Source:

European Working Conditions Survey 2016.

Variable and value labels for EWCS 2016 dataset:

Q2a - Gender

Values 1: Male 2: Female

Q2b - Age

Values numeric

Q87a - I have felt cheerful and in good spirits [...which is the closest to how you have been feeling over the last two weeks]

Q87b - I have felt calm and relaxed [...which is the closest to how you have been feeling over the last two weeks]

Q87c - I have felt active and vigorous [...which is the closest to how you have been feeling over the last two weeks]

Q87d - I woke up feeling fresh and rested [...which is the closest to how you have been feeling over the last two weeks]

Q87e - My daily life has been filled with things that interest me [...which is the closest to how you have been feeling over the last two weeks]

Values for variables Q87a to Q87e

1. All of the time.
2. Most of the time
3. More than half of the time
4. Less than half of the time
5. Some of the time
6. At no time

Q90a - At my work I feel full of energy [Please tell me how often you feel this way...]

Q90b - I am enthusiastic about my job [Please tell me how often you feel this way...]

Q90c - Time flies when I am working [Please tell me how often you feel this way...]

Q90f - In my opinion, I am good at my job [Please tell me how often you feel this way...]

Values for variables Q90a to Q90f

1. Always.
2. Most of the time
3. Sometimes
4. Rarely
5. Never

# Workflow description 

In the first part of the coursework, we are given a dataset which contains a survey on European working conditions in 2016. The data set contains numeric data about different individuals, the goal is to use various unsupervised learning techniques to summarize the given data in appropriate categories. First, we import the packages, load the dataset, and start with an exploratory data analysis to gain insight about our data. We check if there are any missing values or non-numeric values and after that we use the pandas describe() method to display all the descriptive statistics.
Here we can see that the min value for each column is -999. After checking if it’s a unique value and considering our goal, this variable isn’t in line with our task, and we would consider dropping it from every column in our dataset. The next step is constructing the correlation matrix for our dataset. Correlation matrix is a type of a graph that shows us the correlation coefficients between variables in our data set. The value of correlation should be between -1 and 1. In simple terms the correlation matrix shows us how the columns in our dataset affect each other. To improve the readability and meaningfulness of the graph we use different color styles. Here we can see that if there is a strong positive correlation the value is closer to 1 and the color is a profound blue color, the variables that have a correlation coefficient closer to 0 are uncorrelated and are in light grey. In strong negative correlations, which means that if the correlation is closer to -1, we would expect to get a deep red color. From the graph we can see that columns Q87a, Q87b, Q87c, Q87d have a medium positive correlation. This could be explained because these parameters are similar in structure. 
My next step was looking at the distribution of the data in the columns. The Q2a column which shows the gender has normal distribution for each gender and the number of males and females is close to equal. The distribution in column Q2b shows us that the average age is 40 years old. And all other columns show us the distribution of answers to questions, from this we can conclude that “2” is the most popular answer. 
From this point I will focus on finding the optimal number of clusters to use in the KMeans clustering model. First, I will scale the data using the RobustScaler to deal with any possible outliers. To get the optimal value of clusters, I will use the elbow method. The method runs, kmeans several times and with each run the number of clusters which is k is incremented then SSE curve is plotted.  Visually we determine that 2 is the elbow. Thus 2 is the optimal number of clusters. 
My model of choice is KMeans clustering as it is easy to implement, and it gives good performance. After we performed the clustering, we can see that all the data is distributed in 2 clusters and the model performed well, we can see there are 2 distinct clusters and there is little mix up between the points. 


## Part 2

In the second part you will be presented with a regression problem. The aim would be to compare various models and techniques for their estimation to allow meaningful interpretation and competitive predictive performance. The latter should be assessed by appropriate experiments based on training and test datasets. In addition to linear regression, Tree based methods, Non-linear models or other suitable techniques can be used if you think they can provide improvement.

## Description for Student Performance Dataset
Task:

Build a regression model for the variable G3 (final grade) without using the variables G1 and G2. Interpret the model and assess its predictive performance.

## Source:

Paulo Cortez, University of Minho, Guimaraes, Portugal, http://www3.dsi.uminho.pt/pcortez

## Data Set Information:

This data approach student achievement in secondary education of two Portuguese schools. The data attributes include student grades, demographic, social and school related features) and it was collected by using school reports and questionnaires. 

Two datasets are provided regarding the performance in two distinct subjects: Mathematics (mat) and Portuguese language (por). In [Cortez and Silva, 2008], the two datasets were modeled under binary/five-level classification and regression tasks. 

Important note: the target attribute G3 has a strong correlation with attributes G2 and G1. This occurs because G3 is the final year grade (issued at the 3rd period), while G1 and G2 correspond to the 1st and 2nd period grades. It is more difficult to predict G3 without G2 and G1, but such prediction is much more useful (see paper source for more details).

## Attribute Information:

## Attributes for both student-mat.csv (Math course) and student-por.csv (Portuguese language course) datasets:
1. school - student's school (binary: 'GP' - Gabriel Pereira or 'MS' - Mousinho da Silveira)

2. sex - student's sex (binary: 'F' - female or 'M' - male)

3. age - student's age (numeric: from 15 to 22)

4. address - student's home address type (binary: 'U' - urban or 'R' - rural)

5. famsize - family size (binary: 'LE3' - less or equal to 3 or 'GT3' - greater than 3)

6. Pstatus - parent's cohabitation status (binary: 'T' - living together or 'A' - apart)

7. Medu - mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 -“ secondary education or 4 - higher education)

8. Fedu - father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 - secondary education or 4 - higher education)

9. Mjob - mother's job (nominal: 'teacher', 'health' care related, civil 'services' (e.g. administrative or police), 'at_home' or 'other')

10. Fjob - father's job (nominal: 'teacher', 'health' care related, civil 'services' (e.g. administrative or police), 'at_home' or 'other')

11. reason - reason to choose this school (nominal: close to 'home', school 'reputation', 'course' preference or 'other')

12. guardian - student's guardian (nominal: 'mother', 'father' or 'other')

13. traveltime - home to school travel time (numeric: 1 - <15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, or 4 - >1 hour)

14. studytime - weekly study time (numeric: 1 - <2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, or 4 - >10 hours)

15. failures - number of past class failures (numeric: n if 1<=n<3, else 4)

16. schoolsup - extra educational support (binary: yes or no)

17. famsup - family educational support (binary: yes or no)

18. paid - extra paid classes within the course subject (Math or Portuguese) (binary: yes or no)

19. activities - extra-curricular activities (binary: yes or no)

20. nursery - attended nursery school (binary: yes or no)

21. higher - wants to take higher education (binary: yes or no)

22. internet - Internet access at home (binary: yes or no)

23. romantic - with a romantic relationship (binary: yes or no)

24. famrel - quality of family relationships (numeric: from 1 - very bad to 5 - excellent)

25. freetime - free time after school (numeric: from 1 - very low to 5 - very high)

26. goout - going out with friends (numeric: from 1 - very low to 5 - very high)

27. Dalc - workday alcohol consumption (numeric: from 1 - very low to 5 - very high)

28. Walc - weekend alcohol consumption (numeric: from 1 - very low to 5 - very high)

29. health - current health status (numeric: from 1 - very bad to 5 - very good)

30. absences - number of school absences (numeric: from 0 to 93)

## these grades are related with the course subject, Math or Portuguese:

31. G1 - first period grade (numeric: from 0 to 20)

31. G2 - second period grade (numeric: from 0 to 20)

32. G3 - final grade (numeric: from 0 to 20, output target)

## Relevant Papers:

P. Cortez and A. Silva. Using Data Mining to Predict Secondary School Student Performance. In A. Brito and J. Teixeira Eds., Proceedings of 5th Future Business Technology Conference (FUBUTEC 2008) pp. 5-12, Porto, Portugal, April, 2008, EUROSIS, ISBN 978-9077381-39-7.

# Workflow description 

in the second part we are given two datasets with academic achievements of students from two distinct schools on two subjects. The goal is to use different techniques of machine learning and compare their performance in prediction. We must predict the results without using some of the data provided in the datasets. We will start with loading our datasets and EDA to gain some insight about the data in our datasets. First, I figured out the shape of each dataset. Then I looked at the datatypes of each variable in our datasets and we can see that we have two data types “object”, which is categorical data and “int64”, which is numeric data. From here we will start our data preprocessing as there are “object” type data and regression models do not work with non-numeric values. There are a few steps to convert the data, first we will gather all the unique values in each column and create a dictionary. The key for the dictionary is a string and the value is the index of that string. In this way every value of type “object” is replaced by its index. Now we have only numeric values, and we can continue our task. Now we can construct a correlation matrix for each dataset to look if there are any strong correlations between columns. 
If we look at the correlation matrix for both datasets, we can see that a strong positive correlation is only between columns G1, G2, G3 as they have a similar structure. In this task we must predict the response variable G3 which is y_mat and y_por for the two datasets, without including columns G1, G2 in our prediction models. One more step before dividing the data to train data and test data is normalizing the length of the data frames as they are unequal. Now we perform the train test split where our train data will be equal to 80% and the test data to 20%. To ensure that the results are repeatable I will use seed number equal to 42. To avoid manually training and fitting every model we will use a different approach. We instantiate 4 models and create a dictionary to gather the instantiated models. Then we create a for loop to iterate through our dictionary with instantiated models to train and fit all models. Then we create a for loop to predict our results where we iterate through our fitted models. The models I used are Linear Regression, Ridge Regression, Decision Tree Regression. After predicting our target variables, we must evaluate the results of our prediction. We will use 3 metrics to evaluate how well we managed to predict the response variables. The metrics are MAE, MSE, RMSE. 
As a result, we got that for both datasets the best performing model is Random Forrest as it has the lowest MAE, MSE and RMSE. From this we can say that it’s better to use more complicated models and use some measures to prevent overfitting. The interpretability of this model will be lower, but the final prediction will be more accurate 

## Part 3 

Finally, in the third part you will be given a classification problem. The analysis will contain similar steps with the 2nd part but you should be able to interpret the output from different models and compare their predictive performance taking into account that the response variable will be binary. In addition to appropriate regression or discriminant analysis, Tree-based methods, Non-linear models or other suitable techniques can be used if you think they will perform better.

## Description for Bank Marketing Dataset
## Task:

Build a Classification model to predict if the client will subscribe (yes/no) a term deposit (variable y). Interpret the model and assess its predictive performance.

## Source:

[Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014

## Data Set Information:

The data is related with direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.

## Attribute Information:

## Input variables:
## bank client data: 1 - age (numeric)

2. - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')

3. - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)

4. - education (categorical:
'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')

5. - default: has credit in default? (categorical: 'no','yes','unknown')

6. - housing: has housing loan? (categorical: 'no','yes','unknown')

7. - loan: has personal loan? (categorical: 'no','yes','unknown')

## related with the last contact of the current campaign:

8. - contact: contact communication type (categorical: 'cellular','telephone')

9. - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')

10. - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')

11. - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

## other attributes:

12. - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

13. - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)

14. - previous: number of contacts performed before this campaign and for this client (numeric)

15. - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')

## social and economic context attributes

16. - emp.var.rate: employment variation rate - quarterly indicator (numeric)

17. - cons.price.idx: consumer price index - monthly indicator (numeric)

18. - cons.conf.idx: consumer confidence index - monthly indicator (numeric)

19. - euribor3m: euribor 3 month rate - daily indicator (numeric)

20. - nr.employed: number of employees - quarterly indicator (numeric)
Output variable (desired target):

21. - y - has the client subscribed a term deposit? (binary: 'yes','no')
Relevant Papers:

S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014

S. Moro, R. Laureano and P. Cortez. Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology. In P. Novais et al. (Eds.), Proceedings of the European Simulation and Modelling Conference - ESM'2011, pp. 117-121, Guimaraes, Portugal, October, 2011. EUROSIS. [bank.zip]

# Workflow description 

In the third part we also face a classification problem. The goal is to predict whether the client will term a deposit, The target variable is binary either the client gives a positive or negative answer, which means that the possible values are 0 and 1. We load the dataset and start with an exploratory data analysis to gain insight about our data. We check if there are any missing values or non-numeric values and after that I use the pandas describe() method to display all the descriptive statistics. 
We look at the datatypes of each variable in our datasets and we can see that we have two data types “object” and “int64”. From here we will start our data preprocessing as there are “object” type data and regression models do not work with non-numeric values. There are a few steps to convert the data, first we will gather all the unique values in each column and create a dictionary. The key for the dictionary is a string and the value is the index of that string. 
In this way every value of type “object” is replaced by its index. Now we have only numeric values, and we can continue our task. Now we can investigate the distribution of 0 and 1 in our target variable. We will use sns.countplot.
We can see that we have a lot more 0’s which is a “no” answer, than 1’s which is a “yes” answer in the target variable. We can say that roughly 500 clients gave a positive answer 4000 gave a negative answer. We get the following results. 
We can construct a correlation matrix to look if there are any strong correlations between columns. We see that there is no strong negative nor positive correlation between the columns. One more step before dividing the data to train data and test data is normalizing the number of 0 and 1 in our response variable as they are unequal, also we drop the duration column as we do not know the real duration. This is done to get a more consistent sample for prediction. We normalize and concatenate. Now we perform the train test split where our train date will be equal to 80% and the test data to 20%. To ensure that the results are repeatable I will use seed number equal to 42. To avoid manually training and fitting every model we will use a different approach. We instantiate 3 models and create a dictionary to gather the instantiated models. Then we create a for loop to iterate throw our dictionary with instantiated models to train and fit all models. Then we create a for loop to predict our results where we iterate through our fitted models. The models I use are Logistic Regression, Support Vector Classifier, Gradient Boosting Classifier. After predicting our target variable, we must evaluate the results of our prediction. We will use 3 metrics to evaluate how well we managed to predict the response variables. The metrics are Accuracy, Precision, ROC-AUC, Recall. We get the following results. We can see that the best peforming model is Gradient Boosting Classifier. We plot two graphs
The left one is the actual distribution and the right one is the predicted. We can see that our model tends to predict more 1’s than there are in the actual data.




