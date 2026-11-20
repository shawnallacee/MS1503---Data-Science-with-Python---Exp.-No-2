# Experiment 2 : Customer Data Exploration Using Pandas

## Aim
To create a sample customer dataset and perform data exploration, filtering, sorting, grouping, and basic statistical analytics using Pandas functions in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data manipulation and analysis.
3. **Initialize Dataset**: Create a Python dictionary `data` containing customer attributes (`Customer_ID`, `Customer_Name`, `Region`, `Age`, `Annual_Income`, `Spending_Score`, `Loyalty_Years`).
4. **Construct DataFrame**: Convert the dictionary into a structured Pandas DataFrame `df` using `pd.DataFrame(data)` and print the dataset.
5. **Inspect Structure & Summary**:
   * Display dataset dimensions (`df.shape`), column names (`df.columns`), data types and null counts (`df.info()`), and descriptive statistics (`df.describe()`).
   * Display the first 3 records (`df.head(3)`) and last 3 records (`df.tail(3)`).
6. **Sort & Filter Records**:
   * Sort customers in descending order of `Annual_Income` using `df.sort_values()`.
   * Filter high-income customers where `Annual_Income > 70000`.
7. **Perform Group-Wise & Frequency Analysis**:
   * Group customers by `Region` and calculate regional averages for `Annual_Income` and `Spending_Score` using `df.groupby().mean()`.
   * Count customer distribution across each region using `df["Region"].value_counts()`.
8. **Compute Overall Metrics & Top Performer**:
   * Identify the customer record with the highest `Spending_Score` using `df["Spending_Score"].idxmax()` and `df.loc[]`.
   * Calculate overall mean `Annual_Income` and mean `Spending_Score`.
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation** | `pd.DataFrame()` | Converts a Python dictionary into a 2D labeled tabular DataFrame |
| **Structural Inspection** | `df.shape`, `df.columns` | Retrieves dimensions `(rows, columns)` and column labels |
| | `df.info()`, `df.describe()` | Summarizes column data types, memory usage, and descriptive statistics |
| | `df.head(n)`, `df.tail(n)` | Views the first `n` and last `n` rows of the dataset |
| **Sorting & Filtering** | `df.sort_values()` | Orders records by `Annual_Income` in descending order |
| | Boolean Indexing (`df[...]`) | Filters customers with `Annual_Income > 70000` |
| **Grouping & Aggregation** | `df.groupby().mean()` | Aggregates mean income and spending score per `Region` |
| | `df["Region"].value_counts()` | Counts occurrences of customers in each region |
| | `idxmax()`, `df.loc[]`, `.mean()` | Locates the top spender row and computes dataset-wide averages |

## Program
import pandas as pd  

# Customer Data Exploration using Pandas  
 
# Step 1: Create a sample customer dataset  
data = {  
    "Customer_ID": [101, 102, 103, 104, 105, 106, 107, 108],  
    "Customer_Name": [  
        "Ananya Sharma",  
        "Rohan Verma",  
        "Priya Nair",  
        "Karthik Iyer",  
        "Meera Krishnan",  
        "Arjun Mehta",  
        "Divya Menon",  
        "Vikram Rao",  
    ],            
    "Region": [    
        "South",  
        "North",  
        "South",  
        "South",  
        "West",  
        "North",  
        "West",  
        "East",  
    ],  
    "Age": [28, 35, 24, 42, 31, 46, 29, 38],  
    "Annual_Income": [65000, 82000, 52000, 95000, 74000, 88000, 61000, 71000],  
    "Spending_Score": [78, 64, 85, 58, 91, 52, 73, 69],  
    "Loyalty_Years": [3, 6, 2, 8, 5, 9, 4, 5],  
}  

# Step 2: Convert to a Pandas DataFrame  
df = pd.DataFrame(data)  
print("--- Full Customer Dataset ---")  
print(df)  

# Step 3: Basic exploration  
print("\n--- Shape ---")  
print(df.shape)  

print("\n--- Columns ---")  
print(df.columns)  

print("\n--- DataFrame Info ---")  
df.info()  

print("\n--- Descriptive Statistics ---")  
print(df.describe())  

# Step 4: Display first and last few records  
print("\n--- First 3 Records ---")  
print(df.head(3))  

print("\n--- Last 3 Records ---")  
print(df.tail(3))  
  
# Step 5: Sort customers by Annual Income (descending)  
sorted_by_income = df.sort_values(by="Annual_Income", ascending=False)  
print("\n--- Customers Sorted by Annual Income (Descending) ---")  
print(sorted_by_income)  

# Step 6: Filter high-income customers (Income > 70000)  
high_income_customers = df[df["Annual_Income"] > 70000]          
print("\n--- High-Income Customers (Annual_Income > 70000) ---")    
print(high_income_customers)  

# Step 7: Group customers by Region and find average Income and Spending Score          
regional_averages = df.groupby("Region")[["Annual_Income", "Spending_Score"]].mean()    
print("\n--- Regional Average Income and Spending Score ---")  
print(regional_averages)  

# Step 8: Count number of customers in each Region  
region_counts = df["Region"].value_counts()    
print("\n--- Customer Count per Region ---")    
print(region_counts)    

# Step 9: Identify customer with maximum Spending Score  
top_spender_idx = df["Spending_Score"].idxmax()  
top_spender = df.loc[top_spender_idx]  
print("\n--- Customer with Maximum Spending Score ---")  
print(top_spender)  

# Step 10: Compute overall averages  
overall_avg_income = df["Annual_Income"].mean()    
overall_avg_spending = df["Spending_Score"].mean()  
print("\n--- Overall Averages ---")  
print(f"Average Annual Income: {overall_avg_income:.2f}")      
print(f"Average Spending Score: {overall_avg_spending:.2f}")  


## Output

## Result
The program successfully creates a customer dataset using Pandas and performs exploratory analysis, sorting, filtering, regional grouping, and summary statistics.
