---
title: "GLM in R (and specification of non-explanatory variables)"
date: 2009-10-28
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-10-28
Hi all,

I am trying to fit a model via the glm function in R. I am wondering if R will differentiate between categorical and continuous (covariate) variables, or will I need to specify either in the model. From the in-built help it appears neither and I had a quick rake through the R archives to no avail.

From what I gather, in SAS you typically specify the categoricals, whereas in Minitab it is the covariates. e.g.

```


## MTB Code

GLM "Y" = X1 X2;
Covariates 'X3';
Brief 3.

## SAS Code

proc glm;
  class X1 X2;
  model Y= X1 X2 X3/p solution;

# Note: May not provide equivalent functionality


```

How are these stipulated in R, is glm the right tool for the job or should I be investigating ANCOVA functions or another library function? Many thanks in advance!

Kind regards,

Pag

---

### Post by akniss on 2009-10-28
> **Mr_Pag said:**
> Hi all,

I am trying to fit a model via the glm function in R. I am wondering if R will differentiate between categorical and continuous (covariate) variables, or will I need to specify either in the model. From the in-built help it appears neither and I had a quick rake through the R archives to no avail.

From what I gather, in SAS you typically specify the categoricals, whereas in Minitab it is the covariates. e.g.

```



## SAS Code

proc glm;
  class X1 X2;
  model Y= X1 X2 X3/p solution;

# Note: May not provide equivalent functionality


```

How are these stipulated in R, is glm the right tool for the job or should I be investigating ANCOVA functions or another library function? Many thanks in advance!

Kind regards,

Pag

It depends on how your variables are coded. If you have a variable that is text (say, "M","F") then it will automatically assume they are categorical. If your variable is coded as a number, (say, "1", "2") then R will assume they are continuous. To tell R explicitly that you want those numeric values to be used as categorical variables, you may use the as.factor() function. 

Assuming variables a and b are numeric, and x and z are categorical:
```
as.factor(x)->x
as.factor(z)->z
glm(y~x+z+a+b)->fm1
summary(fm1)
```

should do the trick.

---

### Post by Mr_Pag on 2009-10-30
Nice one, thanks very much for your help!! I've give this a bash once I've updated to Karmic (I imagine a few people are in this boat today) - :D

All the best,

Alan

---

