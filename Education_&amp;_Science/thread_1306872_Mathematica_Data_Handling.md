---
title: "Mathematica Data Handling"
date: 2009-10-30
forum: Education &amp; Science
---

### Post by rajan on 2009-10-30
Hi, I'm having some problems with Mathematica importing my x,y data from various files and then processing them. The import seems to be going fine with the command 

```
DA23 = Import["/home/rajan/Work/ExpData/PL/102109/P147DA23.PRN", 
  "Data"]
```

which outputs an array of x,y data like this (truncated)

```
{{430, 650}, {430.5, 624}, {431, 644}, {431.5, 636}, {432, 734}, { }}
```

but i can't figure out how to numerically integrate this data set. The examples (and the actual syntax) seem to require a function in order to integrate it. I'd rather not have to set up some sort of calculation that does this same thing because someone else has probably done it. thanks for reading.

---

### Post by Chronon on 2009-11-01
That is the impression I get too.  You probably need to write a short routine to carry out a summation algorithm.  Simpson's rule maybe?

---

### Post by rajan on 2009-11-03
yeah that's what i was thinking ... when i was sitting in math class in high school, i never thought i would actually use simpson's rule again. maybe i'll try the other methods in that chapter and send it to my teacher for laughs. thanks for the post, Chronon

---

