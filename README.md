# ev-charging-etl-pipeline

## Project Overview

This project focuses on analyzing EV charging session data to understand charging demand, station usage, and charging behavior.

The project covers the complete analytics process, starting with data extraction, cleaning, transformation, and feature engineering using PySpark. The processed data was then loaded into SQLite for SQL-based analysis and validation. Finally, Tableau was used to create a dashboard to present the main findings through interactive visualizations.

## Goals

The main goals of this project were to:

- Process and clean raw EV charging session data.
- Analyze charging demand across different times of the day.
- Identify the busiest charging stations.
- Compare stations based on total energy delivered.
- Understand the relationship between charging duration and energy delivered.
- Present the main findings through a Tableau dashboard.

## Methods Used

The raw JSON dataset was loaded and processed using PySpark. Since the data contained nested session records, the `_items` array was flattened into individual charging sessions. The data was checked for missing values and duplicate sessions, timestamps were converted into proper datetime fields, and charging and connection durations were calculated.

Additional features such as charging date, hour, day of week, and month were created to support time-based analysis. Invalid charging-duration values were handled without removing the complete sessions. PySpark was then used to create session-level and station-level analytical datasets.

The processed datasets were loaded into SQLite, where SQL queries were used to validate the data and analyze peak charging hours, busiest stations, and stations with the highest total energy delivered.

Finally, Tableau was used to create a dashboard containing:

- Total Sessions
- Average Session Duration
- Total Energy Delivered
- Active Stations
- Charging Demand Over Time
- Charging Demand by Hour
- Top 10 Stations by Session Count
- Charging Duration vs Energy Delivered

## Key Insights

The analysis was performed on **2,499 charging sessions across 52 stations**.

- The dataset recorded approximately **22,239 kWh** of total energy delivered.
- The average charging session duration was approximately **213 minutes**.
- **3 PM** was the busiest charging hour with **519 sessions**, followed by 4 PM with 331 sessions.
- Station **2-39-139-28** had the highest number of sessions with **107 sessions** and also delivered the highest total energy at approximately **1,031 kWh**.
- Station **2-39-91-437** had fewer sessions but a higher average energy delivered per session at approximately **13.8 kWh**.
- Charging duration and energy delivered showed an overall positive relationship, although the relationship varied considerably between individual sessions.

These findings highlight the differences in charging demand across time and stations and provide an overview of charging behavior within the analyzed dataset.

## Tools Used

- Python
- PySpark
- Pandas
- SQLite
- Tableau
- Jupyter Notebook
- Git & GitHub

## Project Files

- `acndata_sessions.json` - Original EV charging session dataset.
- `charging_sessions.csv` - Processed session-level dataset generated using PySpark.
- `station_summary.csv` - Station-level aggregated dataset generated using PySpark.
- `ev_charging.db` - SQLite database containing the processed datasets.
- `01_data_etl_using_pyspark.ipynb` - PySpark notebook containing data extraction, cleaning, transformation, feature engineering, and aggregation.
- `02_data_analysis_using_sql.ipynb` - SQL notebook containing database loading, validation, and analytical queries.
