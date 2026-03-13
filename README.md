# 📊 Credit Risk EDA Case Study

> Exploratory Data Analysis to identify patterns in loan application data that drive credit default risk.

---

## 🧠 Objective

Financial institutions face significant losses when loans are approved for applicants who are unable to repay. This case study uses **Exploratory Data Analysis (EDA)** to uncover the key factors that distinguish defaulters (Target = 1) from non-defaulters (Target = 0) — enabling smarter, data-driven lending decisions.

---

## 📁 Dataset

Two datasets from a real-world lending institution:

| File | Description |
|------|-------------|
| `application_data.csv` | Current loan applications with client demographics, financials, and repayment history |
| `previous_application.csv` | Historical loan applications and their outcomes for the same clients |

**Target Variable:** `TARGET` — `1` = client had payment difficulties, `0` = all payments on time

---

## 🔍 Analysis Workflow

### 1. Data Cleaning
- Identified and dropped columns with **>13% missing values**
- Applied **percentile clipping** (5th–95th) to handle outliers in skewed numeric columns such as `AMT_ANNUITY`, `AMT_GOODS_PRICE`, and social circle observation counts
- Imputed remaining nulls using **mean** (numeric) and **mode/domain logic** (categorical)

### 2. Feature Engineering
- **`LOAN_PERIOD`** — derived as `AMT_CREDIT / AMT_ANNUITY` to estimate loan duration
- **`AGE`** — converted from `DAYS_BIRTH` (negative days) to positive years
- **`AGE_BIN`** — bucketed age into decade ranges (11–20, 21–30, ..., 61–70) for cohort analysis

### 3. Univariate Analysis
Compared distributions across Target = 0 and Target = 1 for:
- Income type (`NAME_INCOME_TYPE`)
- Education level (`NAME_EDUCATION_TYPE`)
- Family status (`NAME_FAMILY_STATUS`)
- Housing situation (`NAME_HOUSING_TYPE`)
- Contract type (`NAME_CONTRACT_TYPE`)
- Day of week for application (`WEEKDAY_APPR_PROCESS_START`)

### 4. Bivariate & Correlation Analysis
- **Pearson correlation heatmaps** for both defaulter and non-defaulter segments
- **Scatter plots** exploring relationships between credit amount, goods price, and annuity
- **Box plots** comparing numerical variables across risk segments

### 5. Previous Application Analysis
- Univariate analysis of contract type, contract status, and client type from historical applications
- Correlation heatmap for previous application dataset
- Scatter plot confirming linear relationship between `AMT_APPLICATION` and `AMT_GOODS_PRICE`

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core analysis language |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations |
| Matplotlib | Visualization |
| Seaborn | Statistical plots and heatmaps |
| Jupyter Notebook | Interactive analysis environment |

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone 
cd <repo-name>

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Launch the notebook
jupyter notebook EDA_Case_Study_Final.ipynb
```

> **Note:** Place `application_data.csv` and `previous_application.csv` in the same directory as the notebook before running.

---

## 👥 Authors

- **Rudra Varade** — [GitHub](https://github.com/rudravarade101-boop)


---

## 📌 Key Takeaways

- Clients with **lower education levels** and **working income type** were more represented among defaulters
- **Loan period** and **annuity amount** showed notable distributional differences between risk segments
- A strong **linear relationship** exists between `AMT_GOODS_PRICE` and `AMT_APPLICATION` in previous applications, suggesting consistent pricing behavior
- **Age** is a meaningful risk differentiator — younger borrowers showed higher default rates

---

*This project was completed as part of a data analytics case study to develop practical EDA skills on real-world financial data.*
