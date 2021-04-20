# Online-Retail-Analysis
# Objective:
Performing Customer Segmentation /Grouping based on their similar characteristics and using their RFM Scores. The  idea is to segment customers based on when their last purchase was, how often they’ve purchased in the past, and how much they’ve spent overall. 
# About the dataset:
* The dataset was taken from kaggle
* **InvoiceNo**: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction.If this code starts with letter 'c', it indicates a cancellation.
* **StockCode**: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
* **Description**: Product (item) name. Nominal.
* **Quantity**: The quantities of each product (item) per transaction. Numeric.
* **InvoiceDate**: Invoice Date and time. Numeric, the day and time when each transaction was generated.
* **UnitPrice**: Unit price. Numeric, Product price per unit in sterling.
* **CustomerID**: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
* **Country**: Country name. Nominal, the name of the country where each customer resides.
# Exploratory Data Analysis:

**Data Cleaning**:

![ora1](https://user-images.githubusercontent.com/25876186/113345128-a4b5a800-934f-11eb-9185-12ece464441f.png)

The data has missing values and they clearly need to be treated.

![ora2](https://user-images.githubusercontent.com/25876186/113345246-d0389280-934f-11eb-9f0a-455d491f89aa.png)

* At first, While taking a  look at the data, we can see the unit price is  0.0, so when the unit price is 0, when we calculate the total amount i.e unitprice* Quantity that will also amount to 0. There can be no customer who orders a product in large quantites and pay nothing. Also when we look at the record-538919 the quantity is in negative,so we're dropping the records with unit price 0.
* So when that is done, the 0.2% of data which has NaN for description also gets dropped.
* Also we need to store the cancelled orders data separately. Analysis can be done on them separately.
* Dropping all the missing values.
* In certain rows the quantites are still negative, so dropping them too and cleaning the other discrepencies of data.
* Creating new columns such as **TotalPrice = quantity * UnitPrice** and storing the **date** alone in a separate column.
* Regarding stock codes and description, A stock code can have more than 1 description of the product.

![ora3](https://user-images.githubusercontent.com/25876186/113346206-29ed8c80-9351-11eb-9188-3d3e8d288972.png)

* Finding out which transaction had highest sum of purchase:

![ora4](https://user-images.githubusercontent.com/25876186/113346496-89e43300-9351-11eb-9153-589f0baf5d11.png)

* Countries: There are 37 Countries in which UK seems to dominate the most.

![ora5](https://user-images.githubusercontent.com/25876186/113347531-ea27a480-9352-11eb-8155-d4b07a3968f2.png)

* Which customer has ordered more number of Products?

![ora6](https://user-images.githubusercontent.com/25876186/113347691-29ee8c00-9353-11eb-91a2-3b4b7165e66d.png)

* Customer 14646 has ordered more no of products
* Which Product on the whole has been sold(total)?
![ora8](https://user-images.githubusercontent.com/25876186/113348482-417a4480-9354-11eb-8e73-2c824d06c1c9.png)

![ora7](https://user-images.githubusercontent.com/25876186/113348502-48a15280-9354-11eb-82dd-1fc2a4ec6d3c.png)

* Calculating the RFM Values:
RFM stands for **recency, frequency, and monetary value**. The  idea is to segment customers based on when their last purchase was, how often they’ve purchased in the past, and how much they’ve spent overall. All three of these measures have proven to be effective predictors of a customer's willingness to engage in marketing messages and offers.
* Recency: Date of Last of Purchase
* Frequency: Total Number of Orders
* Monetization: Total Order Value

* Building a Model using KMeans Clustering:
KMeans clustering model is built. Elbow curve is plotted and silhoutte score is obtained. After analyzing and visualizing we can see that the cluster 3 performs well when compared with others.

![ora9](https://user-images.githubusercontent.com/25876186/113351273-43460700-9358-11eb-92a3-c38946dccb4c.png)

* Going with 3 clusters wrt clustering method.
* RFM Analysis:
Creating Quartiles based on the RFM Values and creating scores. The graph here represents each group on their total sum of purchase made by the customer, here is the top 10 of each group.

![ora10](https://user-images.githubusercontent.com/25876186/113351691-d5e6a600-9358-11eb-908d-2114ca5d89fa.png)

# Conclusion:
RFM Analysis benefits an organization in:
* Personalization:  By creating effective customer segments, you can create relevant, personalized offers.
* Improve Conversion Rates: Personalized offers will yield higher conversion rates because your customers are engaging with products they care about. 
* Improve unit economics.
* Increase revenue and profits.


