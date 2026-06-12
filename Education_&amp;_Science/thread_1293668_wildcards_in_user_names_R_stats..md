---
title: "wildcards in user names R stats."
date: 2009-10-17
forum: Education &amp; Science
---

### Post by Mr_Pag on 2009-10-17
Hi Folks,

I have a question regarding wildcards in R, could I simplify this following code using control structures? i.e a for statement for (i in 1:n)

> 
  yarn1 <- yarn[which(yarn$spinner=='1'),]
  yarn2 <- yarn[which(yarn$spinner=='2'),]
  yarn3 <- yarn[which(yarn$spinner=='3'),]
  ...
  yarnn <- yarn[which(yarn$spinner=='n'),]


I can't figure out how to directly itegrate wildcards into variable names. I had a look through the R archives, but have had no luck.

Can anyone point me in the direction of a solution, or has a solution?

Thanks in advance,

Alan

---

### Post by ahmatti on 2009-10-18
You can do what you want with the assign command:

```

for (i in 1:n){
  assign(paste('yarn',i,sep=''), yarn[yarn$spinner==i,])
}


```

---

### Post by gunksta on 2009-10-18
ahmatti beat me to this.

---

### Post by Mr_Pag on 2009-10-18
Thank you, this is a terrific technique to learn. I'm sure it'll be useful for all sorts of things. Many thanks!!

---

### Post by ahmatti on 2009-10-19
You're welcome! There is also the "split" function, which can be used in similar problems as the above code.

---

