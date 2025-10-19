# rossman-sales-prediction
Sales Prediction of Rossman Store using Machine Learning.

<h2>Introduction</h2>

This project aims to predict Sales for Rossman retail chain to optimize their inventory and staff management.

<h2>About Dataset</h2>

Kaggle Dataset link : <a>https://www.kaggle.com/datasets/pratyushakar/rossmann-store-sales</a>

This dataset contains historical data from over 1000 rossman stores located across European countries.
The dataset provides detailed information about daily sales, promotions, competition, holidays, and store characteristics.

<h4>Data Files</h4>

train.csv - Historical data including daily sales for each store.

test.csv - Test set used for generating final predictions.

store.csv - Metadata describing each store’s characteristics such as type, assortment, and competition details.

<h4>Data Overview</h4>
Time period covered: January 2013 to July 2015

Total observations (training data): ~1 million rows

Number of stores: 1,115

Target variable: Sales (numeric, daily revenue per store)

<h4>Key Insight</h4>

The dataset exhibits strong seasonality (weekly and monthly patterns) and promotional effects, making it well-suited for time series forecasting and feature engineering based on dates and promotions

<h2>Data Preprocessing</h2>
<b>Merging Datasets : </b>Combines Store.csv and train.csv using Store column.

Before data preprocessing , rows where the store is closed was dropped because if the store is closed the sales will obviously be 0 and they those discarded data might just create unnecessary assumptions for the model.

<h4>Handing missing values</h4>

Filled missing values in CompetitionDistance with median distance.
Replaced missing values in Promo2SinceWeek, Promo2SinceYear, and PromoInterval with 0 because there was no Promo2 on those days.
Filled missing values of Competition open since year and month with Store's Year and Month.
Converted Date into Day,Month,Year to capture seasonal trends.

<h4>Feature Engineering</h4>

Derived CompetitionOpenSince column from CompetitionOpenSinceYear*12 - CompetitionOpenSinceMonth .
Replaced Store column with Store's average Sales as we can neither classify Store as a categorical column because it has nearly 1000 different values and not as numerical column because Store as a numerical column doesn't make any sense.

One hot encoded categorical columns like StoreType , Assortment , StateHoliday , PromoInterval.

<h2>Model Selection</h2>
The dataset is split into three parts :
train_df : 01-01-2013 - 31-05-2015
validation_df : 01-06-2015 - 31-06-2015
test_df : 01-07-2015 - 31-07-2015
Baseline model is the average sales of a particular Store and RMSE for baseline model is RMSE of training dataset  1957.6067285072904
RMSE of validation dataset  2205.5202719243725
RMSE of test dataset  1740.1523045840597 

