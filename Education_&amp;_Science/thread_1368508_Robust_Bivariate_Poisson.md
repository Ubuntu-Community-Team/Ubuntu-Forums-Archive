---
title: "Robust Bivariate Poisson"
date: 2009-12-30
forum: Education &amp; Science
---

### Post by ryusukekenji on 2009-12-30
To Experts, 

x = x1 + x3 
y = x2 + x3 
x3 = cov(x1,x2) 

By refer to package "bivpois", I'ld like to downweight previous x,y in my data based on date, I am wondering if lambda3 should robust as well, since lambda3 measure the co-relationship of lambda1 and lambda2, but if  robust lambda3 might effect the covariance of lambda1 and lambda2 I though. 

I am sorry if misunderstanding the concept of a bivariate Poisson. Appreciate if experts willing to share precious advice.

---

### Post by euler_fan on 2009-12-31
> **ryusukekenji said:**
> To Experts, 

x = x1 + x3 
y = x2 + x3 
x3 = cov(x1,x2) 

By refer to package "bivpois", I'ld like to downweight previous x,y in my data based on date, I am wondering if lambda3 should robust as well, since lambda3 measure the co-relationship of lambda1 and lambda2, but if  robust lambda3 might effect the covariance of lambda1 and lambda2 I though. 

I am sorry if misunderstanding the concept of a bivariate Poisson. Appreciate if experts willing to share precious advice.

Please specify the full form of the distribution function. We can help you more once we have that.

Please sketch the problem of interest. We can give you more constructive feedback if you understand the problem you're trying to solve.

A couple thoughts up front:
1) Why are you worried about weighting with time? If so, you need to specify a discounting function. Normally a parametric time series uses the discount to a power=the number of time periods which have elapsed. The more extreme the discount, the less the past matters. A moving average, however, works a little differently. Hybrids can be specified if you like.
2) You clearly are unconcerned about a prior . . . or do you have some reliable prior information? Unreliable prior information?
3) What system are you using? If it's R, then the R-help list will be more suited to your inquiries about implimentation b/c everyone there uses said system and the average level of comfort doing fancy things in that language is higher. Also, you get a higher percentage of working statisticians than you will here.

---

### Post by ryusukekenji on 2010-01-01
> **euler_fan said:**
> Please specify the full form of the distribution function. We can help you more once we have that.
 
Please sketch the problem of interest. We can give you more constructive feedback if you understand the problem you're trying to solve.
 
A couple thoughts up front:
1) Why are you worried about weighting with time? If so, you need to specify a discounting function. Normally a parametric time series uses the discount to a power=the number of time periods which have elapsed. The more extreme the discount, the less the past matters. A moving average, however, works a little differently. Hybrids can be specified if you like.
2) You clearly are unconcerned about a prior . . . or do you have some reliable prior information? Unreliable prior information?
3) What system are you using? If it's R, then the R-help list will be more suited to your inquiries about implimentation b/c everyone there uses said system and the average level of comfort doing fancy things in that language is higher. Also, you get a higher percentage of working statisticians than you will here.
 
Robust bivariate poisson papers below,
[http://stat-athens.aueb.gr/~jbn/papers/presentations/2009_IMA_Sport2_Groningen.pdf](http://stat-athens.aueb.gr/~jbn/papers/presentations/2009_IMA_Sport2_Groningen.pdf)
[http://stat-athens.aueb.gr/~jbn/papers/23/paper_imaconf2009_v0-2.pdf](http://stat-athens.aueb.gr/~jbn/papers/23/paper_imaconf2009_v0-2.pdf)
 
Weighted Function Equations 4.5, 4.6 and 4.7
[http://www.math.ku.dk/~rolf/teaching/thesis/DixonColes.pdf](http://www.math.ku.dk/~rolf/teaching/thesis/DixonColes.pdf)
 
By refer to 3papers above, I would like to make my static model be dynamically while I am not really understand the Maximum Likelihood on Equations 4.5, 4.6 & 4.7 above...

---

