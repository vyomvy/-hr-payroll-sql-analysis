# HR & Payroll SQL Analysis

Self-designed relational database modeling a company's employees, departments, and order activity — built to practice the SQL patterns that come up most in real analyst interviews: joins, correlated subqueries, window functions, and date-based aggregation.

Every query was written and debugged by hand in MySQL Workbench, progressing from basic joins to running totals.

## Schema

Three related tables:

**departments** — `dept_id` (PK), `dept_name`, `location`

**employees** — `emp_id` (PK), `name`, `dept_id` (FK), `salary`, `joining_date`, `manager_id` (self-referencing FK)

**orders** — `order_id` (PK), `emp_id` (FK), `amount`, `order_date`, `status` (delivered / pending / cancelled)

## Queries

| # | Question | Concept |
|---|---|---|
| 1 | List employees with department & location, including those with no department | LEFT JOIN |
| 2 | Total salary and headcount per department, filtered to departments with 2+ employees | GROUP BY + HAVING |
| 3 | Highest-paid employee in each department | Subquery in FROM (MAX per group) |
| 4 | Each employee with their manager's name | SELF JOIN |
| 5 | Employees who joined in the last 5 years, with days worked | DATEDIFF + DATE_SUB |
| 6 | Total order amount per month for 2024 | MONTH() / YEAR() + GROUP BY |
| 7 | Departments with zero employees assigned | LEFT/RIGHT JOIN + NULL check |
| 8 | Gap in days between an employee's consecutive orders | LAG() + DATEDIFF (window function) |
| 9 | Employees who have only ever placed cancelled orders | Conditional aggregation (CASE + HAVING) |
| 10 | Running total of order amounts over time | SUM() OVER (ORDER BY) |

## Files

```
hr-payroll-sql-analysis/
├── README.md
├── dataset/
│   └── practice_sql.sql        — schema + sample data
└── solutions/
    ├── q1_left_join.sql
    ├── q2_groupby_having.sql
    ├── q3_max_per_group.sql
    ├── q4_self_join.sql
    ├── q5_date_filter.sql
    ├── q6_date_groupby.sql
    ├── q7_left_join_null.sql
    ├── q8_lag_date_gap.sql
    ├── q9_multi_join_filter.sql
    └── q10_running_total.sql
```

## Tools

MySQL · MySQL Workbench

---

**Author:** [vyomvy](https://github.com/vyomvy) · [LinkedIn](https://www.linkedin.com/in/sant-sahu-738063319/)
