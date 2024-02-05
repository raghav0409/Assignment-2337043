# Assignment-2337043
Abdul sir assignment

THE ASSIGNMENT USES THE INBUILT FDA_FOOD DATASET ON BIGQUERY

Question 1
Food Recalls by State:

SELECT state, COUNT(*) AS recall_count
FROM `bigquery-public-data.fda_food.food_enforcement`
WHERE status = 'On-Going'
GROUP BY state
ORDER BY recall_count DESC
LIMIT 5;

Question 2
Food Recalls by State:

SELECT 
  COUNT(*) AS total_recalls,
FROM `bigquery-public-data.fda_food.food_enforcement`;
https://drive.google.com/file/d/138EveMj60v8_gxGcTnP9XA2k8ERd1uZn/view?usp=sharing

Question 3
Recalls by Product Type:

SELECT product_type, COUNT(*) AS recall_count
FROM `bigquery-public-data.fda_food.food_enforcement`
GROUP BY product_type
ORDER BY recall_count DESC
LIMIT 10;

https://drive.google.com/file/d/1JFgB8bnFA76ibSd4Hf3sO0eNIFKxyiuM/view?usp=sharing

Question 4
Adverse Events by Product Brand:

SELECT products_brand_name, COUNT(*) AS event_count
FROM `bigquery-public-data.fda_food.food_events`
GROUP BY products_brand_name
ORDER BY event_count DESC
LIMIT 10;

https://drive.google.com/file/d/1dLYAg3Nb7kVF9xo1wFVfI3jhp2Ac-m7i/view?usp=sharing

Question 5
Consumer Age and Adverse Events:

SELECT consumer_age_unit, AVG(consumer_age), COUNT(*) AS event_count
FROM `bigquery-public-data.fda_food.food_events`
GROUP BY consumer_age_unit
ORDER BY consumer_age_unit;

https://drive.google.com/file/d/1TrAzHwswwS2SHGRC8ANAR-l3zbUtDJoa/view?usp=sharing

Question 6
Gender and Adverse Events:

SELECT consumer_gender, COUNT(*) AS event_count
FROM `bigquery-public-data.fda_food.food_events`
WHERE consumer_gender IN ('Male', 'Female')
GROUP BY consumer_gender;

https://drive.google.com/file/d/1WoRXahQYU5sDkOdniYxLyRXIlu3f21nY/view?usp=sharing

Question 7
Time Trend of Food Recalls:

SELECT EXTRACT(YEAR FROM date_created) AS year, COUNT(*) AS recall_count
FROM `bigquery-public-data.fda_food.food_enforcement`
GROUP BY year
ORDER BY year;

Question 8
Recalls and Adverse Events Connection:

SELECT fe.product_description, fe.code_info, fe.reason_for_recall,
       fev.reactions, fev.date_started
FROM `bigquery-public-data.fda_food.food_enforcement` fe
JOIN `bigquery-public-data.fda_food.food_events` fev ON fe.product_description = fev.products_brand_name
WHERE fe.reason_for_recall IS NOT NULL AND fev.reactions IS NOT NULL;

https://drive.google.com/file/d/1MjoJigQI32xcenKBvs34ajbddrz_rl7Z/view?usp=sharing

Question 9
Recalled Products Outside the US:

SELECT fe.product_description, fe.country, fe.state
FROM `bigquery-public-data.fda_food.food_enforcement` fe
WHERE fe.country <> 'US';

https://drive.google.com/file/d/1hQQS5Ukyw5FpEALgXgQ1uygm4JWKnYOl/view?usp=sharing

Question 10
Recalls with Missing Information:

SELECT fe.product_description, fe.reason_for_recall, fev.reactions
FROM `bigquery-public-data.fda_food.food_enforcement` fe
JOIN `bigquery-public-data.fda_food.food_events` fev ON fe.product_description = fev.products_brand_name
WHERE fe.reason_for_recall IS NOT NULL AND fev.reactions IS NOT NULL;

https://drive.google.com/file/d/1SimbtISKmEA2v6vGWng2GY5Fa6IxC-Rk/view?usp=sharing




