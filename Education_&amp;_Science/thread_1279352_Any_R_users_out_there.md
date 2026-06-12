---
title: "Any R users out there?"
date: 2009-09-30
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-09-30
Hey folks,

I'm studying an MSc in applied stats at the moment. The faculty only supports SAS, but I fancy learning R as the price is right and I get to use it on my Ubuntu lappie.

(I'm aware of a linux native SAS, but I can't get that)

So quicky question -

I need to encode my variable test$Sex, currently a factor, as a vector in a separate variable so I can perform multiple regression.

```


test$Gender <- c(test$Sex)


```

So far, so good. Only trouble is is that it encodes this data as 1 and 2, as opposed to 0 and 1. Not a massive problem but I can't follow the examples in the book. Do you know how I could either

a) Specify numbers as 0,1 from test$Sex
b) take test$Gender and recode it as 0,1 without having to redefine this variable.

Pardon me if my terminology is a little out, I've probably got an hours worth of R experience to my name.

Thanks in advance!!

P

---

### Post by samden on 2009-09-30
Firstly, a better way of writing your code would probably be
```
 test$Gender <- as.numeric(test$Sex) 
```
which is a bit easier to understand what you were trying to do when you come back and read it in a few months time! But this still has the same problem. 

The reason is that R codes the first value as "1" when converting a factor to a numeric vector, and the second as "2". Very logical, and it would make a lot of sense if your variables were "male" and "female", it is just a little bit confusing since they are already numbers ("0" and "1").

A simple solution would be:
```
 test$Gender <- as.numeric(test$Sex)-1 
```
That will convert the factor to "1" and "2", then subtract 1 to make them "0" and "1". 

Nice and easy!

Good luck with R, I could have used SAS too but chose to use R for my PhD for the same reason, it's far more convenient to have it on your own laptop. And it worked well for me!

---

### Post by ahmatti on 2009-10-01
You could also use the ifelse function:

```

#Make some data
 sex <- c('M','F','F','M') 

#recode it 
sex <-  ifelse(sex=="M",1,0)

```

---

### Post by gunksta on 2009-10-01
The suggestions given to you by samden and ahmatti are excellent, but I wanted to throw out a couple of possible caveats.

ifelse() is a wonderful function, but is sometimes a little slow. This is irrelevant for most datasets, but can matter if you are working with something like Census data or another huge data-set.

as.numeric() will work, but it's important to understand how R orders it's levels. You have already observed that the first label in R is a 1 and the second is a 2. Have you also noticed that it puts them into alphabetical order?
```

test <- as.factor(c("Male", "Female", "Male", "Female"))

test

```

Look at the output and note that although Male comes first, it is the second level. (Output below, NOT code)
```

> test2                                                   
[1] Male   Female Male   Female                           
Levels: Female Male

```

Thus,
```

as.numeric(test)

```

returns 2,1,2,1 and NOT 1,2,1,2.

I mention this because it matters if you need to later look at only males or only females. Which is which? I have no idea how the data your book is using is structured and I have never used SAS. **But, IF 0=Male and 1=Female** in the data-set used by your course, samden's original code will get it precisely backwards because 0 will be Female.

But, there's a really easy solution to that little problem.

 test$Gender <- abs(as.numeric(test$Sex)-2)
:P


This behavior is really exciting when you import a data-set from SPSS using the foreign library. In this case, R will not follow it's own norm, but will instead use the levels as defined in the SPSS file by default. This is important to remember when working with SPSS data sets, which appear to be the on-going bane of my existence.  :)

---

### Post by Mr_Pag on 2009-10-01
Folks,

Thank you all for these wonderfully concice and prompt replies. On a forum not directly related to R too. Nice one.

Bravo chaps :)

P

---

### Post by samden on 2009-10-01
No worries Mr_Pag, I think you'll find R is one of the most popular pieces of software in this part of the forum, there's usually some help to be had here!

If you ever can't get the answer here, the R mailing list archive is at:
[http://www.nabble.com/R-f13819.html]("http://www.nabble.com/R-f13819.html")
The mailing list is very active and a great help.

---

