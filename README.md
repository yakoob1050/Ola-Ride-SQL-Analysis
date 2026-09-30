🚖 OLA Ride SQL Data Analysis
📌 Project Overview

This project analyzes OLA ride booking data using SQL to extract useful insights related to bookings, customers, vehicles, cancellations, ratings, and revenue.

The project contains SQL queries designed to answer real-world business questions using a ride-booking dataset.

🛠️ Technologies Used
PostgreSQL
SQL
CSV Dataset
pgAdmin / PostgreSQL environment
📂 Dataset

The project uses an OLA ride dataset containing ride and booking-related information.

Key fields used in the analysis include:

Booking ID
Customer ID
Booking Status
Vehicle Type
Ride Distance
Booking Value
Driver Ratings
Customer Rating
Cancellation Reasons
Incomplete Ride Information
📊 SQL Analysis Performed
1. Retrieve Successful Bookings

Identified all rides where the booking status was Success.

SELECT *
FROM ride_data
WHERE booking_status = 'Success';
2. Average Ride Distance by Vehicle Type

Calculated the average ride distance for each vehicle type.

SELECT
    Vehicle_Type,
    ROUND(AVG(Ride_Distance)::numeric, 2) AS Avg_Distance
FROM ride_data
GROUP BY Vehicle_Type;
3. Customer-Cancelled Rides

Calculated the total number of rides cancelled by customers.

SELECT COUNT(*)
FROM ride_data
WHERE Booking_Status = 'Cancelled by Customer';
4. Top 5 Customers by Number of Rides

Identified the five customers who booked the highest number of rides.

SELECT
    Customer_ID,
    COUNT(Booking_ID) AS Total_Rides
FROM ride_data
GROUP BY Customer_ID
ORDER BY Total_Rides DESC
LIMIT 5;
5. Driver Cancellations

Calculated rides cancelled by drivers because of personal and car-related issues.

SELECT COUNT(*)
FROM ride_data
WHERE Reason_for_Cancelling_by_Driver =
      'Personal & Car related issues';
6. Driver Ratings for Prime Sedan

Found the maximum and minimum driver ratings for Prime Sedan bookings.

SELECT
    MAX(Driver_Ratings) AS Max_Rating,
    MIN(Driver_Ratings) AS Min_Rating
FROM ride_data
WHERE Vehicle_Type = 'Prime Sedan'
  AND Driver_Ratings IS NOT NULL;
7. Average Customer Rating by Vehicle Type

Calculated average customer ratings for each vehicle type.

SELECT
    Vehicle_Type,
    ROUND(AVG(Customer_Rating)::numeric, 2)
        AS Avg_Customer_Rating
FROM ride_data
WHERE Customer_Rating IS NOT NULL
GROUP BY Vehicle_Type;
8. Total Booking Value

Calculated the total booking value of successfully completed rides.

SELECT
    ROUND(SUM(Booking_Value)::numeric, 2)
        AS Total_Booking_Value
FROM ride_data
WHERE Booking_Status = 'Success';
9. Incomplete Rides

Retrieved incomplete rides along with their reasons.

SELECT
    Booking_ID,
    Incomplete_Rides_Reason
FROM ride_data
WHERE Incomplete_Rides = '1';

The project source contains these booking, distance, cancellation, customer, rating, booking-value, and incomplete-ride analyses.

🧠 SQL Concepts Used
SELECT
WHERE
GROUP BY
ORDER BY
LIMIT
COUNT()
SUM()
AVG()
MAX()
MIN()
ROUND()
NULL handling
Filtering
Aggregation
Business-oriented SQL analysis
📁 Project Structure
Ola-Ride-SQL-Analysis/
│
├── README.md
│
├── sql/
│   └── ola_ride_analysis.sql
│
├── data/
│   └── ola_ride.csv
│
└── docs/
    ├── Ola_Ride_SQL_Project.pdf
    ├── Ola_Ride_SQL_Project.pptx
    └── Ola_Ride_SQL_Questions.docx
🎯 Key Skills Demonstrated
SQL Query Development
PostgreSQL
Data Analysis
Data Filtering
Aggregation
Customer Analysis
Ride Analysis
Vehicle Analysis
Cancellation Analysis
Rating Analysis
Business Problem Solving
