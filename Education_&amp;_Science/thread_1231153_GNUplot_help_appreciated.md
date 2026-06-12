---
title: "GNUplot help appreciated"
date: 2009-08-04
forum: Education &amp; Science
---

### Post by lorenz_b on 2009-08-04
Hi everyone,

I try to plot data with the following command in gnuplot:

```
plot "elutions2009-08-04.dat" using 2:xtic(1) title column, "" using 3:xtic(1) title column
```

this is giving me nice histograms. How can I make gnuplot to put the actual values on top of each histogram?

cheers,
Lorenz

---

### Post by lorenz_b on 2009-08-05
sorry,
I just realized, that the information provided in my first post was a little sparse.
so i have a datafile that looks like that:
```

Elution wt nf
1 0.55 0.57
2 0.91 0.84
3 0.22 0.24
4 0.09 0.06
5 0.02 0.02
6 -0.01 -0.01

```

and the gnuplot file is:
```

set style data histogram
set style histogram cluster gap 1
set style fill   solid 1.00 border -1
set xlabel "elution #"           
set ylabel "protein conc. [mg/ml]"            
set title "Protein distribution in elution fractions 1 to 6"
set auto x
set yrange [-0.1:1.0]
plot "datafile.dat" using 2:xtic(1) title column, "" using 3:xtic(1) title column

```

as written in my first post I would like to have the bars of the histograms automatically labeled with the actual value. Is there any possibility? I couldnt find out so far.

cheers,
Lorenz

---

### Post by barnex on 2009-08-05
I can only come up with a rather "ugly" solution: manully put some labels on the desired coordinates:

```

set label 1 "myvalue", a at 12,1200

```

Of course this is by no means automated but it might help you if you only need a few of those values in a few plots.

good luck...

---

