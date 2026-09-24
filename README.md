# 🚦 Road Traffic Accident (RTA) Analysis

## 📌 Project Overview

This project analyzes **Road Traffic Accident (RTA)** data using Python and Jupyter Notebook to explore accident patterns, severity, driver characteristics, road conditions, weather, accident causes, and time-based trends.

The project follows a complete data-analysis workflow:

**Data Loading → Data Exploration → Data Cleaning → Feature Engineering → Exploratory Data Analysis → Visualization → Insights**

The analysis is performed on a dataset containing **12,316 accident records and 32 original columns**. Additional features such as `Hour` and `Time_period` are created during the analysis.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Understand the structure and characteristics of the RTA dataset.
* Identify and handle missing values.
* Check for duplicate records.
* Analyze accident severity.
* Identify the most common causes of accidents.
* Analyze accidents by day and hour.
* Examine driver age, gender, and driving experience.
* Explore the relationship between driver characteristics and accident severity.
* Analyze weather and road-surface conditions.
* Create visualizations to communicate important patterns and findings.

---

## 🛠️ Tools & Technologies

| Tool / Library      | Purpose                        |
| ------------------- | ------------------------------ |
| 🐍 Python           | Data analysis and processing   |
| 📓 Jupyter Notebook | Analysis environment           |
| 🐼 Pandas           | Data manipulation and cleaning |
| 🔢 NumPy            | Numerical operations           |
| 📊 Matplotlib       | Data visualization             |
| 📈 Seaborn          | Statistical visualization      |

---

## 📂 Project Structure

```text
RTA-Accident-Analysis/
│
├── RTA-Accident-Analysis.ipynb
├── RTA-Cleaned-Dataset.xlsx
└── README.md
```

## 📊 Dataset Overview

The original dataset contains:

* **12,316 records**
* **32 columns**
* **30 categorical/object columns**
* **2 numerical columns**

The dataset includes information related to:

### 👤 Driver Information

* Driver age group
* Driver gender
* Educational level
* Driving experience
* Vehicle-driver relationship
* Vehicle type
* Vehicle ownership
* Vehicle service year

### 🛣️ Road & Environment

* Accident area
* Lanes/medians
* Road alignment
* Junction type
* Road surface type
* Road surface conditions
* Light conditions
* Weather conditions

### 🚗 Accident Information

* Type of collision
* Number of vehicles involved
* Number of casualties
* Vehicle movement
* Cause of accident
* Accident severity

### 🚶 Casualty Information

* Casualty class
* Casualty gender
* Casualty age group
* Casualty severity
* Work of casualty
* Fitness of casualty
* Pedestrian movement

---

## 🧹 Data Cleaning

The notebook performs several data-quality checks and cleaning operations.

### Missing Values

Missing values were identified across the dataset before cleaning.

The notebook then applies:

* **Median imputation** for integer/numerical columns.
* **`Unknown`** for missing categorical values.

After the cleaning process, the notebook verifies that the dataset contains **0 missing values**.

### Duplicate Records

Duplicate records were checked using:

```python
df.duplicated().sum()
```

The analysis found:

**0 duplicate rows.**

### Data Type Handling

Categorical columns were handled as object-type data, while numerical variables such as:

* `Number_of_vehicles_involved`
* `Number_of_casualties`

were retained as numerical fields.

---

## ⚙️ Feature Engineering

Two new features were created from the `Time` column.

### ⏰ Hour

The accident time was converted into an hourly value:

```python
df["Hour"] = df["Time"].apply(lambda x: x.hour)
```

This allowed accident frequency to be analyzed by hour.

### 🕐 Time Period

The `Hour` variable was further grouped into four periods:
Time Period      Hours       
Morning        05:00–11:59 
Afternoon      12:00–16:59 
Evening        17:00–20:59 
Night          21:00–04:59 

The resulting distribution was:

 Time Period    Accidents 
 Afternoon        3,897 
 Evening          3,496 
 Morning          3,312 
 Night            1,611 

---

# 📈 Exploratory Data Analysis

## 🚨 Accident Severity

The dataset contains three accident-severity categories:

Accident Severity   Count 
Slight Injury      10,415 
Serious Injury     1,743
Fatal injury        158 

Slight Injury represents the largest category in the dataset.

The notebook visualizes accident severity using a count plot.

---

## ⚠️ Top Causes of Accidents

The five most frequently recorded causes were:

| Rank | Cause                      | Accidents |
| ---- | -------------------------- | --------: |
| 1    | No distancing              |     2,263 |
| 2    | Changing lane to the right |     1,808 |
| 3    | Changing lane to the left  |     1,473 |
| 4    | Driving carelessly         |     1,402 |
| 5    | No priority to vehicle     |     1,207 |

These categories were further compared with accident severity using cross-tabulation and stacked bar visualization.

---

## 🌦️ Weather Conditions

The analysis shows the following accident distribution by weather condition:

| Weather Condition | Accidents |
| ----------------- | --------: |
| Normal            |    10,063 |
| Raining           |     1,331 |
| Other             |       296 |
| Unknown           |       292 |
| Cloudy            |       125 |
| Windy             |        98 |
| Snow              |        61 |
| Raining and Windy |        40 |
| Fog or mist       |        10 |

The notebook also examines weather conditions together with road-surface conditions and accident severity.

---

## 📅 Accidents by Day of Week

The distribution of accidents across the week is:

| Day       | Accidents |
| --------- | --------: |
| Friday    |     2,041 |
| Thursday  |     1,851 |
| Wednesday |     1,840 |
| Tuesday   |     1,770 |
| Monday    |     1,681 |
| Saturday  |     1,666 |
| Sunday    |     1,467 |

The notebook visualizes this distribution using a day-of-week count plot.

---

## ⏰ Accidents by Hour

The analysis identifies the following hours among the highest accident counts:

|  Hour | Accidents |
| ----: | --------: |
| 17:00 |     1,228 |
| 18:00 |       956 |
| 16:00 |       921 |
| 15:00 |       874 |
| 08:00 |       828 |
| 13:00 |       772 |
| 19:00 |       708 |
| 12:00 |       691 |
| 14:00 |       639 |
| 20:00 |       604 |

A line chart is used to visualize accident frequency by hour.

---

# 👤 Driver Analysis

## Age Group

The driver-age distribution is:

| Age Group | Accidents |
| --------- | --------: |
| 18–30     |     4,271 |
| 31–50     |     4,087 |
| Over 51   |     1,585 |
| Unknown   |     1,548 |
| Under 18  |       825 |

The notebook also compares driver age groups with accident severity.

---

## 👥 Driver Gender

The dataset contains:

| Driver Gender | Accidents |
| ------------- | --------: |
| Male          |    11,437 |
| Female        |       701 |
| Unknown       |       178 |

A count plot is used to visualize accident records by driver gender.

---

## 🚘 Driving Experience

The distribution of driving experience is:

| Driving Experience | Accidents |
| ------------------ | --------: |
| 5–10 years         |     3,363 |
| 2–5 years          |     2,613 |
| Above 10 years     |     2,262 |
| 1–2 years          |     1,756 |
| Below 1 year       |     1,342 |
| Unknown            |       829 |
| No Licence         |       118 |
| unknown            |        33 |

Driving experience is also compared with accident severity using a cross-tabulation.

---

# 🔍 Severity Analysis

The notebook examines accident severity across different driver age groups.

For example, the 18–30 age group contains:

* **3,605** Slight Injury cases
* **604** Serious Injury cases
* **62** Fatal Injury cases

The 31–50 age group contains:

* **3,492** Slight Injury cases
* **541** Serious Injury cases
* **54** Fatal Injury cases

The analysis also examines the interaction between **driver age group, driving experience, and accident severity**.

---

# 🌧️ Weather & Road Conditions

A cross-tabulation was created between:

* Weather conditions
* Road-surface conditions
* Accident severity

This allows the analysis to examine accident severity across combinations such as:

* Normal weather + Dry road
* Normal weather + Wet/Damp road
* Raining + Wet/Damp road
* Cloudy + Dry road
* Snow + Snow-covered road

The notebook uses these combinations to explore how environmental conditions relate to recorded accident severity.

---

# 🗺️ Day & Hour Analysis

A day-versus-hour cross-tabulation was created to examine when accidents occur throughout the week.

The analysis includes all seven days and all 24 hours, allowing patterns such as higher accident counts during specific weekday/time combinations to be explored.

A heatmap is used to visualize this relationship.

---

# 📊 Visualizations

The notebook includes several visualizations, including:

* Accident severity count plot
* Top accident causes
* Weather-condition distribution
* Accidents by day of week
* Accidents by hour
* Driver age-group distribution
* Driver gender distribution
* Driving-experience distribution
* Driver age group vs. accident severity
* Top accident causes vs. accident severity
* Day vs. hour accident heatmap
* Weather and road-condition severity analysis

---

# 💡 Key Findings

Based on the analysis performed in the notebook:

* **12,316 accident records** were analyzed.
* **Slight Injury** is the most frequently recorded accident severity, with **10,415 cases**.
* **No distancing** is the most common recorded cause of accidents, with **2,263 cases**.
* **Friday** has the highest number of recorded accidents among the days of the week, with **2,041 cases**.
* **17:00** has the highest hourly accident count in the analysis, with **1,228 cases**.
* The **18–30** driver age group has the highest number of accident records, with **4,271 cases**.
* Male drivers account for **11,437** accident records in the dataset.
* **Normal weather conditions** account for the largest number of accident records, with **10,063 cases**.
* The analysis found **0 duplicate rows**.
* After the cleaning process, the notebook reports **0 remaining missing values**.
* Accident patterns were further examined across driver characteristics, causes, weather, road conditions, day, and time.

> These findings describe patterns in the analyzed dataset and should not be interpreted as causal relationships.

---

# 🚀 How to Use This Project

### 1. Clone or download the repository

```bash
git clone https://github.com/rohitbachan/RTA-Accident-Analysis.git
```

### 2. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### 3. Open the notebook

```bash
jupyter notebook
```

Then open:

```text
RTA-Accident-Analysis.ipynb
```

### 4. Run the notebook

Run the cells sequentially to reproduce the data cleaning, feature engineering, analysis, and visualizations.

---

# 📁 Repository Files

 File                                 Description                                 
 `RTA-Accident-Analysis.ipynb`    Complete Python analysis and visualizations 
 `RTA-Cleaned-Dataset.xlsx`       Cleaned dataset                             
 `README.md`                      Project documentation                       

---

# 👨‍💻 Author

**Rohit Bachan Prasad**

Aspiring Data Analyst

**Skills:** Python • SQL • Power BI • Excel • Data Analytics

---

## ⭐ Project Highlights

This project demonstrates practical experience in:

* Data Cleaning
* Exploratory Data Analysis
* Feature Engineering
* Data Visualization
* Categorical Data Analysis
* Cross-tabulation
* Time-based Analysis
* Accident Severity Analysis
* Python for Data Analytics

Author
Rohit Bachan Prasad

Aspiring Data Analyst
Python | SQL | Power BI | Excel | Data Analytics
