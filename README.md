# Pewlett Hackard Analysis
## Overview
Pewlett Hackard is anticipating an upcoming wave of retirements as Baby Boomers age out of their workforce, and are preparing some analyses of employee data to help them prepare for the positions that will need to be replaced as those retirements occur.  The initial analysis focused on identifying the current employees who will be eligible for retirement (see `retirement_info.csv`), and summarizing their number by department (see `dept_retirement.csv`). 

A secondary analysis was requested to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program.  This analysis will enable managers at Pewlett Hackard to develop and present a proposal for a mentoring program for employees getting ready to retire. Through this program, the employees who are close to retirement would step into a part-time role instead of retiring completely. Their new role in the company would be as a mentor to new hires in their areas of experience. 

## Results
The following observations are made in response to the two analyses delivered:
 
1. Reviewing the positions that the retirement-eligible employees currently hold (see `unique_titles.csv` and the summary `retiring_titles.csv`), we see that the largest impact will be to the Senior Engineer and Senior Staff positions.

  INSERT IMAGE retiring_titles.png
  
2. We can see that this is in-line with the fact that these positions are the most numerous in the company. This was determined by writing a query to identify the number of current employees by title:
  ```
  SELECT title, count(emp_no) as "No of employees" 
  FROM titles
  WHERE to_date = '9999-01-01'
  GROUP BY title
  ORDER BY "No of employees" DESC;
  ```

  which had these results:
  INSERT IMAGE current_employee_titles.png

In total, Pewlett Hackard needs to plan for between 25-30% of their workforce across all positions retiring in the 'silver tsunami'.

3. Looking only at current employees who were born in 1965 as the potential population for a mentorship program will provide the company with 1,549 potential mentors.  This was found by executing the query `SELECT count(*) FROM mentorship_eligibility;`

4. As shown in the results below, this population of potential mentors are working across all of the positions, except manager, where Pewlett Hackard will be experiencing retirement losses. These results were pulled by writing the below query:

  ```
  SELECT title, count(emp_no) as "number of mentors" 
  FROM mentorship_eligibility
  GROUP BY title
  ORDER BY "number of mentors" DESC;
  ```

  INSERT IMAGE mentor_titles.png

## Summary
In summary, Pewlett Hackard needs to plan for the retirement of 72,458 employees. 




  
