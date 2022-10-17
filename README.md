# Module 12 Report Template

# Overview of the Analysis

This report shows the results of two logistic regression models based on the same dataset of various loan variables to determine whether the likelihood of a loan being being successful (or not).

The first model was run on the dataset without any balancing of data.  The data is inherently imbalanced because the number of "good" loans will naturally outnumber the number of "risky" loans".  The second model utilizes the same dataset but rebalances the dataset using the RandomOverSampler module from the imbalanced learn library.

The models generate predictive values to determine creditworthiness based on the following factors:  loan_size, interest rate, borrower's income, borrower's debt to income, number of accounts, derogatory marks, and borrower's total debt.  The datasize contains 77,357 rows of data, which contain the foregoing variables (or features).  This data is contained in the file "lending_data.csv" in Resources folder, which is in the repository.

# Methodology

* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

After importing the csv file, the data was separated into the y variable and an aggregation of the remaining dataset (containing the features that comprise model) to generate an X variable.  The data is further split into training and testing dataset using the train_test_split function.

After declaring use of the logistic regression model via the scikitlearn library, the training and testing data is fit to the model, and predicted values are generated.  At this point, an accuracy score and overall classification report can be generated.

With respect to Model 2, the same data needs is resampled such using the RandomOverSampler module from the imbalanced learn library.  By oversampling, the datasize of "bad" loans is increased to the same amount of data as "good" loan (i.e., same number of rows).  At this point, the data is balanced, and the above results can be generated utilizing the same procedure:  split the data into training and testing data, call (or invoke) the model, fit the model, and predict values.  Finally, the accuracy score and classification report are generated.

## Results

* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.

Overall, the Model 1 is 99% accurate.

As to healthy loans, denoted by the target_name "0", precision is 100%, which means the model did not generate any false positives (precision=TP/(TP+FP).  The model's recall score is 99%, which means the model yielded nearly perfect results when it predicted true negatives in relation to false positives.  In other words, very few loans that should have been denied were approved (at a rate of less than 1%).

As to high risk loans, denoted by the target_name "1", precision is 85%, which means the model predicted a higher rate of false positives for these loans.  15% of the loans that were refused should have been approved.  The model's recall score is 91%, which means the model yielded more false positives in relation to true negatives.  About 9% of loans that should have been denied were approved.

The lower precision and recall scores for the higher risk loans are likely attributable to the data imbalance.  There were 18,765 healthy loans vs. only 619 high-risk loans in the dataset used.

* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.

After resampling the data, Model 2 revealed better results.  The accuracy score is still 99% but even slightly more accurate than when utilizing the imbalanced dataset (99.47% vs. 99.18%).

Both precision and recall for 0 and 1 loans improved to 99%, which means the model predicted fewer false positives in relation to true positives and fewer false positives in relation to true negatives.

## Summary

The logistic regression model, fit with oversampled data, is superior to the same model without use of the oversampled data.  The preferred model is the regression model utilizing the rebalanced data.  The unsampled model has an accuracy of 99.18%.  The resampled model yields an accuracy rate of 99.47%.
# homework_12
