### Account Receivable (AR) Aging Report
This project involves calculating and categorizing AR aging and visualizing it into charts. It helps in identifying overdue payments and assessing the financial health of the company.

### Project Overview
This project demonstrates how to create an AR aging report using Excel. The report categorizes outstanding invoices based on their due dates and visualize it. 

📌 Tools used: Microsoft Excel

📌 Skills demonstrated: IF functions, VLOOKUP, pivot tables, data visualization with charts

### 🎯 Objectives
- Calculate AR aging based on invoice due dates
- Categorize outstanding invoices into aging buckets (e.g., not due, 1-30 days, 31-60 days, etc.)
- Visualize the AR aging distribution using charts
- Identify overdue payments and assess the financial health of the company

---

The original dataset contains 5 columns with the following features:
AR_id, Customers name, Invoice date, Due date, Amount.

### Steps:
1. **Calculate Due Date**: Ensure that the due date column is in date format. Then, use formula to calculate the due date based on the invoice date and payment terms (in this case 30): `=WORKDAY(AR_age_category!$C2;$J$1)`

I used the `WORKDAY` function to calculate the due date, which excludes weekends and holidays.

<img src="screenshots/due-date.png" width="" alt="Dashboard">


2. **Calculate Past Due Days**: Create a new column to calculate the number of days past due using the formula: `=IF([@[due_date]]>=TODAY();0;NETWORKDAYS([@[due_date]];TODAY()))`

I used the `NETWORKDAYS` function to calculate the number of working days past due, which excludes weekends and holidays.

<img src="screenshots/past-due-days.png" width="" alt="Dashboard">

3. **Create AR aging buckets table**: Create a new table to categorize the past due days into aging buckets.

<img src="screenshots/aging-bucket-table.png" width="" alt="Dashboard">

4. **Categorize AR aging**: Use the `VLOOKUP` function to categorize the past due days into aging buckets based on the table created in step 3: `=VLOOKUP(AR_age_category!$F2;aging_bucket[#All];2)`

<img src="screenshots/aging-category.png" width="" alt="Dashboard">

5. **Create Pivot Table**: Create a pivot table to summarize the total amount in each aging bucket.

<img src="screenshots/pivot-table.png" width="" alt="Dashboard">

6. **Visualize AR aging distribution**: Create a chart.

In this case I chose a stacked chart and slicer to filter by customer name and aging category.

<img src="screenshots/AR-chart.png" width="" alt="Dashboard">

7. **Create Dashboard**: Arrange the pivot table, chart, and slicer in a dashboard layout for easy analysis.

 <img src="screenshots/AR-dashboard.png" width="" alt="Dashboard">



### Insights:
- The majority of outstanding invoices are in the >90 days past due category, indicating a significant issue with overdue payments.
- All customers have invoices in the >90 days past due category, suggesting a widespread issue with payment delays.
- The company should take action to address these overdue payments and improve its accounts receivable management to enhance cash flow and financial health.
- By regularly monitoring the AR aging report, the company can identify trends in payment delays and take proactive measures to mitigate risks associated with overdue payments.

### Conclusion:
The AR aging report provides valuable insights into the company's accounts receivable management and helps identify areas for improvement. By categorizing outstanding invoices into aging buckets and visualizing the distribution, the company can better understand its cash flow situation and take necessary actions to address overdue payments. Regularly monitoring the AR aging report is essential for maintaining financial health and ensuring timely collections from customers.

### Future Improvements:
- Implementing automated reminders for customers with overdue invoices to encourage timely payments.
- Conducting credit risk assessments for customers to identify potential risks of non-payment and adjust credit terms accordingly.
- Implementing stricter credit policies, offering incentives for early payments, or improving communication with customers regarding payment terms and due dates.
- Analyzing the reasons for payment delays and addressing any underlying issues with customers or internal processes.
