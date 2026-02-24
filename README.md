# Data Center Water Efficiency (WUE) Analysis

A datathon project that predicts optimal data center locations in the US based on **Water Usage Efficiency** (WUE = Annual Water Usage L / IT Energy kWh), using climate and grid-renewable data.

## Approach

1. **Regression model** — OLS on African data center data: WUE ~ wetbulb temperature + wind speed + precipitation + renewable energy share
2. **US climate data** — Weather via Open-Meteo API for US climate divisions
3. **Predictions** — Apply the model to US climate divisions to score locations

## Key Files

| File | Description |
|------|-------------|
| `datacenter_project.ipynb` | Main notebook: WUE model + US predictions |
| `wue_regression.py` | Standalone OLS regression script |
| `scrape_weather.py` | Fetches climate data (wetbulb, wind, precip) from Open-Meteo |
| `plot_climate_regions.py` | Map of predicted WUE by US climate division |
| `plot_world.py` | Map of grid carbon intensity + renewable plants + WUE sites |

## Setup

```bash
pip install pandas geopandas matplotlib statsmodels openmeteo-requests requests-cache retry-requests cmocean
```

## Data

- `data/daily_african_df.csv` — African data center climate + WUE (training data)
- `data/climate_data.csv` — US climate division aggregates (from `scrape_weather.py`)
- `data/CONUS_CLIMATE_DIVISIONS/` — US climate division shapefiles
- `geojson_files/` — Electricity zones, water efficiency points
