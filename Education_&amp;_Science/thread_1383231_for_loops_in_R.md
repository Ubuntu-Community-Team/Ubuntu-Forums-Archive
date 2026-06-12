---
title: "for loops in R"
date: 2010-01-17
forum: Education &amp; Science
---

### Post by cjmr on 2010-01-17
Hello!
 
I just started R and am trying to convert C code to it. I need help in checking if the two codes below are the same.
 
[I]for (i in 1:popsize) { 
  for (j in 1:maxvar) {
   gBest<-sample(top,size=1)   
   velocity[i,j]<-.4* velocity[i,j] + 1 * runif(1) * (pbestsVar[i,j] - popVar[i,j]) + 1 * runif(1) * (archiveVar[gBest,j] - popVar[i,j])
  }[/I]
* }*
 
and
 
[I]i<-seq(1,popsize)
 j<-seq(1,maxvar)[/I]
*velocity[i,j]<<-.4* velocity[i,j] + 1 * runif(1) * (pbestsVar[i,j] - popVar[i,j]) + 1 * runif(1) * (archiveVar[gBest,j] - popVar[i,j])*
 
Also does using lapply instead of a for loop increase performance?
 
many thanks

---

### Post by samden on 2010-01-17
Don't know C so can't help with the main query, but I understand lapply should be considerably faster than a for loop. Having said that I still tend to use for loops for nearly everything... I'll need to improve that!

---

