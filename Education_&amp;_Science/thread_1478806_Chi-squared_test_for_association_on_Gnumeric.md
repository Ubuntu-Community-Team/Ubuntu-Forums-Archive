---
title: "Chi-squared test for association on Gnumeric"
date: 2010-05-10
forum: Education &amp; Science
---

### Post by Berk on 2010-05-10
Hey, I asked a little while ago about 2 way ANOVA without replication and got pointed towards Gnumeric.
Now I have a slightly different question, but along the same lines.
I'm now looking at doing a Chi-squared test for association, but me and my tutor are looking at Gnumerics stats options and not seeing anything obvious, so were wondering if it might be under another name.

If it is, what is it under, if not are there any easy ways of doing this?

Thanks in advance for any help you may be able to give.

---

### Post by gunksta on 2010-05-10
It's real real easy, but if you looked in the Tools -> Statistical Analysis, you would never find it.

A chi-square test is a standard Excel compatible function (although depending on the version of Excel, the results can be a little wonky in extreme cases). Gnumeric implements the standard functions in this regard.

Go to Insert -> Function and browse the list of statistical functions available in the standard gnumeric functions table. I suspect you will find what you are looking for. chitest() may do what you need it to do.

---

