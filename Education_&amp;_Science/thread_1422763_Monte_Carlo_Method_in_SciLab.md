---
title: "Monte Carlo Method in SciLab"
date: 2010-03-05
forum: Education &amp; Science
---

### Post by JorgeM93 on 2010-03-05
Hello ubuntu users. As a project for the University, I've been told to apply the Monte Carlo Method ([http://en.wikipedia.org/wiki/Monte_Carlo_method](http://en.wikipedia.org/wiki/Monte_Carlo_method)) for a project, which requests using Matlab. Even though I could do it in my University's computers, I would like to see if I can do it from my Linux PC, using Scilab.

This procedure is used for simulation in experiments, and its somewhat "simple", like this:
-You want to simulate the value of a magnitude which depends on other ones (e. g. Velocity = distance/time), using a lot of generated values (1000 would be ok).
- Make 2 variables for the mean and standard deviation of every magnitude [easy]
- Generate random numbers for every magnitude accordign to the normal distribution [easy with the command rand(1 , 1000 ,'normal')
- Make the operations between magnitudes to find the one you want (point wise operations) [for example v=x./t]
- Estimate the mean of the generated results [e. g. mean(v)]
- And finally calculate the error margin*,_ which is the step at which I'm stuck_*, for this, you are supposed to use the **QUANTILE** function, but it seems not to appear in Scilab.  Basically, what I want to know are the numbers which's comulative frecuence are 2.5% and 97.5%
Any idea on how to do this final step?

Thanks for reading

---

### Post by JorgeM93 on 2010-03-06
The only thing I'd like to know if its possible to calculate quantiles in SciLab.

Tanks

---

### Post by memilanuk on 2010-03-06
Never used the program myself... but I downloaded the 10.19 MB PDF for the manual and did a text search for 'quantile' and got this...

Name
perctl — computation of percentils
p=perctl(x,y)
Parameters
x
real or complex vector or matrix
y
vector of positif integer values between 0 and 100.
Description
Compute the matrix p of percentils (in increasing order, column first) of the real vector or matrix x.
The percentils are indicated by the entries of y, the values of entries of y must be positive integers
between 0 and 100.
p is a matrix whose type is length(y) x 2 and the content of its first column are the percentils values.
The contents of its second column are the places of the computed percentiles in the input matrix x.
The minimum or maximum values in x are assigned to percentiles for percent values outside that range.

Go to page 1974 of the document (out of 3401 -yikes!!)

Not sure if thats what you're after or not... but it looks to be as close as it gets.

---

### Post by hubie on 2010-03-07
It isn't SciLab, but I'll put in my monthly plug for R. :)

What you described would be a four line script:

```
x <- rnorm(1000, mean=100, sd=5)
t <- rnorm(1000, mean=20, sd=2)
v <- x/t
quantile(v)

```

On my system I get:
```
      0%      25%      50%      75%     100% 
3.681100 4.639021 5.003037 5.375908 7.674783 

```

---

### Post by JorgeM93 on 2010-03-07
Tkank you for your replies.

I think I'd better start using R: its better for statistics; SciLab may be more useful when talking about Linear Algebra.


@memialunk:
Thank you for trying to help, I have also tried looking at SciLab's manual in order to find a "quantile" function. The problen with  perctl(x,y) is that it only allows integrer percentages, and I need decimal ones.

---

