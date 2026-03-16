# Telco Customer Churn (Python + Power BI)

## Goal
Clean the **Telco Customer Churn** dataset in **Jupyter (Python)**, export cleaned tables (CSV), and build a **Power BI** churn dashboard.

## Dataset
Input file: `WA_Fn-UseC_-Telco-Customer-Churn.csv`  
Target column: `Churn` (Yes/No)

## Run (Jupyter)
1. Put CSV in the notebook folder (or update the path in code).
2. Run the notebook to:
   - Fix types (especially `TotalCharges`)
   - Create `ChurnFlag` (0/1)
   - Add features like `TenureBand`, `MonthlyChargesBand`, `CLV_Proxy`
   - (Optional) create `ChurnProbability` + `RiskBucket`
3. Exports will be generated as CSV.

## Outputs for Power BI
- `exports/fact_customer_churn.csv` (main cleaned dataset)
- `exports/agg_churn_drivers.csv` (churn by Contract/InternetService/PaymentMethod/etc.)
- `exports/agg_tenure_cohort.csv` (churn rate by tenure)

## Power BI
Power BI Desktop → **Get Data → Text/CSV** → load the exported CSVs.  
Create measures:
- `Customers = COUNTROWS(fact_customer_churn)`
- `Churned = SUM(fact_customer_churn[ChurnFlag])`
- `Churn Rate = DIVIDE([Churned], [Customers])`

## Suggested Dashboard
- KPI cards: Customers, Churned, Churn Rate
- Bar charts: Churn Rate by Contract, InternetService, PaymentMethod
- Line: Churn Rate by tenure (cohort)
