# 📦 Retail Demand Forecasting — Time Series Analysis

> Forecasting monthly furniture sales using SARIMA and Facebook Prophet on the Superstore retail dataset to support inventory planning and procurement decisions.

---

## 📌 Project Overview

Retail businesses lose significant revenue through stockouts and overstock situations driven by poor demand visibility. This project builds an end-to-end time series forecasting pipeline on 9,994 retail orders to predict future furniture category sales — translating raw transactional data into actionable demand signals for inventory replenishment and supply chain planning.

---

## 🗂️ Dataset

| Attribute | Details |
|---|---|
| **Source** | Sample Superstore Dataset (`.xls`) |
| **Total Records** | 9,994 orders |
| **Features** | 21 columns (Order Date, Ship Date, Ship Mode, Category, Sales, Quantity, Discount, Profit, Region, Segment, etc.) |
| **Focus Subset** | Furniture category — 2,121 records |
| **Time Range** | 2014 – 2017 |
| **Granularity** | Daily transactions → resampled to Monthly frequency |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| `Python` | Core programming language |
| `Pandas` | Data wrangling, groupby, resampling |
| `NumPy` | Numerical operations |
| `Statsmodels` | SARIMA model (SARIMAX) |
| `Prophet` | Facebook's forecasting library |
| `Matplotlib` | Time series visualizations |
| `itertools` | Grid search over SARIMA hyperparameters |
| `Google Colab` | Development environment |

---

## 🔄 Project Workflow

```
Raw Superstore Data (.xls)
        │
        ▼
  Data Loading & EDA
  - df.describe(), df.info()
  - Null checks, dtype validation
        │
        ▼
  Data Preprocessing
  - Filter: Category == 'Furniture'
  - Set Order Date as index
  - Resample to Monthly frequency (sum of Sales)
        │
        ▼
  Time Series Decomposition
  - Visualize trend, seasonality, residuals
        │
        ├──────────────────────────────────┐
        ▼                                  ▼
  SARIMA Model                      Facebook Prophet
  - Grid search (p,d,q)(P,D,Q)      - Yearly seasonality
  - AIC-based model selection        - 12-month forecast
  - Forecast + 95% CI                - Confidence intervals
        │                                  │
        └──────────────┬───────────────────┘
                       ▼
           Forecast Visualization
           & Demand Insights
```

---

## 📊 Key Steps

### 1. Exploratory Data Analysis
- Inspected dataset shape, data types, and statistical summary
- Filtered to Furniture category and validated 2,121 records
- Grouped by Order Date and aggregated monthly sales to create time series

### 2. Time Series Decomposition
- Visualized observed sales trend, seasonal patterns, and residuals
- Identified annual seasonality with recurring Q4 sales peaks

### 3. SARIMA Modeling
- Performed automated grid search across all combinations of:
  - `p, d, q` — non-seasonal order parameters
  - `P, D, Q` — seasonal order parameters
- Selected the optimal model configuration using **AIC (Akaike Information Criterion)**
- Generated a **12-month forecast** with **95% confidence intervals**
- Evaluated model fit with residual diagnostics

### 4. Facebook Prophet
- Trained a Prophet model with yearly seasonality enabled
- Produced a comparative 12-month forecast
- Visualized trend and seasonality components

---

## 📈 Results & Business Insights

- **Seasonal Demand Peaks:** Furniture sales consistently rise in Q3–Q4, enabling proactive inventory build-up ahead of peak demand
- **Forecast Confidence Intervals:** 95% CI bands quantify demand uncertainty, directly informing safety stock calculations
- **Demand Signals:** Monthly forecasts allow procurement teams to align purchase orders with lead times, reducing stockout risk and excess inventory carrying costs

---

## 💡 Business Applications

| Insight | Supply Chain Action |
|---|---|
| Q4 demand spike identified | Pre-position inventory 6–8 weeks ahead |
| Low-demand months (Q1) | Reduce reorder quantities, minimize carrying cost |
| Forecast uncertainty (CI width) | Adjust safety stock buffer dynamically |
| Multi-model comparison | Validate forecast reliability before operational use |

---

## 📁 Repository Structure

```
├── Time_Series_Step_By_Step.ipynb   # Main analysis notebook
├── Sample_-_Superstore.xls          # Source dataset
└── README.md                        # Project documentation
```

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/retail-demand-forecasting.git
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib statsmodels prophet openpyxl
   ```

3. **Run the notebook**
   - Open `Time_Series_Step_By_Step.ipynb` in Jupyter or Google Colab
   - Upload `Sample_-_Superstore.xls` to your Colab Drive or local directory
   - Update the file path in the data loading cell
   - Run all cells sequentially

---

## 📚 Skills Demonstrated

- Time series data preprocessing (resampling, indexing, aggregation)
- Seasonal decomposition and trend analysis
- SARIMA hyperparameter tuning via grid search and AIC selection
- Demand forecasting with confidence interval estimation
- Comparative model evaluation (SARIMA vs. Prophet)
- Supply chain insight generation from forecasting outputs

---

## 👤 Author

**Sarth Jayesh Patel**  
MS Information Management (Data Analytics) — University of Illinois Urbana-Champaign  
📧 sarthp870@gmail.com | 🔗 [LinkedIn](https://linkedin.com/in/sarth-patel-s1411)
