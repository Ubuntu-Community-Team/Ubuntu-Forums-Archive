---
title: "[SOLVED] Weighting Data in R"
date: 2008-06-13
forum: Education &amp; Science
---

### Post by gunksta on 2008-06-13
For those of you who are programatically inclined, I have an R-Cran questions for you.

I have a sampled data set that I need to weight. Basically, I sampled people working in a geographic region called a circuit. I know how many people I could have questioned and I know my sample size. Because my proportionality varies between circuit, I need to weight my data accordingly.

I could have R simply replicate the samples per circuit for the appropriate weighting, but this seems rather silly AND will make an already large data set, huge.

I am looking for a way to build cross-tabs (ftable, etc) that are weighted according to circuit in a way similar to how SPSS can let me define a weighting variable. In SPSS I can define a single variable (I usually call it weight) per sample, and it will let me change the weighting of the cross-tabs while keeping the number of cases in memory == to the original sample size. I'd like to know if/how to do this in R.

Thanks!

---

### Post by akniss on 2008-06-13
sounds to me like you want the wtd.table() function in the Hmisc package.
```
library(Hmisc)
?wtd.table
```

---

### Post by gunksta on 2008-06-13
Thanks akniss! That is exactly what I am looking for.

---

