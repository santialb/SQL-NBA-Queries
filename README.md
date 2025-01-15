# SQL NBA Analysis Project

## Overview
This project demonstrates fundamental SQL skills by analyzing NBA player data. The dataset includes attributes like player name, team, position, age, height, weight, and draft year. The analysis focuses on answering insightful questions using SQL queries.

## Goals
1. Showcase SQL skills by creating and running meaningful queries.
2. Gain insights into NBA player data through aggregation, filtering, and grouping.
3. Provide a foundation for future data visualization projects with tools like Tableau.

---

## Dataset
The dataset contains the following columns:
- `Player`: The name of the player.
- `Team`: The team the player is associated with.
- `Conference`: The player's conference (if applicable).
- `Position`: The player's position (e.g., PG, SF, etc.).
- `Age`: The player's age.
- `Height_CM`: Height of the player in centimeters.
- `Weight_KG`: Weight of the player in kilograms.
- `Draft_Year`: The year the player was drafted.
- `Seasons_in_League`: The number of seasons the player has played in the league.

---

## SQL Queries and Results

### 1. **Get the Average, Maximum, and Minimum Age of Players**
```sql
SELECT ROUND(AVG(age)) AS average_age, MAX(age) AS maximum_age, MIN(age) AS minimum_age 
FROM players;
```
- Purpose: To understand the age distribution of players in the league.
- Result: Outputs the average, oldest, and youngest player ages.
  

### 2. **Find Teams with Total Height Greater than 10,000 cm**
```sql
SELECT team, SUM(height_cm) AS total_team_height 
FROM players 
GROUP BY team 
HAVING total_team_height > 10000;
```
- Purpose: To identify teams with exceptionally tall players.
- Result: A list of teams whose combined player heights exceed 10,000 cm.


### 3. **Categorize Players by Age Groups**
```sql
SELECT COUNT(*) AS player_count, 
       CASE
           WHEN age > 30 THEN 'Old Player'
           WHEN age >= 27 THEN 'Prime Player'
           ELSE 'Young Player'
       END AS players_age_range
FROM players 
GROUP BY players_age_range;
```
- Purpose: To classify players into age groups: Young, Prime, and Old.
- Result: A count of players in each age category.


### 4. **List Players Drafted After 2015 Playing as PG or SF**
```sql
SELECT DISTINCT player, team, age, height, weight, position 
FROM players
WHERE draft_year > 2015 
  AND position IN ('PG', 'SF');
```
- Purpose: To find recently drafted point guards (PG) and small forwards (SF).
- Result: A unique list of players meeting the criteria.


### **Acknowledgments**
- Special thanks to the open-source community for inspiration and guidance.
- The dataset used for this project is from [Khan](https://www.khanacademy.org/) and designed for educational purposes.


### **Contact**
Feel free to reach out if you have any questions or suggestions:
- GitHub: santialb
- Email: sa_albarracin@hotmail.com
