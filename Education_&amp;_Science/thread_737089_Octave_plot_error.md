---
title: "Octave plot error"
date: 2008-03-27
forum: Education &amp; Science
---

### Post by browny254 on 2008-03-27
Hi, I have just started using koctave, but when i use the plot function i get the following error

```
error: __plt2vv__: vector lengths must match
error: evaluating if command near line 53, column 3
error: called from `__plt2vv__' in file `/usr/share/octave/2.1.73/m/plot/__plt2vv__.m'
error: evaluating if command near line 55, column 5
error: evaluating if command near line 48, column 3
error: called from `__plt2__' in file `/usr/share/octave/2.1.73/m/plot/__plt2__.m'
error: evaluating if command near line 58, column 4
error: evaluating if command near line 56, column 2
error: evaluating if command near line 55, column 7
error: evaluating while command near line 44, column 5
error: evaluating if command near line 30, column 3
error: called from `__plt__' in file `/usr/share/octave/2.1.73/m/plot/__plt__.m'
error: called from `plot' in file `/usr/share/octave/2.1.73/m/plot/plot.m'
error: evaluating for command near line 151, column 1 
```

im sure its not a vector error as i checked the length of the variable and they are the same. I did a bit of searching and found others who had the same problem, but no solutions on how to fix it.

- Andrew.

---

### Post by browny254 on 2008-03-27
dont worry...i got it working finally.

---

### Post by gorgonikos on 2008-11-10
how did you fix it? I've got a similar problem. Can't plot anything! 
Thanks in advance...

---

### Post by jpkotta on 2008-11-15
It helps to post a minimal example of what you're trying to do.

---

