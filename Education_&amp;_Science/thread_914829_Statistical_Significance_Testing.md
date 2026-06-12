---
title: "Statistical Significance Testing"
date: 2008-09-09
forum: Education &amp; Science
---

### Post by talikarng on 2008-09-09
I would like to test whether or not loss in numbers from one group is significantly higher than for another group but have no experience with statistical software.
What would be my best option?

(Here is the scenario, Group A started with 225 people but went down to 75, group B started with 299 and went down to 142. I would like to work out whether or not there is a significant difference between these two groups)

---

### Post by SuperSonic4 on 2008-09-09
Well the percentage differences are

(original - new)/original *100% 

group A = (225-75)/225 = 66.67%

group B = (299-142)/299 = 52.50%

---

### Post by kaspar_silas on 2008-09-09
You have to clarify what you are measuring and your sources of errors.

For example if you test was ruled by simple counting statisitcs (say for example you were measuring radioactive decay of two Groups of atoms). Then the standard error for group A and B is 15 (the square root of 225). So the difference is statistically significant. However the system you are measuring may have much greater error sources which you would have to account for. 

Indiviudal error calculations don't require complex programs. However if you are adding several together or doing several groups you might want to use something like Gnumeric or another spreadsheet program.

---

### Post by mali2297 on 2008-09-09
I would suggest performing a chi-squared [contingency table test](http://en.wikipedia.org/wiki/Contingency_table) of the table
```

  Staid  Left
A   75   150
B  142   157

```
This leads to a p-value of approximately 0.001, which is highly significant.

It is a rather standard test that can be found in R and probably in many spreadsheet programs, although I can't find it in Gnumeric?

---

### Post by kaspar_silas on 2008-09-10
To be honest I was more thinking of actually entering the equations into Gnumeric. Thou now you come to mention it, R is a better choice. 

Standard statistics options can be very useful but be vary of using statistics you don't understand. For example, it is annoying when people quote MS excel's R^2 value (the one that you get for "free" when you fit a graph) but are baffled if you ask what R^2 actually is.

I take mali2297s point on the chi squared based  algorithm probably being best for you. But you may still need to evaluate errors. For example if group B had sources of error that group A.

If not saying it's wrong but you can't statistically justify a result by solely looking at the numbers and not knowing the method.

---

### Post by akniss on 2008-09-10
> **talikarng said:**
> I would like to test whether or not loss in numbers from one group is significantly higher than for another group but have no experience with statistical software.
What would be my best option?

(Here is the scenario, Group A started with 225 people but went down to 75, group B started with 299 and went down to 142. I would like to work out whether or not there is a significant difference between these two groups)

Henry Clay once said "Statistics are no substitute for judgment."
Andrew Lang said "He uses statistics as a drunken man uses lampposts - for support rather than for illumination."

Point: if you have some explanation for why the two groups responded differently, why does it matter if the two are 'significantly different' or not?  Why do you need a number to prove suspicion?  Especially if you have no replication of this phenomena, who is to say it was not a single freak event that could never be repeated?  My suggestion would be not to worry about whether the two are different statistically.  You obviously suspect that they are, so a post-hoc test to prove your point is one of the most common misuses of statistics.

---

