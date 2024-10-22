# Store Sales Time Series Prediction

## Overview

This project focuses on building a machine learning model to forecast daily unit sales for Corporación Favorita, a major grocery retailer in Ecuador. Accurate sales forecasting helps optimize inventory management, reducing overstocking, understocking, and minimizing food waste, which ultimately enhances customer satisfaction.

### **Key Insights and Accomplishments**:

- **Seasonal and Holiday Effects**: Sales exhibit strong seasonality, with peaks during holiday periods, particularly in December.
- **Weekend Sales Patterns**: Sales tend to be higher on weekends, especially Saturdays, while Thursdays experience a noticeable dip.
- **Promotions Impact**: Promotional periods have a strong positive correlation with sales, driving significant spikes in purchasing behavior.
- **Modeling Success**: The best-performing model, a **Boosted Hybrid Model** (combining Linear Regression and Random Forest), achieved an RMSLE of **0.6841**, effectively capturing the interactions between promotions, holidays, and other sales drivers.

By leveraging historical sales data along with metadata such as promotions, oil prices, and holiday information, the project successfully identified the factors influencing sales patterns and developed a robust predictive model.

## Problem Statement

The objective is to develop a model that accurately predicts daily sales for different products across various stores. The system uses historical sales data along with metadata such as promotions, oil prices, and holiday information to improve forecast accuracy.

Dataset source: [Corporación Favorita Grocery Sales Forecasting](https://www.kaggle.com/c/favorita-grocery-sales-forecasting)

---

## Data Wrangling

The data preparation involved the following steps:

- **Merging Datasets**: Data from multiple sources, including sales, holiday events, and oil prices, were combined using common keys like store IDs and dates.
- **Handling Missing Values**: Missing sales data were imputed using mean values for corresponding product categories or specific days. Missing values in other datasets were either imputed or removed, depending on their impact.
- **Feature Engineering**: Date-related features, such as day of the week, month, and quarter, were created to capture temporal patterns essential for time series modeling.

- **Data Standardization**: The data was standardized to ensure uniformity across features, which is critical for models like PCA and LSTM.

---

## Exploratory Data Analysis (EDA)

Key insights from the data analysis:

- **Seasonality and Holidays**: Sales peaked during holiday periods, especially in December, confirming the influence of seasonal factors.
  ![Seasonal decomposition of daily sales](<image/Screenshot 2024-10-21 at 7.58.01 PM.png>)
- **Weekend Sales**: Sales were consistently higher on weekends, particularly Saturdays, while Thursdays had the lowest sales.
  ![Sales distribution by day of the week](<image/Screenshot 2024-10-21 at 7.56.39 PM.png>)
  ![Tukey HDS test result](<image/Screenshot 2024-10-21 at 7.56.49 PM.png>)
- **Promotions**: Strong positive correlation with promotions, showing that promotional periods drive significant increases in sales.
  ![sales correlation with promotion](<image/Screenshot 2024-10-21 at 7.59.17 PM.png>)

These insights guided the creation of features related to holidays, days of the week, and promotions, which were incorporated into the model.

---

## Model Development: Time Series Forecasting

The following models were explored:

- **Linear Regression**: Used as a baseline, achieving an RMSLE of 0.7743.
- **ARIMA**: Captured time series characteristics but did not outperform the baseline.
- **LSTM (Long Short-Term Memory)**: Showed potential for capturing long-term dependencies but required further refinement.
- **Boosted Hybrid Model**: Combining Linear Regression and Random Forest, this model achieved the best performance with an RMSLE of 0.6841.

### Model Performance

Through **cross-validation** and **hyperparameter tuning**, the **Boosted Hybrid model** outperformed others by effectively capturing the interactions between features such as promotions, holidays, and sales.

---

## Future Work

Improvements could include:

- **Incorporating Additional Data Sources**: Weather data and competitor pricing could provide further insights and improve prediction accuracy.
- **LSTM Model Refinement**: Hyperparameter tuning and experimenting with advanced architectures like bidirectional LSTMs could enhance performance.
- **Time Series Cross-Validation**: Implementing time series cross-validation would improve the generalizability of the model when predicting future sales.

---

## Tools and Libraries

- **Languages**: Python
- **Libraries**: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
- **Machine Learning Models**: Linear Regression, ARIMA, LSTM, Random Forest, Boosted Hybrid Model
