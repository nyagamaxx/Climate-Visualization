# Climate Visualization Project

## Overview

This is a full-stack Climate Visualization project built with **Flask (Python)**, **MySQL**, and a **React frontend**. The project allows users to view climate data, upload datasets, and explore summary statistics.

---

## Features

* Fetch climate data filtered by country, region, and year range.
* View summary statistics including mean, min, max temperatures, and rate of change.
* Upload CSV datasets directly from the frontend.
* View lists of available countries and regions.
* Fully integrated Flask backend with MySQL database and React frontend.

---

## Tech Stack

* **Backend:** Flask, Python, MySQL, flask-cors, pandas
* **Frontend:** React, Vite, TypeScript
* **Database:** MySQL (via XAMPP or any MySQL server)
* **Other:** CSV file support, CORS enabled for frontend integration

---

## Project Structure

```
ClimateProject/
│
├── Backend/          # Flask backend
│   ├── app.py
│   ├── .env          # Database credentials
│   └── venv/         # Python virtual environment
│
├── Frontend/         # React frontend
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── .env          # API URL
│
└── README.md
```

---

## Backend Setup (Flask + MySQL)

1. **Activate Python Virtual Environment**

   ```bash
   cd Backend
   venv\Scripts\activate
   ```

2. **Install Required Packages**

   ```bash
   pip install -r requirements.txt
   ```

   Or manually:

   ```bash
   pip install flask flask-cors mysql-connector-python pandas
   ```

3. **Configure MySQL**

   * Create database: `climate_db`
   * Create table `climate_data`:

     ```sql
     CREATE TABLE climate_data (
         id INT AUTO_INCREMENT PRIMARY KEY,
         country VARCHAR(100) NOT NULL,
         region VARCHAR(100) NOT NULL,
         year INT NOT NULL,
         month INT NOT NULL,
         temperature DECIMAL(5,2) NOT NULL,
         anomaly DECIMAL(5,2) NOT NULL,
         INDEX idx_country (country),
         INDEX idx_region (region),
         INDEX idx_year (year)
     );
     ```
   * Add your MySQL credentials in `Backend/.env`.

4. **Run Flask Server**

   ```bash
   python app.py
   ```

   The server runs at: `http://localhost:5000`

---

## Frontend Setup (React)

1. **Install Node Packages**

   ```bash
   cd Frontend
   npm install
   ```

2. **Configure API URL**

   * In `Frontend/.env`:

     ```env
     VITE_API_URL=http://localhost:5000/api
     ```

3. **Run Frontend**

   ```bash
   npm run dev
   ```

   Visit the app: `http://localhost:8080`

---

## Integration Checklist

* [x] Backend (Flask) runs without errors.
* [x] MySQL database exists and is connected.
* [x] Frontend fetches data from Flask API.
* [x] Upload CSV datasets through frontend successfully stores in database.
* [x] Endpoints return expected responses:

  * `/api/climate-data`
  * `/api/stats`
  * `/api/upload`
  * `/api/countries`
  * `/api/regions`

---

## Expected CSV Format for Upload

```csv
country,region,year,month,temperature,anomaly
USA,North America,2020,1,15.5,0.8
China,Asia,2020,1,12.3,-0.2
```

---

## Notes

* The project is fully functional with **Flask + MySQL backend** and **React frontend**.
* The frontend uses `VITE_API_URL` to communicate with Flask API.
* Use `npm run dev` to start frontend development server.
* CSV files must follow the expected format to avoid import errors.

---

