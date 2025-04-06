# 🏡 House Price Prediction Web App

## 📌 About the Project

This project is a complete end-to-end **House Price Prediction Web Application** built using **Machine Learning** and a real-world dataset inspired by the **Gurgaon housing market**. It began as a classic regression problem but quickly evolved into a multi-functional product that combines:

- **Predictive Modeling**
- **Recommendation System**
- **Visual Analytics**
- And a fully interactive **web interface**

The goal was to go beyond the typical ML regression project and create a solution that mirrors a real estate tech product — helpful for both buyers and analysts.

---

## 🏙️ Real-World Focus: Gurgaon Housing Market

To give this project a **realistic business edge**, the focus was narrowed down to **Gurgaon (Gurugram)** — one of India’s rapidly developing cities with a highly organized real estate sector. The city's **sector-based structure** made it ideal for analyzing price trends and regional comparisons.

To gather meaningful insights and define the data schema, I referred to **property listings from [99acres.com](https://www.99acres.com/)**. This helped in:
- Understanding how listings are described in the real world
- Identifying key features like BHK, area (sq ft), furnishing, locality, etc.
- Mimicking the kind of experience users expect from real estate platforms

This grounding in real-world data makes the app much more than a data science demo — it's a **prototype for a practical solution**.

---

## ✅ Project Features

1. **🏠 Price Predictor**  
   A trained regression model that estimates property prices based on location, size, furnishing, and other features.

2. **🧠 Recommendation System**  
   Recommends similar houses based on user preferences (area, price range, BHK, etc.).

3. **📊 Analytics & Visual Insights**  
   Interactive plots and heatmaps to show pricing trends across sectors, popular property types, and more.

4. **🖥️ Web Application**  
   Developed using **Flask**, **HTML/CSS/JS**, and integrated with ML models — offering a sleek, responsive user interface.

---




## 🚧 Development Workflow

The project followed a structured pipeline to ensure accuracy, explainability, and usability. Below is a breakdown of each key stage:

---

### 📥 Stage 1: Data Gathering  
Collected structured property data focused on **Gurgaon**. The dataset includes features like:
- Location (sector/locality)
- Number of bedrooms (BHK)
- Property size (in sq. ft.)
- Furnishing status
- Price (target variable)

Data inspiration and schema were designed by referencing real listings from **99acres.com**.

---

### 🧹 Stage 2: Data Cleaning  
Performed thorough preprocessing to handle:
- Duplicates and inconsistent entries  
- Noise in location names (e.g., "Sector-56" vs "Sec 56")  
- Formatting issues (removing units from text like "1500 sq ft")

---

### 🧠 Stage 3: Feature Engineering  
- Extracted new features such as **price per sq ft**, **property age**, and **sector groupings**.  
- Grouped rare or inconsistent locality names into broader regions.  
- Converted categorical data using **label encoding** and **one-hot encoding**.

---

### 📊 Stage 4: Exploratory Data Analysis (EDA)  
Generated:
- Distribution plots for price, BHK, and area  
- Correlation heatmaps  
- Boxplots and violin plots to detect outliers  
- Region-wise average price comparisons

---

### 🚨 Stage 5: Outlier Removal  
- Used domain knowledge and statistical methods (IQR, Z-score) to remove extreme values that could distort the model.  
- Examples:  
   - Properties priced unreasonably high or low  
   - Area mismatch with price (e.g., 100 sq ft house priced in crores)

---

### 🧩 Stage 6: Missing Value Imputation  
- Imputed missing values based on:
  - **Mean/median** (for numerical features)  
  - **Mode or nearest neighbor logic** (for categorical ones)

---

### 📌 Stage 7: Feature Selection  
- Used **correlation analysis**, **mutual information**, and **model-based importance (like XGBoost feature importances)**  
- Kept only the most relevant features for better performance and explainability

---

### 🧪 Stage 8: Model Selection & Hyperparameter Tuning  
Tried multiple regression models:
- Linear Regression  
- Decision Tree Regressor  
- Random Forest Regressor  
- XGBoost  
- Gradient Boosting Regressor

**Best model selected based on R², RMSE, and cross-validation.**  
Tuned using `GridSearchCV` and `RandomizedSearchCV`.

---

### 📈 Stage 9: Analytics & Insight Module  
Built a powerful **analytics dashboard** for exploring:
- Price trends by location and BHK  
- Furnishing status influence  
- Sector-based heatmaps  
- Top recommended areas for investment

Interactive plots were made using **Plotly**, **Seaborn**, and **Matplotlib**.

---

### 🤖 Stage 10: Recommendation System  
A lightweight content-based system suggesting similar houses based on:
- Price range  
- Area  
- BHK  
- Sector proximity

Built using **cosine similarity** and custom filtering logic.

---

### 🌐 Stage 11: Web App Development  
- Backend: **Flask**  
- Frontend: **HTML, CSS, JavaScript, Bootstrap**  
- Connected model inference, analytics module, and recommender to a clean UI

---

### 🚀 Stage 12: Deployment  
Deployed the app using:
- **Render / Heroku** (Flask backend)  
- **GitHub Pages or Netlify** (if frontend is separated)  
- Ensured it runs end-to-end: user inputs -> prediction + visualization + recommendations

---




# **📦 Stage 1: Data Collection – The Foundation of the Project**

The first step of the project was to gather real-world data that reflects the actual property market. Since the objective was to predict house prices and recommend similar listings, I chose **Gurugram (Gurgaon)** — a city where properties are well-structured across sectors, making it suitable for spatial and categorical analysis.

#### 🔍 Data Source
I collected data from **[99acres.com](https://www.99acres.com/)**, a popular Indian real estate listing platform.

#### 🧰 Tools Used
- **Python**
- **BeautifulSoup** for HTML parsing and scraping
- **Requests** for making HTTP calls
- **Pandas** for data structuring and storage

#### 🏘️ What I Scraped
I scraped **flats, houses, and apartment listings**, ensuring the dataset covered all types of residential properties. For each listing, I collected details such as:

```python
property_data = {
    'property_name': ...,  
    'link': ...,  
    'society': ...,  
    'price': ...,  
    'area': ...,  
    'areaWithType': ...,  
    'bedRoom': ...,  
    'bathroom': ...,  
    'balcony': ...,  
    'additionalRoom': ...,  
    'address': ...,  
    'floorNum': ...,  
    'facing': ...,  
    'agePossession': ...,  
    'nearbyLocations': ...,  
    'description': ...,  
    'furnishDetails': ...,  
    'features': ...,  
    'rating': ...,  
    'property_id': ...
}
```

---

#### ⚠️ Real Challenges Faced

- **IP Blocking:** Due to scraping limits on the site, I had to run the scraper multiple times with strategic delays and retries to avoid getting blocked.
- **Data Inconsistency:** Flats and houses had different formats and available features, so I carefully handled missing fields and normalized them across categories.

---

#### 🔄 Final Dataset Preparation

- Scraped **multiple categories**: flats, houses, and apartments.
- Merged all datasets and **shuffled entries** to ensure randomness and reduce ordering bias.
- Stored the final dataset in a **clean, structured format** (CSV/Excel) ready for preprocessing and model training.




---

# 🧹 **Stage 2: Data Cleaning – From Raw to Reliable**

Before building any machine learning model, the foundation lies in **cleaning and understanding the data**. Raw real estate data is often inconsistent, messy, and incomplete — so I took this stage seriously and applied **both domain knowledge and logic** to build a high-quality dataset.

---

#### 🛠️ What Cleaning Involved:

✅ **Initial Manual Checks in Excel**  
- Both *flat* and *house* datasets were first opened in Excel to quickly spot and drop blatantly wrong or irrelevant entries (e.g., blank rows, unreadable formats).
- This made it easier to manage smaller sections and speed up the cleaning phase inside Jupyter Notebook.

✅ **Scripted Cleaning in Jupyter**  
After initial Excel-based cleanup, both datasets were loaded into Python for a deeper, programmable cleaning process.  
Here’s what was handled:

- **Separate cleaning** for flats and houses (since they had slightly different structures).
- **Merging** both after cleaning to form a unified dataset.
- **v2 Deep Cleaning** post-merge to remove inconsistency between overlapping fields (e.g., different area formats).

---

#### 🔎 Smart & Logical Cleaning Decisions

Here are some specific actions I took using both research and common sense:

- 🔁 **Dropped entries where price was listed as "Price on Request"**, since these are not usable for ML predictions.
- 🔍 **Cleaned and standardized area units** (e.g., `Sq. Ft.` → numeric).
- 🧼 **Removed inconsistent or duplicate entries** that could skew results.
- 🧠 **Used domain understanding** to decide which rows are valuable, which ones aren't (e.g., listings without bedroom/bathroom count were removed).
- 🚫 **Handled “junk columns”** or rarely filled text columns by dropping or consolidating them.

---

#### 📄 Final Columns After Cleaning

After thorough filtering, renaming, parsing, and formatting, the final cleaned dataset was saved as:  
📁 `gurgaon_properties.csv`  

It contains the following **clean, usable columns**:

```text
['property_name', 'property_type', 'society', 'price', 'price_per_sqft',
 'area', 'areaWithType', 'bedRoom', 'bathroom', 'balcony',
 'additionalRoom', 'address', 'floorNum', 'facing', 'agePossession',
 'nearbyLocations', 'description', 'furnishDetails', 'features',
 'rating', 'noOfFloor']
```

---

#### 📊 Final Dataset Summary

- ✅ **4,000+ usable property records**
  - Around **3,000+ flats**
  - Around **1,000+ houses**
- 🎯 All key features like area, price, rooms, location, and amenities are retained and formatted.
- 💾 Stored as: `gurgaon_properties.csv` — this acts as the **master dataset** for all further stages like EDA, ML modeling, recommendations, and analytics.



---
---



# **Stage 3:🔧 Feature Engineering**

After data cleaning, the dataset was enhanced through careful feature engineering — a crucial step to convert raw, unstructured values into meaningful and predictive features. This process combined domain knowledge with analytical techniques to enrich the data and boost model performance.

### 🧠 Key Highlights

- **Area Parsing & Conversion**
  - Extracted numerical values from `areaWithType` column using regular expressions.
  - Converted all area types (e.g., Carpet, Built-up, Super Built-up) into a common unit (sq.ft).
  - Created separate columns for easier downstream processing.

- **Price per Sqft**
  - Introduced a new column `price_per_sqft` by dividing total price by usable area.
  - This normalized feature helps in comparing properties across different configurations.

- **Room Feature Extraction**
  - Parsed `additionalRoom` column to identify and encode:
    - `has_servant_room`
    - `has_store_room`
  - These utility features add functional and value-based signals for each listing.

- **Furnishing Standardization**
  - Cleaned `furnishDetails` column to extract structured furnishing types.
  - Created a categorical `furnishing_type` feature: 
    - Unfurnished
    - Semi-Furnished
    - Fully-Furnished

- **Possession Age Categorization**
  - Designed a custom function to convert textual values in `agePossession` into 5 interpretable buckets:
    - 🟢 New Property
    - 🟡 Relatively New
    - 🟠 Moderately Old
    - 🔴 Old Property
    - 🔨 Under Construction

---

### 💎 Luxury Score & Clustering

To capture the lifestyle and luxury quotient of each property, a scoring and clustering system was developed:

- Created a **luxury feature dictionary** assigning weighted scores to 100+ premium amenities (e.g., Golf Course, Concierge, Infinity Pool, Spa).
- Calculated a **`luxury_score`** by summing the weights of features present in each listing.
- Applied the **Elbow Method** to cluster properties into:
  - **Standard**
  - **Mid-range**
  - **Luxury**

These engineered features allowed the model to distinguish properties not just by size or price, but by **lifestyle value** — making the dataset ready for sophisticated modeling and pricing recommendations.

---

📁 The final dataset from this stage was saved as:  
`gurgaon_properties_featured.csv`


---

# 🧠 **Stage 4: Exploratory Data Analysis (EDA) – Gurgaon Properties 🏡**

After comprehensive **feature engineering**, a detailed Exploratory Data Analysis (EDA) was conducted to understand the underlying patterns, distributions, and relationships in the Gurgaon real estate dataset.

This EDA is categorized into three key notebooks:

- 📘 `univar.ipynb` → Univariate Analysis
- 📙 `multivariateEda.ipynb` → Multivariate Analysis
- 📗 `pandas_profiling.ipynb` → Automated Profile Report

---

## 📌 Univariate Analysis Highlights

### 🏘️ Property and Society Distribution
- ~13% properties are **independent houses**.
- **675 unique societies** identified:
  - Top 75 societies = 50% of all listings.
  - **308 societies** have only **1 property** listed.
  - Just **1 society** has more than **100 listings**.

### 🗺️ Sector-wise Listings
- Total of **113 sectors**:
  - Only 3 sectors have more than 100 listings.
  - Majority (63 sectors) fall in the 10–49 listings range.

### 💰 Price Distribution
- **Mean Price**: ₹2.53 Cr | **Median Price**: ₹1.52 Cr
- **Range**: ₹0.07 Cr – ₹31.5 Cr
- **Skewness**: 3.28 → heavily right-skewed
- **Kurtosis**: 14.93 → extreme outliers
- **IQR**: ₹0.95 Cr – ₹2.75 Cr
- **Outliers**: 425 properties priced above ₹5.46 Cr

### 📦 Built-up and Super Area
- **Built-up Area**: Mostly 500–3500 sq.ft (Right-skewed)
- **Super Area**: Typically 1000–2500 sq.ft, with some outliers

### 🧱 Floor Distribution
- Majority of properties are between **1st–4th floor**.
- A few listings report 20+ floors, mostly apartments or commercial units.

---

## 🔍 Multivariate Analysis Highlights

### 📊 Property Type vs Price & Area
- **Bar plots** show Villas have **higher median price & area**.
- **Box plots** show Villas exhibit **more price variability**.

### 🛏️ Bedrooms and Property Type Correlation
- **Heatmaps** indicate:
  - Apartments: 2–3 BHK dominate
  - Villas: Wider range (up to 6+ BHK)

### 📈 Area vs Price
- **Scatter plot** confirms a **positive correlation**.
- Coloring by `furnishing status` or `age` reveals deeper feature interactions.

### ⏳ Possession Age vs Price
- Newer properties command **higher prices**.
- Older properties (>10 years) tend to have **stable or declining** value.

### 🌐 Sector-Level Price Heatmap
- Large inter-sector variation.
- Certain sectors show **consistently high average prices**, indicating premium locations.

---

## 🔧 Data Transformation

- Applied **log transformation**: `np.log1p()` on skewed variables like `price`.
- Transformed values are reversible using `np.expm1()` when needed.

---

## ⚠️ Key Takeaways

- Strong **right-skewed distributions** in price and area.
- High **inequality in society and sector distribution**.
- Clear correlation between **property type, area, bedrooms, and price**.
- Multivariate plots helped uncover **latent patterns and outlier behavior**.

---

# 🏡 **Stage 5: Outlier Detection & Removal**

Outliers can distort data insights and negatively impact the performance of machine learning models. This phase focuses on detecting and handling outliers in key real estate features such as `price`, `price per sqft`, and `area-to-room ratio` to ensure **data consistency**, **accuracy**, and **interpretability**.

---

## 📌 Objectives

- Identify and remove **incorrect**, **illogical**, and **extreme outliers**.
- Preserve **genuine high-end property data** for realistic market representation.
- Apply **domain-specific logic** (e.g., area-to-room ratio) for validation.
- Improve the dataset for downstream **modeling and visualization**.

---

## 🔍 Why Outlier Detection Matters

Outliers can arise from:
- **Data entry errors** (e.g., extra/missing zeros).
- **Unrealistic feature combinations** (e.g., 7 BHK in 700 sqft).
- **Rare or luxury properties** (which should be verified and retained).
- **Small area with large price** or vice versa, distorting `price per sqft`.

### ❗ Effects of Outliers:
- **Skewed distributions**, hiding real data trends.
- **Misleading summary statistics** (e.g., mean, std).
- **Inaccurate machine learning models**.
- **Uninterpretable visualizations**.

---

## ⚙️ Steps Followed

### 1. **Outlier Detection in `price` Column** ✅ *(More Treatment Done Here)*

- **Plotted the distribution** and used **boxplot** for visual detection.
- Applied **IQR method**:
  - `IQR = Q3 - Q1`
  - Outliers: values < Q1 - 1.5×IQR or > Q3 + 1.5×IQR
- Found **425 outliers**, exported to `outliers.csv` for manual review.

**Manual Review & Action:**
- ✅ Retained genuine luxury properties after validation.
- ✂️ Dropped entries with:
  - Price typos (e.g., extra 0s or missing digits).
  - Invalid price-to-area ratios.
- 🛠 Corrected values based on domain logic and locality norms.

**📈 Result:** Cleaner and more realistic price distribution.

---

### 2. **Outlier Detection in `price_persqft`**

- This column was **highly right-skewed** due to:
  - Tiny properties with unusually high prices.
  - Large areas with low prices.

**Steps:**
- Boxplot and histogram analysis.
- Reapplied **IQR method**.
- Dropped:
  - Properties with **area > 1 lakh sqft**.
  - Extremely high `price_persqft` with no justification.

**Preserved:**
- Verified high-end listings in posh sectors.

**📈 Result:** Distribution normalized to reflect realistic per sqft prices.

---

### 3. **Area-to-Room Ratio Validation**

Used **architectural logic** to check:
- Does the area make sense for the number of rooms?
- Examples:
  - 700 sqft with 7 BHK → ✖️ (illogical for flats).
  - 700 sqft, 7 BHK, 4 floors → ✔️ (possible for a house).

**Steps:**
- Validated entries based on:
  - `property_type`: `House` vs `Flat`.
  - `floor_count`: Used to assess multi-story houses.
- Dropped:
  - Flats with very high room counts and tiny areas.
  - Entries with missing floor count and room mismatch.

**🏗️ Result:** Architecturally consistent dataset.

---

### 4. **Final Refinement**

- Revisited flagged records to ensure no genuine listings were removed.
- Carefully handled each row for:
  - Structural feasibility,
  - Market alignment,
  - Price and area justification.

**Kept:**
- Genuine outliers to retain real estate diversity.

**Removed:**
- All unverifiable or logically inconsistent entries.

---

## ✅ Outcome Summary

| Category              | Action Taken                       |
|----------------------|------------------------------------|
| `price`              | IQR method + manual correction     |
| `price_persqft`      | IQR method + logical filtering     |
| Area-to-Room Ratio   | Domain rule-based validation       |
| Total Rows Dropped   | ~400+ (after thorough analysis)    |
| Final Dataset        | Clean, consistent, and ML-ready    |

---

## 📁 Files & Artifacts

- `outliers.csv` – Contains the removed/flagged outlier rows for transparency.
- `outlier_analysis.ipynb` – Notebook with code, plots, and logic for detection.
- `cleaned_data.csv` – Final dataset post outlier removal.

---
---

# **🧩 Stage 6: Missing Value Imputation**

In this stage, missing values weren't just cleaned — they were understood. I leveraged **real-world relationships**, **logical imputation strategies** to impute values with confidence and maintain the integrity of the Gurgaon Real Estate dataset.

---

## 📉 Overview of Missing Data

| Feature                | Missing Values |
|------------------------|----------------|
| `balcony`              | 0              |
| `floorNum`             | 17             |
| `facing`               | 1,011          |
| `super_built_up_area`  | 1,680          |
| `built_up_area`        | 1,968          |
| `carpet_area`          | 1,715          |
| `agePossession`        | 0 (but 291 "Undefined") |

---

## 🧱 Imputing `built_up_area` – Based on 530 Valid Samples

### 🔍 Step 1: Ratio Derivation

From 530 rows where `carpet_area`, `built_up_area`, and `super_built_up_area` were all present, I derived realistic ratios:

| Ratio                                | Value   | Meaning                               |
|-------------------------------------|---------|---------------------------------------|
| carpet_area / built_up_area         | ≈ 0.90  | Carpet is ~90% of built-up area       |
| super_built_up_area / built_up_area | ≈ 1.105 | Super built-up is ~110.5% of built-up |

### 📐 Step 2: Smart Estimation Logic

| Available Columns       | Estimation Formula                                                                 |
|-------------------------|------------------------------------------------------------------------------------|
| Carpet + Super          | Average of (carpet_area / 0.9) and (super_built_up_area / 1.105)                   |
| Only Carpet             | built_up_area = carpet_area / 0.9                                                  |
| Only Super              | built_up_area = super_built_up_area / 1.105                                        |

🎯 **Result**: All 1,968 missing values were filled logically and confidently.

---

## 🏢 Imputing `floorNum` – Grouped by Context

The 17 missing values in `floorNum` were mainly from properties labeled as "House".

✅ **Strategy**:
- Grouped by `sector`, `property_type`, and room count.
- Used **median floor number** from similar groups.

🎯 Result: Imputed floor levels were contextually valid and realistic.

---

## 🏡 Handling `agePossession` – Replacing "Undefined"

Although not NaN, 291 rows had `"Undefined"` in `agePossession`.

✅ **Strategy**:
1. Grouped by `sector + property_type` → Imputed with mode.
2. If unavailable, used mode within `sector` only.
3. Assigned age categories like:
   - "Newly Constructed"
   - "Relatively New"
   - "Moderately Old"

🎯 Result: All 291 "Undefined" entries were replaced with meaningful labels.

---

## ✅ Final Outcome

| Feature           | Missing Before     | Missing After | Imputation Strategy                     |
|------------------|--------------------|----------------|------------------------------------------|
| `built_up_area`  | 1,968              | 0              | Ratio-based estimation using 530 rows   |
| `floorNum`       | 17                 | 0              | Median from location-type grouping      |
| `agePossession`  | 291 ("Undefined")  | 0              | Mode-based contextual replacement       |

---

## 🧠 Key Highlights

- ✅ Used **real-world data** over statistical assumptions
- ✅ Logic grounded in **domain understanding**
- ✅ Improved **data trustworthiness** for future modeling
- ✅ Inspired by 530 solid, complete examples

---
---


# **🧠 Stage 7: Feature Selection**

Feature selection is a vital part of the machine learning pipeline, helping models focus on the most informative inputs. In this stage, we took a **statistically and mathematically driven approach** to find and finalize the **most important features** influencing property prices in Gurgaon.

---

## 🚫 Step 1: Dropping Irrelevant Features

We dropped the following features before starting selection:

- `society`: Not useful for generalization or prediction.
- `price_per_sqft`: This could leak target information (data leakage), as it is derived from `price`.

---

## 🎯 Step 2: Creating User-Friendly Categorical Features

To enhance **interpretability** and **usability**, we transformed numerical features into categorical representations:

### ✅ Luxury Score → `luxury_category`

A score was generated based on various property attributes and categorized as:

```python
def categorize_luxury(score):
    if 0 <= score < 50:
        return "Low"
    elif 50 <= score < 150:
        return "Medium"
    elif 150 <= score <= 175:
        return "High"
    else:
        return None
```

---

### ✅ Floor Number → `floor_category`

The floor number was converted to floor type to enhance user understanding:

```python
def categorize_floor(floor):
    if 0 <= floor <= 2:
        return "Low Floor"
    elif 3 <= floor <= 10:
        return "Mid Floor"
    elif 11 <= floor <= 51:
        return "High Floor"
    else:
        return None
```

---

## 🧪 Step 3: Multi-Technique Feature Selection (The Main Act 🎬)

Instead of relying on a single method, we used **8 feature selection techniques**, treating each as an expert. The final selection was based on the **average importance across all techniques**.

### ✅ Techniques Used:

1. **Correlation Coefficient**
2. **Random Forest Feature Importance**
3. **Gradient Boosting Importance**
4. **Permutation Importance**
5. **Lasso Regression Coefficients**
6. **Recursive Feature Elimination (RFE)**
7. **Linear Regression Coefficients**
8. **SHAP (SHapley Additive exPlanations)**

---

## 📊 Feature Importance Table (Combined View)

| Feature          | Corr | RF    | GBoost | Perm | Lasso | RFE   | LinearReg | SHAP   |
|------------------|------|-------|--------|------|--------|--------|-----------|--------|
| sector           | -0.21 | 0.102 | 0.103  | 0.246 | -0.07 | 0.104  | -0.079    | 0.384  |
| bedRoom          | 0.59  | 0.024 | 0.038  | 0.041 | 0.014 | 0.028  | 0.017     | 0.050  |
| bathroom         | 0.61  | 0.026 | 0.036  | 0.035 | 0.275 | 0.024  | 0.282     | 0.113  |
| balcony          | 0.27  | 0.013 | 0.002  | 0.013 | -0.044| 0.012  | -0.066    | 0.040  |
| agePossession    | -0.13 | 0.015 | 0.004  | 0.013 | 0.000 | 0.014  | -0.002    | 0.027  |
| built_up_area    | 0.75  | 0.651 | 0.678  | 0.899 | 1.510 | 0.653  | 1.513     | 1.256  |
| study room       | 0.24  | 0.008 | 0.003  | 0.004 | 0.172 | 0.008  | 0.180     | 0.020  |
| servant room     | 0.39  | 0.019 | 0.023  | 0.040 | 0.161 | 0.018  | 0.170     | 0.096  |
| store room       | 0.31  | 0.008 | 0.010  | 0.004 | 0.200 | 0.008  | 0.204     | 0.017  |
| pooja room       | 0.32  | 0.006 | 0.000  | 0.003 | 0.074 | 0.005  | 0.077     | 0.012  |
| others           | -0.01 | 0.003 | 0.000  | 0.002 | -0.017| 0.003  | -0.025    | 0.007  |
| furnishing_type  | 0.23  | 0.011 | 0.003  | 0.010 | 0.164 | 0.010  | 0.173     | 0.027  |
| luxury_category  | 0.01  | 0.008 | 0.001  | 0.008 | 0.055 | 0.006  | 0.066     | 0.016  |
| floor_category   | 0.04  | 0.007 | 0.000  | 0.007 | -0.003| 0.006  | -0.013    | 0.025  |

---

## 🏁 Final Selected Features

After averaging and evaluating all 8 techniques, the following features were selected for the **final dataset**:

- `property_type`
- `sector`
- `bedRoom`
- `bathroom`
- `balcony`
- `agePossession`
- `built_up_area`
- `servant room`
- `store room`
- `furnishing_type`
- `luxury_category`
- `floor_category`
- `price` (Target)

---

## 📁 Output File

The final result was saved as:

**`gurgaon_properties_post_feature_selection.csv`**

### Sample Row:
```
property_type,sector,bedRoom,bathroom,balcony,agePossession,built_up_area,servant room,store room,furnishing_type,luxury_category,floor_category,price
0.0,36.0,3.0,2.0,2.0,1.0,850.0,0.0,0.0,0.0,1.0,1.0,0.82
```

---
---

# **🔍 Stage 8: Model Selection – [A] Building the Baseline Model**

This stage marks the **beginning of our modeling journey**. The goal was to establish a **baseline model**—a foundational benchmark to compare future, more complex models against.

Rather than aiming for perfection here, the focus was on:
- Getting the pipeline structure right ✅  
- Ensuring preprocessing is handled correctly 🔧  
- Achieving reasonably strong results without tuning 💪

And we did exactly that. Let’s walk through it.

---


## 🧼 Preprocessing Pipeline

To ensure fairness and consistency in model evaluation, I applied **careful preprocessing**:

### 🔹 1. One-Hot Encoding for Categorical Variables

Categorical features like:
- `sector`
- `furnishing_type`
- `luxury_category`
- `floor_category`

…were converted into numerical format using **One-Hot Encoding**, allowing the linear model to understand them without introducing bias from arbitrary numerical mapping.

---

### 🔹 2. Feature Scaling

Since Linear Regression is sensitive to feature magnitudes, **Standard Scaling** was applied to all relevant numerical features such as:
- Property type
- Bedroom, Bathroom counts
- Built-up Area
- Presence of servant/store rooms

This ensured all features contribute equally during model training.

---

### 🔹 3. Log Transformation on Target Variable

The target column, `price`, was **right-skewed**, meaning most properties had lower prices with a few very high outliers.

To normalize the distribution, a **log transformation** was applied. This helps stabilize variance and improves the linear model's ability to generalize.

---

## 🏗️ Model Construction

All preprocessing steps were integrated into a **single pipeline** along with the Linear Regression model. This made the workflow efficient, clean, and reproducible—ensuring that transformations were consistently applied across training and validation splits.

---

## 🔁 Model Evaluation – K-Fold Cross Validation

To validate the model fairly, I used **K-Fold Cross-Validation**:
- Ensures the model is evaluated on different parts of the data.
- Reduces overfitting on any one subset.
- Provides a reliable estimate of real-world performance.

---

## 📈 Performance Metrics

| Metric                  | Value                     |
|--------------------------|---------------------------|
| **R² Score (Mean)**       | **0.8845** ✅ Excellent     |
| **R² Score (Std Dev)**    | **0.0147** 🔁 Very Stable   |
| **Mean Absolute Error**   | **0.5324** 📉 Reasonable Error |

This performance is **impressive for a baseline** model — proving that the selected features and preprocessing strategy are strong even before introducing any model tuning or complexity.

---

## 📁 Notebook Reference

All work for this stage is saved in:

> 📘 **`baseline.ipynb`**

It contains:
- Preprocessing logic
- Pipeline definition
- Cross-validation & evaluation

---

## 🧠 Summary

> "You can’t improve what you don’t measure."

This baseline model gave us **clear measurement and direction**. With a score of `0.88+` out-of-the-box, it validated that our **feature selection**, **data cleaning**, and **transformation logic** from earlier stages were strong.


---
---


# **🧠 Stage 8: [B] Model Building and Hyperparameter Tuning**

This stage focuses on experimenting with different preprocessing techniques and regression models to identify the most accurate and robust model for price prediction. The entire process was designed to work within a unified pipeline architecture to maintain consistency and reproducibility across experiments.

---

### 🔄 Encoding Strategies Explored

To understand the impact of feature encoding on model performance, I tested **three types of encoding** on categorical features:

- **Ordinal Encoding**  
  Mapped categories to integers based on frequency and importance. Naturally suited for tree-based models.

- **One-Hot Encoding**  
  Applied selectively to columns with fewer unique values (`sector`, `agePossession`, `furnishing_type`). Although it increased dimensionality, it allowed testing model performance in a sparse representation scenario.

- **Target Encoding**  
  Encoded categories based on their relationship with the target variable, introducing a supervised context to the transformation.

Each encoding method was integrated into a full **preprocessing + regression pipeline**, evaluated across multiple models:

- Linear Regression
- Ridge & Lasso Regression
- SVR
- Decision Tree
- Random Forest
- Extra Trees
- Gradient Boosting
- AdaBoost
- MLPRegressor
- XGBoost

---

### 🔍 Comparative Results Summary

#### ✅ **Ordinal Encoding**
- **Top Models**: XGBoost (~0.891), Random Forest (~0.880)
- **MAE**: ~0.51 to 0.53
- **Mean R²**: 0.736, **Std**: 0.032  
- **Insight**: Performed best with tree-based models. Linear models struggled, especially Lasso which failed to converge effectively.

---

#### 🎯 **One-Hot Encoding**
- **Top Models**: XGBoost (~0.896), Random Forest (~0.891)
- **MAE**: ~0.46 to 0.50
- **Mean R²**: 0.062, **Std**: 0.019  
- **Insight**: Slight improvements in some models but not significant. Increased feature space added variance. Dimensionality reduction (e.g., PCA) didn’t help much and was discarded.

---

#### 🎯 **Target Encoding**
- **Top Models**: Extra Trees (0.902), Random Forest (0.900), XGBoost (0.900)
- **MAE**: ~0.45 to 0.48
- **Mean R²**: 0.829, **Std**: 0.018  
- **Insight**: Most consistent and highest-performing setup. Helped both linear and non-linear models without inflating dimensionality.

---

### ⚙️ Hyperparameter Tuning

After comparing models, **Random Forest Regressor** was selected for exhaustive tuning due to its strong baseline performance and general robustness.

#### ✅ GridSearchCV Tuning
- **Parameters Tuned**:
  - `n_estimators`
  - `max_depth`
  - `max_samples`
  - `max_features`
- **Search Space**: 1280 combinations × 10-fold CV = **12,800 model evaluations**
- **Time Taken**: Several hours  
- **Note**: Bayesian optimization (e.g., Hyperopt) for XGBoost was skipped due to time constraints.

---

### 📦 Final Model & Pipeline Storage

- **`pipeline.pkl`**: Contains the final trained pipeline including preprocessing + Random Forest model  
- **`df.pkl`**: Reference DataFrame to maintain column structure and categories – useful for inference and UI dropdown generation

---

### 🏁 Final Summary

| Aspect              | Value/Model                       |
|---------------------|----------------------------------|
| Best Encoding       | Target Encoding                  |
| Best Models         | Extra Trees / RF / XGBoost       |
| Final R² Score      | ~0.90                            |
| Final MAE           | ~0.45                            |
| Total Model Trials  | 1280 (via GridSearchCV)          |
| CV Strategy         | 10-fold                          |

This stage reflects a significant effort in **model tuning and experimentation**, ensuring that the final predictive system is **robust, reliable, and production-ready**.



## 🥳 Hurray! The Price Predictor is Live 🎉

After a long and enriching **8-stage journey**, I’ve successfully built a **robust and accurate property price predictor** for Gurugram apartments! This model combines the best of **feature engineering**, **model tuning**, and **smart encoding strategies** to provide realistic price estimations.

➡️ **Try it out now** on the deployed website:  
🔗 [https://houseing.onrender.com/](https://houseing.onrender.com/)  
💡 Enter basic apartment features and **get predicted prices instantly**!

---
---
---
---
## **🔮 Next Stage: The **Recommendation Module** (A Crazy Cool Build!)**

Let’s move into something even more powerful and interactive:  
### ✨ **Apartment Recommendation System**  
Yes, I built **not one**, but **three different recommendation engines** — all combined to suggest similar apartments with *your* preferences in control.

---

### 🏙️ Input Dataset

I used **247 Gurugram apartment listings**, each packed with rich features like:

- **Nearby Locations & Distances**  
  Example:  
  ```json
  {
    "AIPL Business Club Sector 62": "2.7 Km", 
    "Indira Gandhi International Airport": "21.1 Km", 
    "Golf Course Ext Rd": "99 Meter",
    ...
  }
  ```

- **Top Facilities**  
  Example:  
  ```json
  ["Swimming Pool", "Salon", "Restaurant", "Spa", "Cafeteria", "24x7 Security", "Club House", "Gated Community"]
  ```

From the complete dataset (`PropertyName`, `PropertySubName`, `NearbyLocations`, `LocationAdvantages`, `Link`, `PriceDetails`, `TopFacilities`), I selected 3 **core features** to power recommendations:

- 🧭 **Location Advantages**  
- 💰 **Price Details**  
- 🏢 **Top Facilities**

---

### 🧠 The 3 Pillars of Recommendation

To generate accurate suggestions, I designed **three separate recommendation models**, each focusing on one feature of similarity:

📦 These are visualized as a **flow of 3 boxes**:
1. **Location Advantage Model**
2. **Price Similarity Model**
3. **Facility Match Model**

Each model gives its own **similarity score**, and together they create a **hybrid recommendation score**.

---

## Here are the **ASCII-style** architecture diagram

        +---------------------+       +---------------------+       +---------------------+
        | Location Advantage  |       |     Price Details   |       |   Top Facilities    |
        +---------------------+       +---------------------+       +---------------------+
                  \                         |                         /
                   \                        |                        /
                    \                       |                       /
                     \                      |                      /
                      \                     |                     /
                       \                    |                    /
                        \                   |                   /
                         \                  |                  /
                          \                 |                 /
                           \                |                /
                            \               |               /
                             \              |              /
                              \             |             /
                               \            |            /
                                \           |           /
                                 \          |          /
                                  \         |         /
                                   \        |        /
                                +--------------------------------------+
                                |     Final Recommendation System      |
                                +--------------------------------------+
---
---

### 🔧 How the Engine Works

Here's the full recommendation workflow:

1. 🗺️ The user enters a **location** (e.g., *IGI Airport*) and a **radius**.
2. 📍 Apartments **within that radius** are filtered and displayed.
3. 🏠 The user selects **one apartment**.
4. 🤖 The system computes **similarity scores** from all 3 models.
5. ➕ These scores are **combined with weightage** to produce a final similarity score.
6. ✅ The top 5 apartments are returned as **personalized recommendations**!

---

### 🎚️ Why 3 Models Instead of 1?

The modular setup allows **customization of recommendation priorities**:

- Want to **prioritize facilities**? Increase the weight of the **Facility Match Model**.
- More concerned with **location proximity**? Give the **Location Model** more weight.

This flexibility puts **user preference in control** and enhances recommendation quality.

---

### 🛠️ Preprocessing & Regex Magic

To clean and use unstructured location data:

- I used **Regex** to extract and format location names and distances.
- The system now handles **~1070 unique location entries** (many messy due to spelling issues or abbreviations 😅).
- This preprocessing was essential to compute meaningful **location-wise proximity**.

---

### 🧾 Model Files for Website Integration

The backend is powered by:
- `cosine_sim_location.pkl`  
- `cosine_sim_price.pkl`  
- `cosine_sim_facilities.pkl`  
- `location_distance.pkl` (used to filter apartments by radius)

📊 The current weighted formula:
```python
cosine_sim_matrix = 0.5 * cosine_sim1 + 0.8 * cosine_sim2 + 1 * cosine_sim3
```

✅ In the future, this formula can be easily **adjusted to prioritize any feature**, giving users full control over recommendation behavior.

---

## 🚀 Summary

You can now:
- ✅ **Predict apartment prices** using a powerful ML model  
- ✅ **Get smart, personalized apartment recommendations**  
- ✅ **Control what matters most** — location, price, or facilities

🔗 **Live it in action**:  
🏡 [Try Recommendation + Prediction Tool](https://houseing.onrender.com/)

This is not just a tool—it's your **smartest assistant** for exploring homes in Gurugram! 💡🏘️

---
---
---
---

# 🧠 Real Estate Data Analytics & Visualization – Gurugram 🏙️

One of the most insightful and interactive modules of this project is **Data Analytics & Visualization**, which brings the Gurugram real estate dataset to life with clean, meaningful, and crazy-good plots! These visualizations uncover deep insights about locality trends, pricing patterns, and buyer preferences — all made easily understandable through visuals.

Below is a breakdown of the key visualizations and what they reveal:

---
## 🗺️ Geospatial Plot (Gurugram Property Map)

This plot visualizes the geographical distribution of property listings across Gurugram using **Folium**, an interactive mapping library in Python.

### 🔧 How It Works:
- I extracted unique sector names from the dataset.
- Automated Google search requests were made for each sector to fetch **latitude and longitude** from search result snippets.
- These coordinates were programmatically extracted and cleaned.
- Each sector was plotted as a **marker** on the Folium map.
- A **color gradient** was applied to indicate property prices:  
  - **Darker shades** → Higher prices (e.g., Sector 26, 25)  
  - **Lighter shades** → Lower prices (e.g., Manesar)

### 📌 Key Insights:
- Helps visualize premium vs. affordable localities across the city.
- Users can observe proximity to key infrastructure such as roads, metro lines, and commercial hubs.
- Facilitates intuitive understanding of spatial price trends for smarter property investment decisions.

### 📍 Example:
- Sector 26 appears with a dark-colored marker due to high average prices.
- Sector 104 or Manesar appears lighter, reflecting budget-friendliness.

---

## 📊 Area vs Price Scatter Plot

This scatter plot illustrates the relationship between **built-up area (in sq ft)** and **property price (in ₹)**.

### 🔧 How It Works:
- Data is plotted with area on the X-axis and price on the Y-axis.
- Each point is color-coded by **BHK (number of bedrooms)**.
- Outliers were removed to provide a more meaningful trend.

### 📌 Key Insights:
- A positive correlation: as area increases, price typically increases.
- Cluster of listings around 2-3 BHK with 1000–2000 sq ft range.
- Some luxury properties occupy high-price, high-area zones.

### 📍 Example:
- A 4BHK property with 5000+ sq ft shows up in the top-right corner with a price of ₹8Cr+.

---

## 🏠 BHK Distribution (Pie Chart)

This pie chart presents the distribution of properties based on **BHK configuration**.

### 🔧 How It Works:
- Counted the number of listings per BHK type.
- Generated a percentage pie chart using **Plotly**.

### 📌 Key Insights:
- 3 BHK properties dominate the listings (~43%).
- 2 BHK comes next (~25%), followed by 4 and 5 BHK.
- Highlights the market's inclination towards mid-sized family homes.

### 📍 Example:
- Buyers looking for 3 BHKs have the most options in Gurugram.

---

## 📦 Price Distribution by BHK (Box Plot)

This box plot compares **price ranges** across different **BHK categories**.

### 🔧 How It Works:
- BHK types on the X-axis, price (in ₹) on the Y-axis.
- Uses box plot to represent median, IQR, and outliers.

### 📌 Key Insights:
- Price variability increases with BHK count.
- 3 BHK median price ~₹1.6Cr, with a range of ₹35L to ₹13Cr.
- 5+ BHKs show significant outliers—luxury segment.

### 📍 Example:
- 2 BHKs show tight price range (~₹50L–₹1.5Cr), reflecting affordability.

---

## 🧱 Property Type Distribution (Histogram)

This plot distinguishes between **Flats** and **Independent Houses**.

### 🔧 How It Works:
- Count of properties by type is plotted.
- Overlaid with price histogram to see price ranges.

### 📌 Key Insights:
- Flats dominate property count.
- Houses are fewer but cover higher price brackets.
- Useful for understanding type-wise market segmentation.

### 📍 Example:
- Most high-end properties (₹10Cr+) are Houses, not Flats.

---

## ☁️ WordCloud of Common Features

A word cloud showing the most frequently mentioned **property features**.

### 🔧 How It Works:
- Parsed the `property_features` column.
- Tokenized words and counted frequency.
- Created visual using the **WordCloud** package.

### 📌 Key Insights:
- Popular features: **Vaastu Compliant, Gym, Water Storage, Lift, Fire Safety**.
- Tells us what's trending in buyer and seller priorities.

### 📍 Example:
- "Vaastu" stands out in almost every configuration, showing cultural importance.

---

## 🔥 Geospatial Price Heatmap

This heatmap illustrates **price per sq ft intensity** across Gurugram sectors.

### 🔧 How It Works:
- Aggregated psqft price by sector.
- Plotted using heatmap layer over latitude/longitude.
- Intensity represents pricing level.

### 📌 Key Insights:
- Central sectors like 25, 26, 27 show higher pricing.
- Outer regions like Manesar are relatively affordable.
- Aids quick visual comparison of hot vs cool zones.

### 📍 Example:
- Sector 48 lights up as a premium locality with prices over ₹20K psqft.

---

## 🔁 Sankey Chart (Property Type → Price Band)

This **Sankey diagram** shows the flow of **property types** into different **price bands**.

### 🔧 How It Works:
- Grouped data by property type and binned prices.
- Sankey nodes represent types and bands.
- Width of links shows count of properties in each flow.

### 📌 Key Insights:
- Most Flats fall into ₹50L–₹1Cr range.
- Houses dominate higher ranges like ₹1Cr–₹5Cr+.
- Excellent for mapping market behavior by type.

### 📍 Example:
- Nearly all ₹5Cr+ listings are Independent Houses.

---

## 📦 Price per Sqft by Sector (Box Plot)

This box plot compares **price per sq ft** across different **sectors**.

### 🔧 How It Works:
- Calculated psqft for each property.
- Grouped by sector and plotted box plots.

### 📌 Key Insights:
- Large spread in premium sectors like 48 and 25.
- Some sectors show consistency, indicating pricing stability.
- Useful to identify overpriced or undervalued localities.

### 📍 Example:
- Sector 48 has psqft prices ranging from ₹5.5K to ₹38K.

---

## 📈 Average Price by Sector (Bar Chart)

A bar chart highlighting the **average price** of listings across sectors.

### 🔧 How It Works:
- Grouped by sector and computed mean prices.
- Plotted using **Matplotlib** or **Seaborn**.

### 📌 Key Insights:
- Sector 26 has highest avg price (~₹31K psqft).
- Sector 37 and Manesar show affordable pricing.
- Easy way to pick top-performing or budget-friendly zones.

### 📍 Example:
- Average price in Sector 37 is almost 6x lower than Sector 26.

---

## 🧠 Feature Importance Plot (Model Explainability)

This bar chart shows the **importance of different features** in the model's price prediction.

### 🔧 How It Works:
- Used correlation or model-based importance scores.
- Plotted horizontal bar chart to rank features.

### 📌 Key Insights:
- **Built-up area** has strongest influence (corr ~0.67).
- Followed by sector, property type, and bathroom count.
- Helps understand what the model “cares about” most.

### 📍 Example:
- BHK count has moderate influence, furnishing has lesser.

---

## 🪑 Furnishing Type vs Average Price

This bar chart shows the **impact of furnishing type** on average property price.

### 🔧 How It Works:
- Grouped data by `furnishing` column.
- Calculated mean price for each furnishing type.

### 📌 Key Insights:
- Fully Furnished: avg ~₹3.9Cr  
- Semi-Furnished: avg ~₹3.3Cr  
- Unfurnished: avg ~₹2.1Cr
- Strong signal that better-furnished homes attract premium prices.

### 📍 Example:
- Going from Unfurnished to Fully Furnished can raise property value by ₹1.8Cr on average.

---
## 📌 Why It Matters?
These visualizations offer:
- 🎯 **Instant insights** on property pricing and trends.
- 📍 **Localized knowledge** to understand sector-specific values.
- 💼 **Better investment decisions** by comparing types, locations, and amenities.

Whether you're a **homebuyer**, **investor**, or a **real estate analyst**, this module is a powerful lens into Gurugram's real estate dynamics.