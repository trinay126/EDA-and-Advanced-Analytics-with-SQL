# SQL Data Analytics Project

## Executive Summary

This is my end-to-end SQL analytics project where I designed and executed a complete analysis workflow on sales data using SQL Server.

The project demonstrates how I:
- structure and load analytical datasets
- perform exploratory and KPI-driven analysis
- apply intermediate and advanced SQL techniques
- build reusable reporting views for business stakeholders

## Project Objective

The objective of this project is to transform raw sales, customer, and product data into actionable business insights.

I focused on answering practical analytics questions such as:
- What is the overall sales performance?
- Which products and customer segments contribute the most value?
- How does performance change over time?
- Which KPIs should be monitored in recurring reports?

## My Role

My responsibilities included:
- data loading and schema setup
- writing all SQL exploration and analysis scripts
- creating customer and product reporting views
- documenting assumptions, logic, and output structure

## Tech Stack

- SQL Server
- SQL Server Management Studio (SSMS)
- T-SQL

## Data Model

I used a star-schema style model under the `gold` schema:
- `gold.fact_sales` as the transaction table
- `gold.dim_customers` as customer dimension
- `gold.dim_products` as product dimension

## Repository Structure

```text
sql-data-analytics-project/
|-- datasets/
|   |-- DataWarehouseAnalytics.bak
|   `-- flat-files/
|       |-- dim_customers.csv
|       |-- dim_products.csv
|       `-- fact_sales.csv
|-- docs/
|   |-- Project Roadmap.png
|-- scripts/
|   |-- 00_init_database.sql
|   |-- 01_database_exploration.sql
|   |-- 02_dimensions_exploration.sql
|   |-- 03_date_range_exploration.sql
|   |-- 04_measures_exploration.sql
|   |-- 05_magnitude_analysis.sql
|   |-- 06_ranking_analysis.sql
|   |-- 07_change_over_time_analysis.sql
|   |-- 08_cumulative_analysis.sql
|   |-- 09_performance_analysis.sql
|   |-- 10_data_segmentation.sql
|   |-- 11_part_to_whole_analysis.sql
|   |-- 12_report_customers.sql
|   `-- 13_report_products.sql
|-- LICENSE
`-- README.md
```

## Project Workflow

I organized the analysis into 14 scripts, each solving a specific analytics stage:

1. `00_init_database.sql`: Database creation, schema creation, table creation, and data loading
2. `01_database_exploration.sql`: Metadata and table structure exploration
3. `02_dimensions_exploration.sql`: Dimension-level profiling
4. `03_date_range_exploration.sql`: Date coverage and temporal boundaries
5. `04_measures_exploration.sql`: Core KPIs and base metrics
6. `05_magnitude_analysis.sql`: Distribution analysis by category, country, and gender
7. `06_ranking_analysis.sql`: Top and bottom performer identification
8. `07_change_over_time_analysis.sql`: Time-series trend analysis
9. `08_cumulative_analysis.sql`: Running totals and moving averages
10. `09_performance_analysis.sql`: Year-over-year and period comparisons
11. `10_data_segmentation.sql`: Business segmentation with CASE logic
12. `11_part_to_whole_analysis.sql`: Contribution analysis as share of total
13. `12_report_customers.sql`: Customer report view creation
14. `13_report_products.sql`: Product report view creation

## Setup Instructions

1. Clone or download this repository.
2. Open SQL Server Management Studio and connect to your SQL Server instance.
3. Open `scripts/00_init_database.sql`.
4. Update all `BULK INSERT` source paths to your local absolute file paths.
5. Run `00_init_database.sql`.
6. Run scripts `01` to `13` in sequence.

## Important Implementation Note

The loader script uses hardcoded file paths that may not match your machine.

Repository CSV location:

```text
datasets/flat-files/dim_customers.csv
datasets/flat-files/dim_products.csv
datasets/flat-files/fact_sales.csv
```

Example of corrected path format:

```sql
BULK INSERT gold.dim_customers
FROM 'Y:\PROJECTS\sql-data-analytics-project\datasets\flat-files\dim_customers.csv'
WITH (
	FIRSTROW = 2,
	FIELDTERMINATOR = ',',
	TABLOCK
);
```

## Final Deliverables

The final analytical outputs are two reusable SQL views:
- `gold.report_customers`
- `gold.report_products`

Quick validation query:

```sql
SELECT TOP 10 * FROM gold.report_customers;
SELECT TOP 10 * FROM gold.report_products;
```

## Skills Demonstrated

This project highlights my ability to:
- write clean and modular SQL scripts
- use joins, CTEs, aggregate functions, and window functions
- design KPI and segmentation logic for reporting
- convert raw data into business-friendly insights
- document technical work in a professional format

## Future Enhancements

Planned next improvements:
- add data quality checks before loading
- parameterize file paths for portability
- include index and performance tuning notes
- publish dashboard layer on top of reporting views

## License
s
This project is licensed under the MIT License. See `LICENSE` for details.
