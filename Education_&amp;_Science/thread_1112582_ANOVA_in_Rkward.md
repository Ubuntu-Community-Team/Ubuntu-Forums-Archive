---
title: "ANOVA in Rkward???"
date: 2009-03-31
forum: Education &amp; Science
---

### Post by PeregrinGo on 2009-03-31
Hi all,

I've been looking for an ANOVA plugin for Rkward. This webpage: [http://rkward.sourceforge.net/wiki/index.php?title=List_Of_Menu_Items_and_Plugins](http://rkward.sourceforge.net/wiki/index.php?title=List_Of_Menu_Items_and_Plugins) indicates that there is one, but I haven't been able to find it and I'm not quite sure where to look. I'm in a first semester statistics course, and I've been learning SAS syntax, but the prospect of learning another "language" for R isn't really appealing to me. **So**, if there **is** such an animal as an ANOVA plugin or package for Rkward, I would love to know. Thanks in advance for any info you can provide!

---

### Post by NikoC on 2009-04-01
Heyz,

Haven't really found the anova function myself in rkward but you could use the console:
model1<-aov(dependent_variable~factor)
summary(model1)

post-hoc with tukey:
tukey1<-TukeyHSD(model1,"dependent_variable")

or pairwise t test with:
pairwise1<-pairwise.t.test(x_values, grouping_values,p.adjust="bonferroni")

Cheers

---

### Post by samden on 2009-04-22
Anovas are easy in R, no need to download any extra plugins.

First you run a linear model (I have named the result model 1):
```
model1 <- lm(data ~ block + treatment + block*treatment)
```
Which means: linear model of "data" as a function of block, treatment, and the block by treatment interaction.

R will run that code and not display anything - but don't panic! Unlike SAS or other packages like that, rather than printing out pages of rubbish you have to trawl through to find the one number you wanted, R prints nothing. You then ask it to tell you just the results you want.

So to get the anova, simply type:
```
anova(model1)
```

And it will print the anova. Easy. If you want more info:
```
summary(model1)
```
That will print contrasts.

Happy analysing!

---

### Post by ahmatti on 2009-04-23
> **samden said:**
> 
First you run a linear model (I have named the result model 1):
```
model1 <- lm(data ~ block + treatment + block*treatment)
```

I'd rather use the aov function for ANOVA, as NikoC illustrated. It is the same model as lm, but Tukey post hoc and model.tables() only work with the aov fit.

Also interaction in R formulae is specified with ':' and not '*'. * is used for specifying the main effects + interaction so infact:

```
block*treatment = block+treatment+block:treatment
```

It is not a problem in this example as R is smart enough not to include the main effects twice, but can cause undesired effects in more complex models.

---

### Post by samden on 2009-04-23
Thanks for that ahmatti, you learn something new every day!

I hope PeregrinGo hasn't given up...

---

