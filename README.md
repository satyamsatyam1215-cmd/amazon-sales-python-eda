# 📊 Amazon E-Commerce Sales Analysis Report
**Portfolio Case Study | Data Analytics & Business Intelligence**  
*Author: Data Analyst Portfolio Project*  
*Tech Stack: Python (Pandas, NumPy, Matplotlib, Seaborn)*

---

## 📌 Executive Summary

This project conducts an end-to-end exploratory data analysis (EDA) of **185,000+ e-commerce sales transactions** from Amazon across the United States. Utilizing **Python (Pandas, Matplotlib, Seaborn)**, the analysis identifies revenue drivers, customer purchasing patterns, temporal peak hours/months, pricing dynamics, and regional market distribution.

### Key Performance Indicators (KPIs)
* **Total Revenue Generated:** **$34,465,000 ($34.47M)** (344.65 Lakhs)
* **Total Quantity Sold:** **208,812 units**
* **Total Orders Processed:** **185,686 orders**
* **Top Revenue Product:** **Macbook Pro Laptop ($8.03M)** — accounts for **23.3%** of total revenue.
* **Top Volume Product:** **AAA Batteries 4-Pack (30,986 units)**.
* **Top Revenue Category:** **Laptops ($12.16M / 35.3%)**, followed by **Phones ($8.94M / 26.0%)**.
* **Peak Revenue Season:** **Q4 ($11.54M / 33.5%)**, driven by December ($4.61M) holiday demand.
* **Top Geographic Market:** **San Francisco ($8.26M / 23.97% of total revenue, 42,898 orders)**.
* **Peak Shopping Hours:** **11:00 AM – 1:00 PM** (Mid-day peak) and **6:00 PM – 8:00 PM** (Evening peak).

---

## 🛠️ Data Pipeline & Methodology

### 1. Data Cleaning & Feature Engineering
- **Date-Time Parsing:** Converted `Order Date` into standard datetime objects to extract temporal metrics: `Month`, `Quarter`, `Day of Week`, `Hour`, and `Time Slot`.
- **Location Extraction:** Split `Purchase Address` into distinct `City` and `State` variables (e.g., `San Francisco (CA)`).
- **Categorization Logic:**
  - **Price Category:**
    - `Budget` (< $50)
    - `Affordable` ($50 – $200)
    - `Mid Range` ($200 – $500)
    - `Premium` (> $500)
  - **Time Slots:** `Morning` (6 AM–12 PM), `Afternoon` (12 PM–5 PM), `Evening` (5 PM–9 PM), `Night` (9 PM–12 AM), `Late Night` (12 AM–6 AM).
- **Derived Metrics:** `Total Sales = Quantity Ordered * Price Each`.

---

## 📈 Exploratory Data Analysis & Deep Insights

### 1. Product-Level Revenue vs. Volume Matrix

| Product | Category | Avg Price ($) | Total Quantity Sold | Total Sales ($) | Revenue Share (%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Macbook Pro Laptop** | Laptop | $1,700 | 4,725 | $8,032,000 (80.32L) | 23.30% |
| **iPhone** | Phone | $700 | 6,847 | $4,793,000 (47.93L) | 13.91% |
| **ThinkPad Laptop** | Laptop | $1,000 | 4,128 | $4,128,000 (41.28L) | 11.98% |
| **Google Phone** | Phone | $600 | 5,529 | $3,317,000 (33.17L) | 9.62% |
| **27in 4K Gaming Monitor** | Monitor | $390 | 6,239 | $2,433,000 (24.33L) | 7.06% |
| **34in Ultrawide Monitor** | Monitor | $380 | 6,192 | $2,353,000 (23.53L) | 6.83% |
| **Apple Airpods Headphones** | Headphones | $150 | 15,637 | $2,346,000 (23.46L) | 6.81% |
| **Flatscreen TV** | TV | $300 | 4,813 | $1,444,000 (14.44L) | 4.19% |
| **Bose SoundSport Headphones** | Headphones | $100 | 13,430 | $1,343,000 (13.43L) | 3.90% |
| **27in FHD Monitor** | Monitor | $150 | 7,541 | $1,131,000 (11.31L) | 3.28% |
| **Vareebadd Phone** | Phone | $400 | 2,068 | $827,000 (8.27L) | 2.40% |
| **20in Monitor** | Monitor | $110 | 4,126 | $454,000 (4.54L) | 1.32% |
| **LG Washing Machine** | Home Appliance | $600 | 666 | $400,000 (4.00L) | 1.16% |
| **LG Dryer** | Home Appliance | $600 | 646 | $388,000 (3.88L) | 1.13% |
| **Lightning Charging Cable** | Charging Cable | $15 | 23,169 | $346,000 (3.46L) | 1.00% |
| **USB-C Charging Cable** | Charging Cable | $12 | 23,931 | $286,000 (2.86L) | 0.83% |
| **Wired Headphones** | Headphones | $12 | 20,524 | $246,000 (2.46L) | 0.71% |
| **AA Batteries (4-pack)** | Battery | $4 | 27,615 | $106,000 (1.06L) | 0.31% |
| **AAA Batteries (4-pack)** | Battery | $3 | 30,986 | $93,000 (0.93L) | 0.27% |

#### 🔍 Key Takeaways:
1. **Inverse Price-Volume Relationship:** Products with lower average prices (e.g., AAA Batteries at $3, USB-C Cables at $12) command the highest sales volume (30,986 and 23,931 units respectively), while high-ticket items (Macbook Pro at $1,700) generate low volume (4,725 units) but dominate revenue ($8.03M).
2. **Flagship Ecosystem Concentration:** Premium hardware (Macbook Pro + ThinkPad + iPhone + Google Phone) yields **$20.27M**, representing **58.8%** of total business revenue.

---

### 2. Category Performance Analysis

```
                    Sales by Category ($ Millions)
Laptop          ██████████████████████████████████████ $12.16M
Phone           ███████████████████████████ $8.94M
Monitor         ███████████████ $6.37M
Headphones      █████████ $3.93M
TV              ████ $1.44M
Home Appliance  ██ $0.79M
Charging Cable  █ $0.63M
Battery         ▍ $0.20M
```

- **Top Revenue Category:** **Laptops ($12.16M / 121.60L)**, driven by high average selling price ($1,373.53).
- **Top Volume Category:** **Batteries (58,601 units)** and **Headphones (49,591 units)**.
- **Price Segment Dominance:** **Premium products ($210.58L / $21.06M)** account for **61.1%** of overall revenue, whereas **Budget products ($10.77L / $1.08M)** represent only **3.1%**.

---

### 3. Temporal & Seasonal Sales Dynamics

#### Monthly Sales & Order Trends
- **Peak Month:** **December** ($4.61M sales | 24,944 orders) due to end-of-year holiday promotions and festive gifting.
- **Secondary Peak:** **April** ($3.39M sales | 18,257 orders) and **October** ($3.74M sales | 20,249 orders).
- **Trough Period:** **September** ($2.09M sales | 11,603 orders) and **January** ($1.82M sales | 9,699 orders) show post-holiday drops.

#### Quarterly Performance Breakdown
* **Q1 (Jan–Mar):** $6.83M (19.8%)
* **Q2 (Apr–Jun):** $9.12M (26.4%)
* **Q3 (Jul–Sep):** $6.98M (20.3%)
* **Q4 (Oct–Dec):** **$11.54M (33.5%)**

#### Daily & Hourly Customer Behavior
* **Peak Days:** **Tuesday ($5.09M sales | 26,063 orders)** leads total revenue and activity, followed by **Sunday ($4.93M)**.
* **Peak Hours:** 
  - **Lunch Window (11:00 AM – 1:00 PM):** Peak at 12 PM with **$2.31M sales & 12,080 orders**.
  - **Evening Window (6:00 PM – 8:00 PM):** Peak at 7 PM (19:00) with **$2.41M sales & 12,380 orders**.
* **Time Slot Aggregate:** **Afternoon ($10.39M)** > **Evening ($9.04M)** > **Morning ($8.26M)** > **Night ($4.83M)** > **Late Night ($1.95M)**.

---

### 4. Geographic & Regional Market Distribution

```
                    Sales by City ($ Millions)
San Francisco   ██████████████████████████████████████ $8.26M (42,898 orders)
Los Angeles     ███████████████████████ $5.45M (28,498 orders)
New York City   ███████████████████ $4.66M (23,848 orders)
Boston          ███████████████ $3.66M (19,092 orders)
Atlanta         ███████████ $2.79M (14,253 orders)
Dallas          ███████████ $2.77M (14,240 orders)
Seattle         ███████████ $2.75M (14,119 orders)
Portland        █████████ $2.32M (11,980 orders)
Austin          ███████ $1.82M (9,509 orders)
```

- **California Concentration:** West Coast tech hubs (**San Francisco + Los Angeles**) generate **$13.70M** or **39.8%** of total US revenue.
- **Top 3 Cities:** **San Francisco, Los Angeles, and New York City** combined generate **$18.37M (53.3% of total revenue)**.

---

## 🎯 Strategic Business Recommendations

### 1. Cross-Selling & Product Bundling
* **Phone + Cable / Case Bundles:** High volume products like Lightning Cables (23.1k units) and USB-C Cables (23.9k units) should be automatically suggested at checkout with iPhones and Google Phones.
* **Laptop Companion Kits:** Offer discounted AirPods or Bose Headphones when customers purchase a Macbook Pro or ThinkPad Laptop to increase Average Order Value (AOV).

### 2. Marketing & Ad Campaign Optimization
* **Hourly Ad Scheduling (Dayparting):** Concentrate digital advertising spend during the two peak buying windows (**11:00 AM – 1:00 PM** and **6:00 PM – 8:00 PM**) to maximize conversion rates.
* **Seasonal Campaign Push:** Heavy up marketing efforts starting in **October** through **December** to capture the Q4 holiday surge ($11.54M revenue window).

### 3. Inventory & Regional Logistics Management
* **Regional Hub Allocation:** Stock high-demand electronics (Laptops and Monitors) heavily in **San Francisco, Los Angeles, and New York** fulfillment centers to enable same-day/next-day shipping.
* **Low-Margin Inventory Efficiency:** Re-evaluate storage for high-volume, low-margin goods (Batteries) to optimize warehouse space for high-margin electronics.

---

## 💻 Python Code Architecture (Portfolio Documentation)

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Data Cleaning & Feature Engineering
df = pd.read_csv('Amazon_Sales_Data.csv')
df = df.dropna(how='all')

# Datetime conversion
df['Order Date'] = pd.to_datetime(df['Order Date'], errors='coerce')
df['Month'] = df['Order Date'].dt.month_name()
df['Month_Num'] = df['Order Date'].dt.month
df['Quarter'] = df['Order Date'].dt.quarter
df['Day_of_Week'] = df['Order Date'].dt.day_name()
df['Hour'] = df['Order Date'].dt.hour

# Calculations
df['Quantity Ordered'] = pd.to_numeric(df['Quantity Ordered'], errors='coerce')
df['Price Each'] = pd.to_numeric(df['Price Each'], errors='coerce')
df['Sales'] = df['Quantity Ordered'] * df['Price Each']

# Extract City
def get_city(address):
    return address.split(',')[1].strip() if pd.notnull(address) else ''

df['City'] = df['Purchase Address'].apply(get_city)

# Time Slot Feature
def time_slot(hour):
    if 6 <= hour < 12: return 'Morning'
    elif 12 <= hour < 17: return 'Afternoon'
    elif 17 <= hour < 21: return 'Evening'
    elif 21 <= hour < 24: return 'Night'
    else: return 'Late Night'

df['Time Slot'] = df['Hour'].apply(time_slot)

# Price Category Feature
def price_category(price):
    if price < 50: return 'Budget'
    elif price < 200: return 'Affordable'
    elif price < 500: return 'Mid Range'
    else: return 'Premium'

df['Price Category'] = df['Price Each'].apply(price_category)

# 2. Aggregations & Visualizations
sales_by_product = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
sales_by_city = df.groupby('City')['Sales'].sum().sort_values(ascending=False)
hourly_sales = df.groupby('Hour')['Sales'].sum()

print("Data processing & EDA successfully executed.")
```

---

## 🏆 Conclusion & Portfolio Summary

This project showcases a complete analytics lifecycle: **Data Extraction → Data Cleaning → Feature Engineering → Exploratory Data Analysis → Strategic Actionable Recommendations**. The findings highlight clear opportunities for cross-selling premium tech accessories, optimizing ad schedules around peak hours, and prioritizing fulfillment logistics in top-performing urban centers.
