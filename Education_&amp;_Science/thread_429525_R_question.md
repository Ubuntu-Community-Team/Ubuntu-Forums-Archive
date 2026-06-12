---
title: "R question"
date: 2007-05-01
forum: Education &amp; Science
---

### Post by Lise on 2007-05-01
Hi

(I know this forum is maybe not the right place to ask it)

Have R a function for group analysis:
for oexample I have a set of data : length of men and women
now I have to calculate the mean length of the women only

if it is not, how I can define such a function. 
I know you can sort variables but if i sort one variable, the other isn't sorted yet.

grtz 
Lise

---

### Post by Lise on 2007-05-01
> **Lise said:**
> Hi

(I know this forum is maybe not the right place to ask it)

Have R a function for group analysis:
for oexample I have a set of data : length of men and women
now I have to calculate the mean length of the women only

if it is not, how I can define such a function. 
I know you can sort variables but if i sort one variable, the other isn't sorted yet.

grtz 
Lise

I could program a function in java, but how can I use that in R?

grtz
Lise

---

### Post by akniss on 2007-05-01
> **Lise said:**
> Hi

(I know this forum is maybe not the right place to ask it)

Have R a function for group analysis:
for oexample I have a set of data : length of men and women
now I have to calculate the mean length of the women only

if it is not, how I can define such a function. 
I know you can sort variables but if i sort one variable, the other isn't sorted yet.

grtz 
Lise

Might the tapply() function be what you are looking for?
```
sex<-rep(c("M","F"),10)
length<-rnorm(20)*10+100
all.data<-data.frame(sex,length)

tapply(all.data$length,all.data$sex,mean)
```

If you are interested in just performing operations on one group, it may be easier to subset the data:
```
m.data<-subset(all.data, sex=="M")
mean(m.data$length)
summary(m.data)
m.data$sqrt.length<-m.data$length^0.5
m.data

```
etc.... etc....

---

