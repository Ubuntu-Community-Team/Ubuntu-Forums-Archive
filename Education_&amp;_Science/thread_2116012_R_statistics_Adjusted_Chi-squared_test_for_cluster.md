---
title: "R statistics: Adjusted Chi-squared test for clustered binary / categorical data"
date: 2013-02-14
forum: Education &amp; Science
---

### Post by ugm6hr on 2013-02-14
I'm looking for some assistance in statistical analysis with R, but also some general stats advice.
I am analysing cardiac phenotype data by comparing 2 groups. The 2 groups are unmatched individuals, but within each group, they are clustered in family subgroups (of between 1 and ~6).
I want to report the difference in prevalence of a specific ECG appearance (binary - i.e. either present or absent in each individual) between the 2 groups.
For example:
> Group 1 consists of 157 individuals comprised of 41 family clusters
Group 2 consists of 463 individuals comprised of 163 family clusters
Prevalence of x in Group 1 = 22.9%
Prevalence of x in Group 2 = 24.6%
Group 1 are cases and Group 2 controls (i.e. not randomized)
What test is most appropriate in this circumstance, and which package in R provides the easiest way to account for the clustering of relatives within families?
Having looked around, I have found:
[LIST]
[*]Ratio estimate chi-square test
[*]Generalized estimating equation
[/LIST]
But I have no experience of either of these techniques, and can't find any examples of their use in R.
Can anyone help?
(PS: This is not homework)

---

### Post by ugm6hr on 2013-02-15
Have done some digging / research:

I believe that the Donner (1989) or Rao & Scott (1992) modifications of chi-squared may be appropriate.

I have found package(aod) which includes functions donner() and raoscott()

I would certainly appreciate a second opinion on which to use, and what options are appropriate. I'm leaning to Donner (as below).

Currently:

```
donner(cbind(y,n-y) ~ group, data=matrix)
raoscott(cbind(y,n-y) ~ group, data=matrix)
```

---

