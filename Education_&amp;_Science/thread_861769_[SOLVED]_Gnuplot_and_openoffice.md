---
title: "[SOLVED] Gnuplot and openoffice"
date: 2008-07-16
forum: Education &amp; Science
---

### Post by arkara on 2008-07-16
I want to plot some data in order to use the graph on latex.
i have exported the on a csv file, but i can't plot them..
any idea?

i get this error message

```
gnuplot> plot 'test4.csv'
              ^
         Bad data on line 1

gnuplot>                  
```

---

### Post by WW on 2008-07-16
What do the first couple lines of test4.csv look like?

---

### Post by arkara on 2008-07-17
> **WW said:**
> What do the first couple lines of test4.csv look like?

this is the whole csv file..

```
'x'	'y'
1	2
2	4
3	6
4	8
5	10
6	12
7	14
8	16
9	18
10	20

```

---

### Post by jeremytaylor on 2008-07-17
If you take out the column names it should work. I've never managed to convince gnuplot to be happy with having text in a data file but there probably is a way to do it!

Jeremy

---

### Post by luisfcup on 2008-07-17
jeremytaylor is correct, gnuplot doesn't like characters in numeric data columns.
You can simply comment the undesirable lines:
```

#'x'  'y'
1   2
2   4
...

```
If you want to label the axis in gnuplot you can do it with set labbel command like this:
```
gnuplot> set xlabel "x-axis"
gnuplot> set ylabel "y-axis"
gnuplot> plot "test4.csv"
```

---

### Post by arkara on 2008-07-17
> **luisfcup said:**
> jeremytaylor is correct, gnuplot doesn't like characters in numeric data columns.
You can simply comment the undesirable lines:
```

#'x'  'y'
1   2
2   4
...

```
If you want to label the axis in gnuplot you can do it with set labbel command like this:
```
gnuplot> set xlabel "x-axis"
gnuplot> set ylabel "y-axis"
gnuplot> plot "test4.csv"
```


ok it now works.

---

