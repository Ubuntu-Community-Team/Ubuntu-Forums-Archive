---
title: "gnuplot: how to specify the range to be a list of discrete numbers?"
date: 2009-03-10
forum: Education &amp; Science
---

### Post by flylehe on 2009-03-10
Hi,
I am new to gnuplot and was wondering how to specify the range of plot to be a list of discrete numbers? For example, I have a file data.dat consisting of a list of numbers each of which corresponds to the one of the same position in [1 5 10 15 20 25 30 35 40 45 50 55 60 65 70]. If I try
```

plot [1 5 10 15 20 25 30 35 40 45 50 55 60 65 70] '${data.dat}' w l lt 1 lc 1 lw 6 

```
I would get error with an arrow pointed at "5", saying "':' or keyword 'to' expected"
Thanks for help me to fix this problem!

---

