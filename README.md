# Prediction of directional movement in Financial Markets - An Optimization Approach

The forecasting of stock price may serve as an essential recommendation system to invest money in stock market. Every investor mainly looks for maximum profit that can be earned and it is quite difficult to select appropriate stock prediction system for the investments. It is necessary to choose a forecasting algorithm for making accurate prediction and this completely depends on a particular algorithm because every algorithm performs in a different way and give different results. Algorithms such as SVR, Linear regression are available but this might not give accurate results in time series data. While the algorithm such as SARIMA, SARIMAX, VAR, VARMA, VARMAX, ARIMA etc. are available for time series data. Some neural networks such as RNN and LSTM can also be used for time series data and neural networks are meant to be learn appropriately. The focus of this study will be on LSTM and ARIMA the results generated by both of these techniques are analysed and explained how these two techniques are performing.

**LSTM Approach**


![image](https://user-images.githubusercontent.com/61080527/147283022-eb3d73b0-e793-4452-b01d-8a9598a4c929.png)

Long short-term memory (LSTM) is a part of recurrent neural network. LSTM based model can predict some arbitrary values into the future after getting trained on the basis of previous information or historical data. A traditional LSTMconsists cell state (ct), hidden state (ht), input gate, forgetgate and output gate which makes LSTM efficient in terms ofboth long-term and short-term dependencies.

Below are the key terms from our LSTM model.

**a.** Optimizer used: Adam.

**b.** Dropout per iteration: 20%

**c.** Loss function used: Mean squared error (MSE).

**d.** Batch size used: 64

**e.** Epochs: Trained for 100 epochs.

**f.** Validation size: 35% of total data.

**g.** Validation loss: 0.0011



**ARIMA Approach**


![image](https://user-images.githubusercontent.com/61080527/147283680-6644e160-04b3-480d-bf1c-6f3fac2f2ab2.png)

The basic requirement for using ARIMA model in any dataset is that the dataset must be stationary i.e. it should not have any trend or seasonality. To check if any dataset column stationary or not Dickey-Fuller test can be used. The value of result variable ‘p’ determine if the dataset is stationary or not.

![image](https://user-images.githubusercontent.com/61080527/147284116-115ea3ba-b15b-4857-bc32-dd0b2686e4e2.png)

We find out value of p for AAPL Dataset and p value found was 0.11. Hence we provide differencing parameter to ARIMA as d=1, so that dataset can be made stationary.
The parameter d=1 symbolizes that each value of dataset will be subtracted from the previous values.

**ARIMA (a, d, q):**
	
	‘a’ is the degree to which the variable correlates itself.  
        
	‘d’ is the differencing to make dataset stationary. The value of d may vary in different datasets depending on the stationarity of that dataset. The value of d was kept for AAPL dataset d=1.
         
	 ‘q’ is the Moving Average i.e. window of indexes in the series which is averaged to get result. The value of q was varied between 2 to 10.




![image](https://user-images.githubusercontent.com/61080527/147284029-b938a712-543b-4f2d-a332-968374afee23.png)


**AutoCorrelation**

![image](https://user-images.githubusercontent.com/61080527/147284360-f15780e1-96d7-4864-8734-387123b93646.png)

ACF(Auto-Correlation) curve, the optimal (that give more accuracy) value of parameter q can be found. The minimum point that crosses the blue region is 5. Thus the
value of parameter q can be taken as q=5. Thus, finalized values are: (a=5, d=1, q=5). The point to be note here is that these values are optimal for only this particular dataset and performance may deteriorate if used in other dataset. This is also one of major drawback of ARIMA algorithm.



![image](https://user-images.githubusercontent.com/61080527/147284572-3bec31f1-5652-4348-b8ef-d92f13973cac.png)

In the above figure, the blue line denote the original datavalues and red line denotes the prediction done on the training data and green line shows the prediction done by LSTM
model for testing data.

![image](https://user-images.githubusercontent.com/61080527/147284664-33195488-9b00-4491-9b82-993d8e678470.png)

While predicting time-series based values using ARIMA model the values of parameters (a, d, q) plays a major role. The efficient values of these parameters will make it more prone to predict the accurate values. The predictions were found for testing data and were compared with original values which gives us satisfactory efficiency. The curve above shows the performance of model. The orange line is the actual data of the dataset and blue line symbolizes the predicted values by the ARIMA model.


![image](https://user-images.githubusercontent.com/61080527/147284808-39fd4d0f-73d3-4ccb-9c37-8b4fa892c19d.png)

The prediction of future values of the stock closing prices can be performed. Below is the curve that shows future predicted stock values. The blue line shows the closing price of stocks till date. The orange line shows the stock values of the company in the future.(here it is 30 days). The model can perform predictions of future values but not give accurate results for long time span.


![image](https://user-images.githubusercontent.com/61080527/147284895-ffe13221-7e94-4aa3-bf34-369a4fd5706b.png)


**Conclusion**

The predictions done using the two different algorithms shows that LSTM gives more accurate results as compared to ARIMA model. ARIMA also has its own drawbacks as lot of preprocessing needs to be done before feeding the data to ARIMA model. On the other hand LSTM approach is more effective and can work better in multiple datasets. The accuracy of LSTM based forecasting were found higher than ARIMA.







