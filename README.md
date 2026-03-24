# [PYTHON] RFM Analysis | E-commerce retail
# 📊 Project Title: RFM Analysis
Author: Truong My Le  
Date: 2025-11-12  
Tools Used: Python  

---

## 📑 Table of Contents  
1. [📌 Background & Overview](#-background--overview)  
2. [📂 Dataset Description & Data Structure](#-dataset-description--data-structure)
3. [📃 Main Process](#-main-process)
4. [📊 Key Insights & Visualizations](#-key-insights--visualizations)  
5. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)
 

---

## 📌 Background & Overview  

### Objective:

### 📖 What is this project about? What Business Question will it solve?

This project uses **Python** to analyze **SuperStore's transaction data**, aiming to solve the following business questions:

**✔️ Scalability:** Automate the segmentation process to handle large-scale data that manual tools cannot manage.

**✔️ Behavioral Insight:** Identify and rank customers using statistical quintiles to understand which segments contribute most to the revenue.

**✔️ Strategic Recommendation:** Determine which indicator among R, F, or M is most critical for SuperStore's specific retail model to optimize the marketing budget.

**✔️ Actionable Campaigns:** Provide insights to design personalized holiday programs, shifting potential customers toward the "Loyal" segment.   

### 👤 Who is this project for?  

✔️ Marketing & Sales Teams  

✔️ Data analysts & business analysts 

✔️ Decision-makers

---

## 📂 Dataset Description & Data Structure  

### 📌 Data Source  
- Source: Provided by Superstore Global Sales dataset
- Size: 541,910 rows and 8 columns 
- Format: Excel file (.xlsx)

### 📊 Data Structure & Relationships  

#### 1️⃣ Tables Used:  

- **Table:** The dataset consists of **one primary table** containing all transaction records from 2010 to 2011.

#### 2️⃣ Table Schema & Data Snapshot  

<details>
<summary>🧩 View Key Columns</summary>

| Column Name | Data Type | Description |  
|--------------|------------|-------------|  
| `InvoiceNo` | STRING | Unique invoice number, each transaction. If this code starts with letter 'C', it indicates a cancellation. |  
| `StockCode` | STRING | Product (item) code, each distinct product |  
| `Description` | STRING |  Product (item) name |  
| `Quantity` | INTEGER |  The quantities of each product (item) per transaction |  
| `InvoiceDate` | DATETIME | The day and time when each transaction was generated|  
| `UnitPrice` | INTEGER |  Product price per unit in sterling |  
| `CustomerID` | STRING | Unique customer number |  
| `Country` | STRING | The name of the country where each customer resides. |  

</details>


---

## 📃 Main Process

**1️⃣ Data Cleaning & Preprocessing:**

- **Handle Missing Identifiers:** Removed all records where CustomerID was null, as individual tracking is the foundation of RFM analysis.
  
- **Feature Selection:** Dropped the Description column to reduce data noise and optimize memory usage, as it did not contribute to quantitative segmentation.
  
- **Transaction Validation:** Filtered the dataset to include only records with Quantity > 0. This step is crucial to exclude cancellations and returns, ensuring the Monetary metric reflects actual realized revenue.
  
- **Data Type Standardization:** Converted CustomerID to integer and InvoiceDate to datetime format to allow for precise mathematical calculations of time-based metrics.

**2️⃣ Exploratory Data Analysis (EDA):**

- **Geographic Dominance:** Discovered that the United Kingdom accounts for over 91% of total transactions.

- **Strategic Segmentation Strategy:** Decided to split the analysis into two distinct flows:
  _UK Market:_ Analyzed separately to avoid domestic data overwhelming international trends.
  _International Market:_ Grouped other countries to identify high-potential global regions.

**3️⃣ RFM Analysis & Segmentation:**

- **Metric:**
  
  *Recency (R):* Days since the last purchase.
  
  *Frequency (F):* Total number of unique InvoiceNo entries (Total visits).
  
  *Monetary (M):* Total spend per customer (Quantity × UnitPrice).

- **Segmentation Mapping:**

  <details>
  <summary>🧩 View Segmentation</summary>
  
  | Segment | RFM Score | Description | Strategy |
  |:---|:---|:---|:---|
  | **Champions** | `555, 554, 544, 545, 454, 455, 445` | Best customers who bought most recently, most often, and spend the most. | Reward loyalty with exclusive offers, early access to new products, and invitations to leave reviews. |
  | **Loyal** | `543, 444, 435, 355, 354, 345, 344, 335` | Buy on a regular basis. Responsive to promotions. | Upsell higher value products. Ask for reviews. Engaged them in loyalty programs. |
  | **Potential Loyalist** | `553, 551, 552, 541, 542, 533, 532, 531, 452, 451, 442, 441, 431, 453, 433, 432, 423, 353, 352, 351, 342, 341, 333, 323` | Recent customers with average frequency and spend. | Offer membership / loyalty program, recommend other products. |
  | **New Customers** | `512, 511, 422, 421, 412, 411, 311` | Bought most recently, but not often. | Provide onboarding support. Send "Welcome" emails and discount codes for the next purchase. |
  | **Promising** | `525, 524, 523, 522, 521, 515, 514, 513, 425, 424, 413, 414, 415, 315, 314, 313` | Recent shoppers, but haven't spent much. | Create brand awareness. Offer free trials or short-term discounts. |
  | **Need Attention** | `535, 534, 443, 434, 343, 334, 325, 324` | Above average recency, frequency and monetary values. May not have bought very recently though. | Make limited time offers, Recommend based on past purchases. Reactivate them. |
  | **About To Sleep** | `331, 321, 312, 221, 213, 231, 241, 251` | Below average recency, frequency and monetary values. Will lose them if not reactivated. | Share valuable resources, recommend popular products / renewals at discount, reconnect with them. |
  | **At Risk** | `255, 254, 245, 244, 253, 252, 243, 242, 235, 234, 225, 224, 153, 152, 145, 143, 142, 135, 134, 133, 125, 124` | Spent relatively big money and purchased often. But long time ago. Need to bring them back! | Send personalized emails to reconnect, offer renewals, provide helpful resources. |
  | **Cannot Lose Them** | `155, 154, 144, 214, 215, 115, 114, 113` | Made biggest purchases, and often. But haven't returned for a long time. | Win them back via renewals or newer products, don't lose them to competition; talk to them. |
  | **Hibernating customers** | `332, 322, 233, 232, 223, 222, 132, 123, 122, 212, 211` | Last purchase was long back, low spenders and low number of orders. | Offer other relevant products and special discounts. Recreate brand value. |
  | **Lost customers** | `111, 112, 121, 131, 141, 151` | Lowest recency, frequency and monetary scores. | Revive interest with reach out campaign, ignore otherwise. |  
  
  </details>



## 📊 Key Insights & Visualizations

### 1️⃣ Customer Volume & Distribution (UK)

<img width="957" height="551" alt="Screenshot 2026-03-23 164309" src="https://github.com/user-attachments/assets/0faedb01-e651-4339-8dba-1c4389b5acf2" />

<img width="787" height="569" alt="Screenshot 2026-03-23 155345" src="https://github.com/user-attachments/assets/86056094-64d7-4a66-9516-0a8bb4a80d30" />

🎯Observations:  

**- The Churn Risk:** The largest segment is Hibernating (812 customers, 20.7%), followed by Lost Customers (14.8%). This indicates that over 35% of the UK database has not made a purchase in a long time. The business is facing a significant "leaky bucket" problem.
  
**- The Growth Engine:** Potential Loyalists (12.8%) and New Customers (12.2%) form a solid base of 25%. These are the "fresh blood" of the company that needs to be nurtured into the "Loyal" or "Champion" tiers.
  
**- The Core:** Champions (11.2%) and Loyalists (5.8%) are a minority in headcount but represent the most stable part of the business.

### 2️⃣ Revenue Contribution (UK)

<img width="953" height="556" alt="Screenshot 2026-03-23 164332" src="https://github.com/user-attachments/assets/f2a9becc-5986-4828-9d47-2125f55d0b90" />

<img width="989" height="532" alt="Screenshot 2026-03-23 164355" src="https://github.com/user-attachments/assets/02a7f558-f834-4480-a78d-f41f4211b8a8" />

🎯Observations:  

**- Extreme Revenue Concentration:** Champions contribute a staggering 45.8% of total revenue ($3.8M). This confirms that a small group of elite customers is the primary driver of success.
  
**- Loyalty Payoff:** The Loyal segment, despite being small in number, is the second-highest revenue contributor (8.9%). Combined with Champions, these two groups generate nearly 55% of the total UK revenue.

**- Low Value of Churn:** Even though "Hibernating" customers are the most numerous, they contribute only 5.4% of revenue, suggesting their individual spend was low even when they were active.

### 3️⃣ RFM Heatmap (Average Monetary Value)

<img width="659" height="514" alt="Screenshot 2026-03-23 164412" src="https://github.com/user-attachments/assets/ce3167dd-382b-4547-b841-8f77b02b3872" />

🎯Observations: High Frequency (F) and recent activity (R) are the best predictors of High Monetary (M) value

**- Recency as a Value Multiplier:** As Recency (R Score) increases from 1 to 5, the average monetary value grows significantly across almost all Frequency levels. This proves that "Active" customers spend much more per transaction than "Lapsing" ones.

### 4️⃣ Global Market Analysis (Excluding UK)

<img width="982" height="561" alt="Screenshot 2026-03-23 155452" src="https://github.com/user-attachments/assets/cbabfbab-0233-4b61-a552-08de5e4a19fc" />

<img width="982" height="559" alt="Screenshot 2026-03-23 155502" src="https://github.com/user-attachments/assets/8791f22a-1547-4559-92f9-1c8a55d69267" />

<img width="988" height="480" alt="Screenshot 2026-03-23 164502" src="https://github.com/user-attachments/assets/de391976-d28e-44d1-b8ee-ed015d37019c" />

<img width="975" height="559" alt="Screenshot 2026-03-23 155511" src="https://github.com/user-attachments/assets/75213a0c-3c03-43fa-8dd5-f175cea2a276" />

🎯Observations: 

**- European Strongholds:** Germany and France represent more than 40% of the international customer base. Spain, Belgium, and Switzerland follow as secondary tiers.
 
**- Global Champions:** contribute 12.5% of the global revenue share. This highlights that the "Elite Customer" strategy works universally across borders, not just in the UK.

**- The Loyal and Need Attention segments** combined only contribute 3.2% -> the company struggles to create "Middle-Class" customers. People are either VIPs (Champions) or they are low-value/inactive.

## 🔎 Final Conclusion & Recommendations

📍 Business Status
  
 **-** The company is in a High-Revenue, High-Churn state. While the financial performance is strongly supported by a dedicated "Champion" segment, the foundation is fragile because the vast majority of customers (Hibernating/Lost) are disengaging. The business relies too heavily on a small group (about 17% of people providing 57% of revenue).

📍 Recency (R) is the most critical metric
  
  **-** Looking at our Heatmap, customers with an R-Score of 5 consistently show the highest average spending (Monetary). You cannot drive Frequency (F) or Monetary (M) if the customer is no longer active (Low R).

📍 Recommendations:

**1. High-Value Retention (Champions & Loyal Customers)**

**- Referral Program:** Leverage the strongest asset by rewarding Champions for referring new customers. This shifts the focus from expensive acquisition to organic, high-trust growth.

**- Experiential Rewards:** Prioritize recognition over discounts (personalized "Thank You" gifts) to maintain high brand prestige.

**- VIP Concierge Service:** Establish a "Platinum" membership for Champions, offering exclusive early access to next campaign sales and dedicated support.

**2. Growth & Habit Building (Potential Loyalists & New Customers)**

**- "Bridge the Gap" Strategy:** For Potential Loyalists, implement frequency-based rewards ("3-strike" bundle deals) to convert one-time shoppers into habitual buyers.

**- Welcome Series Onboarding:** For New Customers (~12% of base), launch an automated email series featuring Best-sellers to drive a second purchase within the first 30 days.

**- Upselling/Bundling:** Offer free international shipping or gifts once a specific basket value is reached.

**3. Churn Prevention & Reactivation (Hibernating)**

**-** High-Value "Shock" Coupons: For the Hibernating segment - the largest group, use aggressive, one-time holiday coupons to pull them back into the platform before they are lost forever.

**4. Market & Operational Optimization**

**- Market Pruning:** Instead of spreading the budget thin across 30+ countries, concentrate marketing spend on the Top 5 (UK, Germany, France, Belgium, Spain) to optimize Customer Acquisition Cost (CAC).
