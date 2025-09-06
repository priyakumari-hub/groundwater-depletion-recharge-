**AI-Powered Groundwater Depletion and Recharge Prediction** 
**Overview**
This project predicts groundwater rise and depletion trends using historical groundwater and rainfall data. It uses AI to forecast groundwater rise based on rainfall and previous groundwater changes and provides a simple classification of recharge levels.

**Feature**

•	Groundwater Trend Prediction – Predicts groundwater rise based on rainfall and prior groundwater data.
•	Recharge Classification – Classifies predicted groundwater rise as "Good Recharge (>=2m)" or "Low Recharge (<2m)".
•	Data Cleaning & Feature Engineering – Handles missing values, encodes categorical data, and creates derived features.
•	Visualization – Shows feature importance via bar plots.
•	Model Persistence – Saves trained Random Forest model and scaler for future use.

**Datasets**
•	Sheet1 (Groundwater Data): District-level rise, fall, and net groundwater change.
•	Sheet2 (Monthly Rainfall Data): Actual, normal rainfall, and departure for districts.
•	Sheet3 (Yearly Rainfall Data): Yearly actual, normal rainfall, departure, and category.

**Problem Statement**
Groundwater over-extraction and variable rainfall can lead to depletion, threatening water supply for agriculture and human consumption. This project predicts groundwater rise and depletion trends to support better water management decisions.

**Solution Approach**

1.	Data Reading and Cleaning 
       •	Remove duplicates.
       •	Correct district name errors.
       •	Convert text categories to numeric values.
       •	Map years and periods to numeric.
       •	Encode categorical features (months, districts)
2. Feature Engineering
       •	Calculate Net_GW_Change = Total_Rise - Total_Fall.
       •	Compute rainfall anomaly and ratio for monthly and yearly data.
       •	Compute rolling averages and previous year rainfall for trend analysis.
3. Data Merging
       •	Merge groundwater and monthly rainfall data by district and year.
       •	Append yearly rainfall data to the processed dataset.
4. Model Building
       •	Features used: Total_Rise, Total_Fall, Net_GW_Change, Actual Rainfall (mm), Normal Rainfall (mm), Departure (mm).
       •	Split dataset into training and testing sets.
       •	Scale features using StandardScaler.
       •	Train a RandomForestRegressor to predict groundwater rise.
       •	Evaluate performance using Mean Squared Error (MSE) and R².
5. Prediction & Classification
       •	Predict groundwater rise for new inputs.
       •	Classify predictions as >=2m (Good Recharge) or <2m (Low Recharge).
6. Visualization
       •	Plot feature importance to understand which factors contribute most to groundwater rise.
7. Model Saving
       •	Save the trained Random Forest model and scaler using joblib.

**Tools & Technologies**
•	Programming Language: Python
•	Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn, joblib, openpyxl
•	Machine Learning Model: Random Forest Regressor
•	Data Storage: Excel (.xlsx)

**How to Run**

•	Clone the repository:git clone <repository_link>
•	Install dependencies: pip install -r requirements.txt
•	Run the main script: python process.py
•	Use the predict() function to forecast groundwater rise for new input data.

**Conclusion**
This project provides AI-based predictions for groundwater rise and depletion, helping users understand trends and take proactive measures for sustainable water management.
