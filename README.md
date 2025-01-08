Petal Power Inventory Analysis

This repository contains the code for analyzing the inventory of Petal Power, a chain of gardening stores. The project involves analyzing inventory data from multiple store locations to fulfill customer requests, improve decision-making, and assist with marketing efforts.

Table of Contents

	•	Overview
	•	Features
	•	Dataset Description
	•	Installation
	•	Usage
	•	Code Overview
	•	Contributing
	•	License

Overview

The Petal Power Inventory Analysis project processes inventory data for:
	1.	Retrieving product information for specific locations.
	2.	Filtering products based on specific criteria.
	3.	Calculating the value of inventory and adding detailed product descriptions.

Features

	•	Inspect inventory for specific store locations (e.g., Staten Island, Brooklyn).
	•	Filter products by type and location (e.g., find seeds sold in Brooklyn).
	•	Identify whether products are in stock.
	•	Calculate the total value of current inventory.
	•	Generate complete product descriptions for marketing purposes.

Dataset Description

The dataset, inventory.csv, contains the following columns:
	•	location: The store location.
	•	product_type: The type of product (e.g., seeds, flowers, tools).
	•	product_description: A description of the product.
	•	quantity: The quantity of the product in stock.
	•	price: The price of the product.

Installation

	1.	Clone the repository:

git clone https://github.com/your-username/petal-power-inventory.git
cd petal-power-inventory


	2.	Install dependencies:

pip install pandas


	3.	Make sure inventory.csv is in the project directory.

Usage

	1.	Open the script in your Python IDE or terminal.
	2.	Run the script to perform inventory analysis:

python inventory_analysis.py


	3.	Modify the code to answer additional business questions as needed.

Code Overview

Key Functions

	1.	Inspecting Data:
	•	Load and view the first 10 rows of the dataset:

print(data.head(10))


	2.	Filtering Data:
	•	Retrieve data for specific locations (e.g., Staten Island, Brooklyn).
	•	Filter based on product type and availability.
	3.	Adding Calculated Columns:
	•	in_stock: Indicates whether a product is in stock (True/False).
	•	total_value: Calculates the total value of inventory (price * quantity).
	•	full_description: Combines product_type and product_description for marketing purposes.

Example Code

import pandas as pd

data = pd.read_csv('inventory.csv')

# Inspect first 10 rows
print(data.head(10))

# Filter Staten Island location
staten_island = data.head(10)
product_request = staten_island['product_description']

# Filter Brooklyn seeds
seed_request = data[(data['location'] == 'Brooklyn') & (data['product_type'] == 'seeds')]

# Add in_stock column
data['in_stock'] = data['quantity'] > 0

# Add total_value column
data['total_value'] = data['price'] * data['quantity']

# Add full_description column
combine_lambda = lambda row: '{} - {}'.format(row.product_type, row.product_description)
data['full_description'] = data.apply(combine_lambda, axis=1)


