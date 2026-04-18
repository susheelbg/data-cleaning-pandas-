
import pandas as pd
import numpy as np

# Create a more complex messy DataFrame for the project
data = {
    'CustomerID': [101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 101, 111, 112, 113, 114, 115],
    'Name': ['Alice Smith', 'Bob Johnson', 'Charlie Brown', 'David Lee', 'Eve Davis', 'Frank White', 'Grace Green', 'Hannah Black', 'Ian Blue', 'JILL RAY', 'Alice Smith', 'Kevin P.', 'Liam Miller', 'Nora White', 'Olivia Green', 'Patrick Day'],
    'Email': ['alice@example.com', 'bob@example.com', 'charlie@example.com', 'david@example.com', 'eve@example.com', np.nan, 'grace@example.com', 'HANNAH@example.com', 'ian@example.com', 'jill@example.com', 'alice@example.com', 'kevin@example.com', 'liam@example.com', np.nan, 'olivia@example.com', 'patrick@example.com'],
    'Age': [25, 30, '35', 40, np.nan, 50, 28, 33, '42', 29, 25, 31, 36, 41, 26, 30],
    'Gender': ['Female', 'Male', 'Male', 'Male', 'Female', 'Male', 'Female', 'Female', 'Male', 'FEMALE', 'Female', 'Male', 'Male', 'Female', 'Female', 'Male'],
    'Subscription_Date': ['2023-01-15', '2023-02-20', '2023-03-10', '2023/04/05', '2023-05-01', '2023-06-12', np.nan, '2023-08-22', '2023-09-01', '2023-10-10', '2023-01-15', '2023-11-05', '2023-12-18', '2024-01-20', '2024-02-15', '2024-03-01'],
    'Annual_Income': [50000, 60000, 75000, 80000, '90000', 55000, 62000, np.nan, 70000, 65000, 50000, 72000, 85000, 92000, 58000, 68000],
    'Last_Purchase_Amount': [120.50, 85.20, 210.00, 50.10, np.nan, 150.00, 99.99, 300.00, 75.00, 180.00, 120.50, 110.00, 130.00, 250.00, 60.00, 100.00]
}

df_customers = pd.DataFrame(data)

print("Original Messy DataFrame:")
display(df_customers)
print("\nOriginal DataFrame Info:")
df_customers.info()
print("\nOriginal DataFrame Description:")
display(df_customers.describe(include='all'))

### 2. Handle Duplicate Records

Duplicate records can skew analysis. We'll identify and remove them, typically keeping the first occurrence.

print(f"Number of rows before removing duplicates: {len(df_customers)}")
df_cleaned_project = df_customers.drop_duplicates(subset='CustomerID', keep='first').copy()
print(f"Number of rows after removing duplicates based on CustomerID: {len(df_cleaned_project)}")
display(df_cleaned_project.head())

### 3. Correct Data Types

Many columns might be loaded as `object` (string) types when they should be numeric or datetime. We'll convert them to their appropriate types, handling errors where necessary.

# Convert 'Age' to numeric, coercing errors to NaN
df_cleaned_project['Age'] = pd.to_numeric(df_cleaned_project['Age'], errors='coerce')

# Convert 'Annual_Income' to numeric, coercing errors to NaN
df_cleaned_project['Annual_Income'] = pd.to_numeric(df_cleaned_project['Annual_Income'], errors='coerce')

# Convert 'Subscription_Date' to datetime, handling mixed formats
df_cleaned_project['Subscription_Date'] = pd.to_datetime(df_cleaned_project['Subscription_Date'], errors='coerce')

print("DataFrame Info after data type correction:")
df_cleaned_project.info()

### 4. Handle Missing Values

We'll address `NaN` values using different strategies:
*   **Age:** Fill with the median age.
*   **Email:** Drop rows where email is missing (critical contact info).
*   **Subscription_Date:** Drop rows where date is missing.
*   **Annual_Income:** Fill with the median income.
*   **Last_Purchase_Amount:** Fill with the mean purchase amount.

# Fill missing 'Age' with the median
df_cleaned_project['Age'].fillna(df_cleaned_project['Age'].median(), inplace=True)

# Fill missing 'Annual_Income' with the median
df_cleaned_project['Annual_Income'].fillna(df_cleaned_project['Annual_Income'].median(), inplace=True)

# Fill missing 'Last_Purchase_Amount' with the mean
df_cleaned_project['Last_Purchase_Amount'].fillna(df_cleaned_project['Last_Purchase_Amount'].mean(), inplace=True)

# Drop rows with missing 'Email' or 'Subscription_Date'
df_cleaned_project.dropna(subset=['Email', 'Subscription_Date'], inplace=True)

print("DataFrame after handling missing values:")
df_cleaned_project.info()

### 5. Standardize Text Data

For categorical columns like 'Name' and 'Gender', we'll standardize casing and remove extra whitespace to ensure consistency.

# Standardize 'Name' to title case and strip whitespace
df_cleaned_project['Name'] = df_cleaned_project['Name'].str.title().str.strip()

# Standardize 'Gender' to title case and strip whitespace
df_cleaned_project['Gender'] = df_cleaned_project['Gender'].str.title().str.strip()

# Standardize 'Email' to lowercase
df_cleaned_project['Email'] = df_cleaned_project['Email'].str.lower().str.strip()

print("DataFrame after standardizing text data (first 5 rows):")
display(df_cleaned_project.head())

### 6. Verify Cleaned Data

Let's check the info and unique values again to ensure our cleaning steps were effective.

print("Cleaned DataFrame Info:")
df_cleaned_project.info()
print("\nUnique Genders:", df_cleaned_project['Gender'].unique())
print("\nCleaned DataFrame Sample:")
display(df_cleaned_project.head(10))  wt happende here simply explain 
