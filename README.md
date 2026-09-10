# ECE 2112 - EXPERIMENT 3: PYTHON DATA ANALYSIS (PANDAS)

HUIT, THIMOTY JOSHUA O.

2ECE-B

9/10/2026

## Objective of this Activity

The objective of this activity is to learn how to use Pandas to load data, select specific rows and columns, filter records using conditions, and extract a specific subset of data without changing the original DataFrame.

## A. POSITIONAL AND LABEL-BASED SLICING

First, the `cars.csv` file was loaded into a Pandas Dataframe named `cars`.

    import pandas as pd

    cars = pd.read_csv('cars.csv')
    cars

The `pd.read_csv()` function is used to read the data from the `cars.csv` file and store it in the DataFrame named cars.

**Checking the shape**

    print("Shape: ")
    print(cars.shape)

The `.shape` function shows the number of rows and columns in the DataFrame. This helps determine the size of the dataset.

**Checking the Column Names**

    print("Column names: ")
    print(cars.columns.tolist())

The `.columns` function gets the names of the columns in the DataFrame while `.tolist()` converts them into a list so they are easier to display.

**Selecting Rows 6 to 10**

    cars_6_to_10 = cars.iloc[5:10]
    cars_6_to_10

The `.iloc` function is used to select rows based on their position. Since Python starts counting from 0, `5:10` selects the 6th to the 10th data rows.

**Selecting the Required Columns** 

    cars_6_to_10 = cars_6_to_10[["Model", "mpg", "cyl", "hp", "gear"]]
    cars_6_to_10

This code selects only the required columns which are `Model`, `mpg`, `cyl`, `hp`, and `gear`.

I used `cars_6_to_10` instead of `cars` because `cars` contains the complete dataset. Using `cars` here would select these columns from all of the rows instead of only rows 6 to 10

## B. MODEL LOOKUP

For this part, Boolean indexing is used to find specific car models based on the values in the `Model` column.

**Toyota Corolla**

    toyota = cars[cars["Model"] == "Toyota Corolla"]
    toyota

The condition checks the `Model` column and searches for the value `"Toyota Corolla"`. The matching record is then stored in the variable `toyota`.

    print("Toyota Corolla: ")
    print(toyota)

Now if you'll run this the condition we put to show the rows and columns will appear.

**Pontiac Firebird**

    pontiac = cars[cars["Model"] == "Pontiac Firebird"]
    pontiac = pontiac[["Model", "mpg", "hp", "wt"]]

    print("Pontiac Firebird")
    print(pontiac)

First, the code searches for the Pontiac Firebird using the `Model` column. After finding the correct record, only the required columns are selected.

This allows the requested information for the Pontiac Firebird to be displayed without using a specific row number.

## C. MULTI-MODEL SUBSETTING

For this part, a list is created containing the three required car models.

    models = ["Datsun 710", "Lotus Europa", "Ferrari Dino"]

The list contains the model names that we need to find in the dataset.

**Selecting the Three Models**

    selected_cars = cars[cars["Model"].isin(models)]
    selected_cars = selected_cars[["Model", "mpg", "cyl", "hp", "gear"]]

The `.isin()` function checks the `Model` column and finds the rows that contain any of the models inside the `models` list.

After selecting the rows, the code keeps only the required columns: `Model`, `mpg`, `cyl`, `hp`, and `gear`.

**Displaying the Selected Cars**

    print("Selected Cars: ")
    print(selected_cars)

This displays the three selected car models together with the requested information

**Checking the Shape**

    print("Selected_cars Shape")
    print(selected_cars.shape)

The `.shape` function is used to check the number of rows and columns in the final DataFrame

which will results in `(3, 5)`. This means that the final DataFrame has 3 rows and 5 columns.


## Conclusion

In this activity, I learned how to use Pandas for basic data analysis and DataFrame manipulation. I used `read_csv()` to load the `cars.csv` file, `iloc` to select rows by position, column labels to select specific columns, Boolean indexing to find specific car models, and `.isin()` to select multiple models. Through these operations, I was able to create the required subsets of data while keeping the original `cars` DataFrame unchanged.
