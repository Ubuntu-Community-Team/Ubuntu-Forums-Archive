---
title: "R² and panel data"
date: 2008-06-10
forum: Education &amp; Science
---

### Post by Jeanvs on 2008-06-10
As a student, i am working on a paper processing panel data. My professor at the university told me that R² is distorted when using panel data. Can anyone tell me why exactly or give me a good source  for an understandable explanation? 

btw, its getting quite urgent.

Thanx

---

### Post by NikoC on 2008-06-10
Hmmz,

Could you tell me what panel data are?

I assume that you are fitting some linear regression model through the data? Then the fitting works as follows: statistics software tries to fit a regression line through the data in such a way that the sum of squares of the offsets is minimized (i.e. the sum of squares of the differences between the real, measured values and the fitted values is the smallest sum possible = least squares fitting). Your R² value describes how well your predicted values fit your measured ones.
e.g. R² = 0 : very poor regression, the linear model applied does not fit the data at all
     R² = 1: the relationship between the dependent variable (Y) and the predictor (X) is perfectly linear.
     R² = 0.80: 80 % of the variation in of the dependent variable can be predicted by the linear model using X as a predictor...

Now if only I knew what panel data were... :)

edit: I'm not a statistics expert, but this is how it was explained to me in the latest course I followed (R).

---

### Post by Tart on 2008-06-10
I'm not really sure about panel data, but if you use regression through origin (regression without constant term), then the sum of squared residuals SSE for this type of regression may exceed the sum of total squares. This can occur when the data from curvilinear pattern or a linear pattern with intercept away form the origin. Hence, R-sq may turn out to be negative.  Coefficient of determination R-sq has no clear meaning for regression through the origin. (partially stolen from "Applied Linear Statistical Models" by Neter et al.)

---

### Post by Jeanvs on 2008-06-10
This is Wikipedias explanation of panel data: Data is broadly classified according to the number of dimensions. A data set containing observations on a single phenomenon observed over multiple time periods is called time series. In time series data, both the values and the ordering of the data points have meaning. A data set containing observations on multiple phenomena observed at a single point in time is called cross-sectional. In cross-sectional data sets, the values of the data points have meaning, but the ordering of the data points does not. A data set containing observations on multiple phenomena observed over multiple time periods is called panel data. Alternatively, the second dimension of data may be some entity other than time. For example, when there is a sample of groups, such as siblings or families, and several observations from every group, the data is panel data. Whereas time series and cross-sectional data are both one-dimensional, panel data sets are two-dimensional.

---

### Post by Tart on 2008-06-10
First of all, standard linear regression model assumes that errors are independent. As soon as you have any time series component on your hands this assumptions is most likely to be violated. One should be very careful when applying regression techniques to time series data. Things like Cochrane-Orcutt model should be used.  

[http://en.wikipedia.org/wiki/Cochrane-Orcutt_estimation](http://en.wikipedia.org/wiki/Cochrane-Orcutt_estimation)

Now, it is my guess that reason for unreliability of R-squared for panel data is the same as for regression through the origin. Basically fundamental regression equation SSTot= SSReg + SSErr is not satisfied, and as a consequence R-sq = SSReg/SSTot = 1 - SSErr/SSTot can be "funny" (negative or way too large).

I hope this helps.

---

