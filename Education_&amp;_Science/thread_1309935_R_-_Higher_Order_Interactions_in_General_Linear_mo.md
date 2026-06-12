---
title: "R - Higher Order Interactions in General Linear models"
date: 2009-11-01
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-11-01
Hi folks,

Can you help? 

I have a model I want to fit using the glm like so:

glm(Y ~ X1 + X2 + X3)

I also want to investigate higher order interactions, i.e.

2nd order > Y ~ X1 + X2 + X3 + X1*X2 + X1*X3
3rd order > Y ~ X1 + X2 + X3 + X1*X2 + X1*X3 + X1*X2*X3

And assess the requirement of such terms using partial F-tests, check for multicollinearity etc. 

This example is easy enough with only three explanatory variables, but with more vars calculation of the higher order terms becomes more complicated.

Does anyone know of a way to have R perform F-tests on the terms in ascending order? Thanks in advance!!

Best regards,

P

---

### Post by hubie on 2009-11-02
I'm not very versed in what you want to do, but I did happen recently upon [this paper]("http://www.stat.umn.edu/geyer/5931/mle/seed2.pdf") that goes through what you want to do.  Pay particular attention to Section 1.2, where, apparently, it matters what order you put in your interaction terms in your formula.

---

### Post by Mr_Pag on 2009-11-02
Thank you very much - it looks like an excellent paper!! I'll have a good read through this, it is nice to have an example specifically in R (the notes are in everything but).

The specific section I am studying is on multicollinearity, and the idea behind plotting all the nth order models is to assess the effects on the fit (through comparison of R^2, MSE etc.) - I am also investigating a package called leaps, which I believe may help me find an optimum model through the best subset approach.

Best regards,

Alan

---

