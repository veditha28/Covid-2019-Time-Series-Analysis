# COVID-19 Time Series Forecasting using ARIMA and Prophet

This repository contains a comprehensive time series analysis of COVID-19 confirmed daily cases in India. The project involves data preprocessing, visualization, and forecasting using two methods: ARIMA (AutoRegressive Integrated Moving Average) and Facebook Prophet. The goal is to understand the structure of the data and develop models to predict future trends.

## 📂 Dataset
- **Source:** Johns Hopkins University CSSE COVID-19 Dataset  
- **File:** `time_series_covid19_confirmed_global.csv`
- **Duration:** January 22, 2020 – March 9, 2023
- **Structure:** Cumulative daily confirmed cases for each country/region

## 🔧 Preprocessing
- Filtered data for India
- Removed irrelevant metadata columns (Province/State, Lat, Long, etc.)
- Aggregated cumulative cases into a single national-level time series
- Converted column headers into datetime format
- Differenced cumulative data to compute daily new cases
- Structured data into Prophet-compatible format with columns `ds` (date) and `y` (daily cases)

## 📊 Exploratory Data Analysis
- Line plot of daily new cases
- 7-day rolling average for trend smoothing
- Weekly seasonality analysis using box plots
- Seasonal decomposition of the series (trend, seasonality, residual)
- Spike detection using 95th percentile threshold

## 🔮 Forecasting Approaches

### Prophet
- Applied to daily new case data
- Forecasted 30 days into the future
- Included trend, weekly, and yearly seasonality components
- Lockdown dates added as holidays to improve accuracy
- **Performance:**  
  - MAE: 37,770.96  
  - RMSE: 50,429.40

### ARIMA
- Data differenced to meet stationarity requirement
- Manually selected ARIMA(2,1,2) parameters
- Produced forecasts for the same test period
- **Performance:**  
  - MAE: 13,550.68  
  - RMSE: 15,693.16

## 📈 Results & Conclusion
- Prophet overestimated cases post-2022 due to flattening trend and lack of seasonality
- ARIMA adapted better to the stationary and noise-driven characteristics of recent data
- Lockdown events helped Prophet partially, but context-aware modeling remains essential

## 📎 Files
- `Covid Time Series.ipynb`: Jupyter notebook with all preprocessing, visualization, and modeling
- `time_series_covid19_confirmed_global.csv`: Raw dataset from JHU CSSE
- `README.md`: Project overview
- `covid_arima_prophet_doc.md`: Full technical documentation

## 🧠 Requirements
- Python 3.7+
- Libraries: `pandas`, `matplotlib`, `seaborn`, `statsmodels`, `prophet`, `pmdarima`, `scikit-learn`

## 📜 References
- [Johns Hopkins CSSE GitHub](https://github.com/CSSEGISandData/COVID-19)
- [Facebook Prophet Documentation](https://facebook.github.io/prophet/)
- [Statsmodels ARIMA Documentation](https://www.statsmodels.org/stable/tsa.html)
