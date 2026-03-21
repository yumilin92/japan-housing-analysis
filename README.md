# 🏠 Japan Residential Property Market Analysis (2005–2024)

A data science project exploring 1.3 million residential property 
transactions across Japan over 20 years — from EDA and price prediction 
to undervalued property detection and regional market mapping.

---

## 📊 Project Series

| Notebook | Description |
|----------|-------------|
| [01 — EDA & Price Prediction](01_eda_and_price_prediction.ipynb) | Exploratory analysis + XGBoost price prediction model |
| [02 — Undervalued Properties](02_undervalued_properties.ipynb) | Finding properties priced below model prediction |
| [03 — Price Forecast 2025–2027](03_price_forecast.ipynb) | Time series forecasting with Prophet |
| [04 — Regional Price Map](04_regional_price_map.ipynb) | Interactive map of price trends by prefecture |
| [05 — COVID Impact Analysis](05_covid_impact_analysis.ipynb) | How the pandemic affected regional property markets |

---

## 📁 Repository Structure

```
japan-housing-analysis/
│
├── data/
│   ├── df_clean.csv                      # cleaned dataset (1.3M rows)
│   ├── undervalued_properties.csv        # 428K undervalued transactions
│   ├── price_forecast_2025_2027.csv      # regional price forecasts
│   ├── prefecture_stats.csv              # stats for all 47 prefectures
│   ├── covid_impact_summary.csv          # COVID period analysis
│   └── japan_prefectures.geojson         # prefecture boundaries
│
├── visuals/
│   ├── price_distribution.png
│   ├── price_trend.png
│   ├── price_by_prefecture.png
│   ├── price_vs_area.png
│   ├── feature_importance.png
│   ├── undervalued_by_prefecture.png
│   ├── undervalued_by_year.png
│   ├── historical_trend.png
│   ├── price_forecast.png
│   ├── regional_forecast.png
│   ├── japan_price_map.html              # interactive map
│   ├── covid_price_changes.png
│   ├── covid_regional_impact.png
│   └── covid_recovery.png
│
├── models/
│   ├── xgb_housing_model.pkl             # trained XGBoost model
│   └── features.pkl                      # feature list
│
├── 01_eda_and_price_prediction.ipynb
├── 02_undervalued_properties.ipynb
├── 03_price_forecast.ipynb
├── 04_regional_price_map.ipynb
├── 05_covid_impact_analysis.ipynb
└── README.md
```

---

## 🔍 Notebook 01 — Key Findings

### Price Trends
- Japanese property prices declined from 2005 to 2012 — a continuation 
  of the post-bubble correction that began in 1991
- Prices stabilized after 2012 under Abenomics economic stimulus policy
- COVID-19 (2020) caused a brief price spike driven by remote work demand

### Regional Insights
- **Tokyo** commands the highest median prices by a significant margin
- **Okinawa** ranks second — driven by US military presence, tourism, 
  and limited island land supply
- Properties in the Tokyo metropolitan area are 27% more influential 
  on price than any other single factor

### Model Results

| Model | R² | RMSE | Training Time |
|-------|----|------|---------------|
| Linear Regression | 0.445 | ¥16.32M | 0.2s |
| Random Forest | 0.641 | ¥13.13M | 47.2s |
| **XGBoost (tuned)** | **0.661** | **¥12.76M** | **5.6s** |

**XGBoost** was selected as the best model — highest accuracy and 
8x faster than Random Forest after hyperparameter tuning.

### Top Predictive Features
1. `IsTokyoArea` (27%) — Tokyo metropolitan area flag
2. `TotalFloorArea` (13%) — building size
3. `PropertyAge` (12%) — age of the building at time of transaction
4. `Region_Kanto` (10%) — Kanto region flag
5. `AverageTimeToStation` (5%) — proximity to public transport

---

## 🛠️ Tech Stack

- **Python 3.12**
- **pandas** — data manipulation
- **matplotlib / seaborn** — visualization
- **scikit-learn** — Linear Regression, Random Forest, model evaluation
- **XGBoost** — gradient boosting model
- **Prophet** — time series forecasting
- **Folium** — interactive geographic maps
- **joblib** — model serialization
- **requests** — GeoJSON data fetching

---

## 📦 Dataset

**Source:** [Kaggle — Japanese Housing Prices 2005-2024](https://www.kaggle.com/datasets/brianmcgloughlin/japanese-housing-prices-2005-2024)  
**Original source:** Japan Ministry of Land, Infrastructure, Transport and Tourism (MLIT)  
**Size:** 1,339,147 transactions | 32 features | 2005–2024

> The raw dataset is not included in this repository due to file size.
> Download it from Kaggle and place it in the `data/` folder.

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/yumilin92/japan-housing-analysis.git
cd japan-housing-analysis

# Install dependencies
pip install pandas matplotlib seaborn scikit-learn xgboost joblib

# Launch Jupyter
jupyter notebook
```

---

## 👤 Author

**Yulia Vovk**  
Economics background + Data Science  
📍 Tokyo, Japan  
