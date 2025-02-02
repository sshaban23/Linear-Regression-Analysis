# Linear-Regression-Analysis

A1: RESEARCH QUESTION:

What factors influence monthly charge for customers?

A2: GOALS:

The goal of this analysis is to find out what factors affect how much customers pay each month. I'll use a multiple linear regression model to see how different things like age, income, and the services they use affect their monthly charges. I also want to figure out which factors are the most important and how changes in these factors change the monthly charges. I will also look at different types of customers to see who pays more or less each month. By predicting monthly charges for new or current customers, we can make sure our model is accurate and useful.


B1: SUMMARY OF ASSUMPTIONS:

The four key assumptions are: linearity, independence, homoscedasticity, and normality of residuals. 

- Linearity: the relationship between the independent variables and the dependent variable is linear.

- Independence: the observations are independent of each other. 

- Homoscedasticity: the variance of the residuals is constant across all levels of the independent variables. 

- Normality of residuals: means that the residuals should be approximately normally distributed.

B2: TOOL BENEFITS:

Using Python for data analysis has many benefits that help with different stages of the analysis. It has many useful libraries like pandas, numpy, matplotlib, seaborn, and scikit-learn that make tasks simple to do, like cleaning data, visualizing it, and building models. Python also works well with Jupyter Notebooks, which help document the analysis and make it easy to repeat and share with others.

B3: APPROPRIATE TECHNIQUE:

I believe that a multiple linear regression is appropriate for this analysis because it predicts a continuous outcome using multiple predictors. This helps us identify and quantify the relationship between monthly charges and other variables. I also believe this will help us control multiple factors all at once and show us a clear interpretation for how each variable will be impacted by monthly charges. 

C1: DATA CLEANING:

My data cleaning goals for this analysis to treat missing data, remove outliers, drop columns that are not relevant to the research question, removing duplicates if there is any, converting categorical variables into a better format for regression analysis, normalize variables to make sure they are all comparable scale and to check for multicollinearity.

C2: SUMMARY STATISTICS:

Quantitative Variables

- Population: Ranges from a small town to a large city population (52,967).

- Children: The number of children in households ranges from 0 to 8.

- Age: Ranges from 18 to 89 years.

- Income: Ranges from $348.67 to $124,025.10.

- Outage_sec_perweek: Outage time per week ranges from 1.14 to 18.85 seconds.

- Contacts: Number of contacts ranges from 0 to 3.

- Yearly_equip_failure: Equipment failures per year range from 0 to 2.

- Tenure: Customer tenure ranges from 1 to 72 months.

- MonthlyCharge: Monthly charges range from $79.98 to $290.16.

- Bandwidth_GB_Year: Bandwidth usage per year ranges from 155.51 GB to 7158.98 GB.


Categorical Variables

- OnlineSecurity_Yes: 36% have online security.

- OnlineBackup_Yes: 45% have online backup.

- DeviceProtection_Yes: 44% have device protection.

- TechSupport_Yes: 37% have tech support.

- StreamingTV_Yes: 49% have streaming TV.

- StreamingMovies_Yes: 49% have streaming movies.

- PaperlessBilling_Yes: 59% use paperless billing.

- PaymentMethod_Credit Card (automatic): 21% use a credit card as a payment method.

- PaymentMethod_Electronic Check: 34% use an electronic check as a payment method.

- PaymentMethod_Mailed Check: 23% use a mailed in check as a form of payment.

C3: VISUALIZATIONS:

Univariate Visualizations:

- Histograms show the distribution of quantitative variables. 

- Bar Charts show the count of each category in categorical variables


Bivariate Visualizations:

- Scatter Plots show trends or patterns between two quantitative variables which helps to identify linear or non-linear relationships.

- Box Plots for categorical variables provide insights into the central tendency and variability of MonthlyCharge across different categories.

C4: DATA TRANSFORMATION: 

My goals for this transformation prepare that data for my initial regression analysis. The steps I took to prepare the data is to are to clean the data by imputing missing values, remove outliers, converting categorical variables, removing correlated variables and ensuring that the data is not too correlated.


D1: INITIAL MODEL: 

The OLS regression model for predicting MonthlyCharge shows a very high R-squared value of 0.996, meaning it explains almost all the variation in monthly charges. However, this high value and a very large condition number suggest that the model has multicollinearity issues, where predictors are too closely related to each other. While the model is statistically significant overall, some diagnostics indicate that the residuals (errors) are not normally distributed. Important factors influencing monthly charges include the number of children, age, tenure, yearly bandwidth, gender, and type of internet service. Therefore, the multicollinearity issue means we need to refine the model to make it more reliable.

![image](https://github.com/user-attachments/assets/3047bb52-909d-4c91-9405-8bb447283f41)

D2: JUSTIFICATION OF MODEL REDUCTION:

To reduce the initial model, I used RFE because it effectively selects the most relevant features from my dataset. In my analysis of MonthlyCharge, RFE allowed me to identify and retain the most significant predictors out of the many potential variables. RFE uses the model's coefficients to rank each feature's importance, removing the least important ones iteratively. This method ensured that only the features with the highest impact on MonthlyCharge were included. 
By using RFE, I reduced the model to 10 key predictors, which enhanced the model’s performance while maintaining a high R-squared value of 0.959.

D3: REDUCED LINEAR REGRESSION MODEL:

The reduced regression model shows that we can explain 95.9% of the changes in monthly charges using our selected features. Important factors affecting monthly charges are fiber optics internet service, Multiple lines, streaming TV.

![image](https://github.com/user-attachments/assets/0b26c318-a74f-439b-bbb7-6a3d550b0d20)

E1: MODEL COMPARISON:

I compared the initial and reduced linear regression models using Adjusted R-squared to see how well they explained the monthly charges. The initial model had a very high Adjusted R-squared of 0.996, meaning it explained almost all the variability, but it had issues with too many related predictors, which made it less reliable. After using feature selection (RFE) to simplify the model, the Adjusted R-squared was 0.959, which still explained a lot of the variability but with fewer and more relevant predictors. I believe that the reduced model is more reliable and easier to interpret.

E2: OUTPUT AND CALCULATIONS:

The reduced linear regression model is a good fit, explaining 95.9% of the variability in monthly charges with a small Residual Standard Error of 8.75, meaning the model's predictions are close to the actual values. The QQ plot shows that the residuals follow a normal distribution, and the histogram confirms this by resembling a bell curve centered around zero. These results indicate that the selected factors effectively predict monthly charges, making the model reliable and easy to understand.


F1: RESULTS:

MonthlyCharge = 83.7867 + 2.2102(Churn_Yes) + 20.1105(InternetService_Fiber Optic) − 12.6106(InternetService_None) + 32.3694(Multiple_Yes) + 2.7233(OnlineSecurity_Yes) + 22.3693(OnlineBackup_Yes) + 12.3925(DeviceProtection_Yes) + 12.6125(TechSupport_Yes) + 41.7925(StreamingTV_Yes) + 51.7655(StreamingMovies_Yes)

- Intercept: (83.7867): reference point for the model

- Churn_Yes (2.2102): Customers who churn have an average monthly charge that is $2.21 higher

- InternetService_Fiber Optic (20.1105): Customers with fiber optic service pay $20.11 more per month.

- InternetService_None (-12.6106): Customers with no internet service pay, on average, $12.61 less.

- Multiple_Yes (32.3694): Customers with multiple lines pay, on average, $32.37 more per month.

- OnlineSecurity_Yes (2.7233): Customers with online security pay $2.72 more per month.

- OnlineBackup_Yes (22.3693): Customers with online backup pay $22.37 more per month.

- DeviceProtection_Yes (12.3925): Customers with device protection pay $12.39 more per month.

- TechSupport_Yes (12.6125): Customers with tech support pay $12.61 more per month.

- StreamingTV_Yes (41.7925): Customers with streaming TV pay $41.79 more per month.

- StreamingMovies_Yes (51.7655): Customers with streaming movies pay $51.77 more per month.


The reduced model demonstrates strong statistical significance, with an R-squared value of 0.959, indicating that it explains 95.9% of the variability in MonthlyCharge. All predictors have p-values below 0.05, confirming their statistical significance. The model identifies key factors impacting monthly charges, which are multiple lines and streaming services. These insights are valuable for the company's pricing strategies and customer segmentation, which will help in revenue optimization and targeted marketing campaigns.


The limitations of this model are multicollinearity among other variables, which could inflate standard errors. Residual non-normality suggests the need for further model refinement or variable transformation. The accuracy of the model depends on the data quality and representativeness, with possible biases affecting the results. There is also the risk of omitted variable bias if relevant factors are not included in the dataset.

F2: RECOMMENDATIONS:

I believe there are a few steps the company can take to improve their services and increase profits. I would recommend focusing on services that significantly increase monthly charges, such as multiple lines, streaming TV, and streaming movies, and promoting fiber optic internet, which customers are willing to pay more for. To reduce churn, offer personalized retention strategies for high-paying customers, like special offers or loyalty programs. Customize service packages to let customers choose what they value most, which can boost satisfaction and revenue. Segment marketing efforts to target specific customer interests, like streaming services. Also, gather customer feedback to continually enhance service offerings and increase customer satisfaction.


