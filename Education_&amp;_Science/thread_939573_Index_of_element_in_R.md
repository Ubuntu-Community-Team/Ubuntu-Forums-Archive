---
title: "Index of element in R ?"
date: 2008-10-06
forum: Education &amp; Science
---

### Post by gvanto on 2008-10-06
I was wondering if there's a index-of-element type function in R
which will give me the index of an element within a vector:

```

a <- c(2, 3, 7, -4, 5, 2)

#If I would like to get the pos of '-4', how to get this? (other than writing a loop) ?

```

Help much appreciated!

Gerry
Vector newbie

---

### Post by Tart on 2008-10-06
Depending on what you need you may use one of the following

ind.1 <- (a==-4) # this will output a TRUE/FALSE vector
ind.2 <- which(a==-4) # this will give you numerical value

> ind.1
[1] FALSE FALSE FALSE  TRUE FALSE FALSE
> ind.2
[1] 4
> a[ind.1]
[1] -4
> a[ind.2]
[1] -4

---

### Post by vanadium on 2008-10-06
x = c(3,7,2,3)
i = seq(1,length(x))

Now, the index of the value 2 can be returned with

i[x==7]

[edit] after studying Tart's contribution: which() is the function you are looking for:

```

> which(x==7)
[1] 2

```

---

### Post by gvanto on 2008-10-06
Thanks alot Tart and Vanadium,
that's perfect !

---

