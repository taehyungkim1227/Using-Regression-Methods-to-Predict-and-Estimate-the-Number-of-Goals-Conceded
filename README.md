# Using Regression Methods to Predict and Estimate the Number of Goals Scored

## Part 1. Project Background

#### As a huge fan of professional football in Europe, I was always interested in predicting ,estimating, and exploring the relationship between the number of goals per team using other team statistics such as shots made on target, dribbles made, and fouls made. I was curious in discovering if and if different regression methods would tell unique stories and results. I explored this using soccer data from https://www.whoscored.com and applying regression methods to this data. One can find the R code used for this project in the "Regression Project.Rmd" file in this repository. The project was done in R. 

## Part 2. Data Preprocessing and EDA

#### In this step of the project, I attempted the following:
#### -Remove numbers preceding some of the team names
#### -Check Data Shape (data consists of 187 teams (each represented by a row) and 6 columns (Team Name, Shots per game, Shots on target per game, dribbles per game, fouled per game, and total goals conceded) 
#### -Summary of the data (Min, Median, Mean, Quartile Values, Max)
#### -Divide the Goals Conceded column by 19 (average number of games played per team during data collection (2022-2023 Season))
#### -Clean variable (column) names in a readable manner
#### -Correlation Pairplot: The main dependent variable (Goals Conceded per Game) seems to be the most correlated (negatively) with Shots per game and Shots on Target per game. Among the independent variables, shots per game and shots on target per game seem to be the highest positively correlated values. 
#### -Histogram: Shots per game and Shots on target per game seem to be right skewed, while Goals Conceded per Game seems to be left skewed. Dribbles per game and Fouled per Game seem to be near a normal distribution centered around the mean.
#### Correlation Matrix to Check for Multicollinearity among the variables + Correlation Heat Map: As shown earlier, the absolute value of the correlation coefficient between dependent variables Shots per Game and Shots on Target per Game seem to be the highest.
#### Check for Normality of Residuals to decide whether to use logarithm on the dependent variable or not
#### Split Data into Train and Test Datasets: Here, the 80:20 split is used to split Train and Test data. As stated above, the dependent variable is Goals Conceded while independent variables are Shots per game, Shots on target per game, Dribbles per game, and Fouled per game.

## Part 3. Modeling

### Part 3-1. Multiple Linear Regression

#### The summary of the multiple linear regression model applied to this dataset shows the most relevant variables based on p-value as shots per game and fouled per game (low associated p-values). The visualization of the regression coefficients show the variable shots per game with the largest absolute value of the coefficient, indicating it has the largest impact among all other variables in this model. The Root Mean Squared Error for this linear regression model is 1.1563, while the R-squared value is 0.5920. 

### Part 3-2. Ridge Regression

#### The ridge regression model will enable us to reduce any multicollinearity issues and prevent overfitting of the model, compared to our ordinary least squares linear regression model in Part 3-1. The penalty value of lambda will enable this model to reduce overfitting of the model into the data we have. Here, the best lambda value is 0.0233, found by cross validation technique. The RMSE value for Ridge Regression is 0.3050, and the R-squared value is 0.5785.

### Part 3-3. Lasso Regression

#### The lasso regression model will also enable us to prevent overfitting of the model, but will achieve this in a slightly different way than ridge regression as lasso regression, unlike ridge regression, in some cases makes some of the coefficients to be exactly zero, instead of near zero. The optimal lambda value in this model is found to be 0.005 (found through cross validation). The RMSE value for Lasso Regression is 0.3056, and the R-squared value is 0.5807.

### Part 3-4. (Extra) Polynomial Regression

#### Polynomial Regression was also attempted. Polynomial relationships between the variables were visualized in an attempt to apply this model. Shots per game seemed to be the best fit for the polynomial regression model. Unfortunately, unlike my initial expectation, the model seems to produce a result that shows only up to the first degree (not the second, third degrees) to be most relevant based on the p-value (which implies variable importance). So, in this case, Linear Regression and variants of Linear Regression methods seem to be the best fit, rather than polynomial regression. 

## Part 4. Conclusion and References

####

#### References used for this project include the following pages:

https://cran.r-project.org/web/packages/jtools/vignettes/summ.html

https://stackoverflow.com/questions/74858614/lmer-and-plot-coefs-add-values-for-estimates

https://www.youtube.com/watch?v=BnRIneLsNJY&ab_channel=DragonflyStatistics

https://www.statology.org/confidence-interval-for-regression-coefficien
