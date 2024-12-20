# SQL Project - Data Cleaning

## Project Overview

This project focuses on cleaning a dataset of layoffs that occurred in 2022. The dataset is sourced from Kaggle. The goal is to clean the data, remove duplicates, fix errors, handle missing values, and perform exploratory data analysis (EDA).

The dataset includes information on various companies that laid off employees in 2022. The columns in the dataset contain details such as company name, location, industry, number of layoffs, percentage laid off, date of layoff, stage of layoffs, country, and funds raised.

The data cleaning process follows several steps:

1. *Remove Duplicates*: Identifying and removing duplicate rows to ensure the dataset contains unique entries.
2. *Standardize Data*: Fixing errors in column values and ensuring consistency (e.g., fixing the "industry" column for entries like 'Crypto Currency' to 'Crypto').
3. *Handle Null Values*: Checking for null values and deciding whether they should be kept or removed based on their significance.
4. *Remove Unnecessary Columns and Rows*: Dropping irrelevant columns and rows with missing critical data (e.g., rows where both total_laid_off and percentage_laid_off are null).
5. *Exploratory Data Analysis (EDA)*: Performing basic analysis to understand trends and insights from the cleaned dataset.

## Steps Taken

### 1. Remove Duplicates

- *Step 1*: The dataset is checked for duplicate rows, especially those where key columns like company, industry, total_laid_off, and date have identical values.
- *Step 2*: Duplicate entries are removed using the ROW_NUMBER() window function to partition the data by relevant columns and delete rows with a row_num > 1.

### 2. Standardize Data and Fix Errors

- *Industry Column*: Entries in the industry column were checked for inconsistencies (e.g., "Crypto Currency" was changed to "Crypto").
- *Country Column*: The country column was cleaned by removing trailing periods.
- *Date Column*: The date column was standardized by converting the string values to proper date format using STR_TO_DATE() and altering the column to a DATE type.

### 3. Handle Null Values

The project identified null values in several columns, including industry, total_laid_off, and `percentage_laid_off. These were handled by:
- Filling missing values where possible (e.g., using the industry from other rows with the same company).
- Removing rows with critical missing data like both total_laid_off and percentage_laid_off.

### 4. Remove Unnecessary Columns and Rows

- The row_num column was added for tracking duplicates and later removed once cleaning was completed.
- Rows with null values in total_laid_off and percentage_laid_off were deleted, as they didn't contribute to meaningful analysis.

### 5. Exploratory Data Analysis (EDA)

- *Top Layoffs by Company*: The number of layoffs by company was analyzed to find the companies with the highest layoffs.
- *Total Layoffs by Country*: Layoffs were aggregated by country to identify the countries with the highest total layoffs.
- *Layoffs by Industry*: The dataset was grouped by industry to understand which industries were most affected by layoffs.
- *Trends Over Time*: The number of layoffs over time was analyzed using the YEAR() and SUBSTRING() functions to observe patterns.

## Key Queries

- *Removing Duplicates*: Using ROW_NUMBER() to identify and delete duplicates.
- *Standardizing Columns*: UPDATE queries were used to standardize values in the industry and country columns.
- *Handling Nulls*: Identified and handled rows with null values in critical columns.
- *Aggregated Analysis*: Summed layoffs by company, location, country, and industry to find key trends.

## Conclusion

After completing the data cleaning steps, the dataset is now ready for further analysis. The cleaned dataset can be used to derive insights on trends in layoffs, the impact on different industries and countries, and how funds raised correlate with layoffs. This project serves as a solid foundation for any further exploratory data analysis or predictive modeling tasks.
