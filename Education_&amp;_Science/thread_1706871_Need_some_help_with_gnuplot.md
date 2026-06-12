---
title: "Need some help with gnuplot"
date: 2011-03-14
forum: Education &amp; Science
---

### Post by Biblion on 2011-03-14
Hey guys, 
The problem is that i have a data file and i have to create a graph with gnuplot.
Basically what i need is to have an error bars there.
Data file has 3 columns -x, y, delta y.The last one contains mistakes made.
I did it this way-
gnuplot> plot 'C:\Users\Irina\Desktop\gp45-winbin\dati.txt'with errorbars
Is it ok?

---

### Post by jazzgossen on 2011-03-16
It seems OK to me. Doesn't it produce the output that you expect? What happens?

---

### Post by Lateralis on 2011-03-18
you're missing at least one character.  Should be 'yerrorbars' not 'errorbars'.  Also, I like to be totally explicit.  If it were me I'd go

```

gnuplot> plot 'C:\Users\Irina\Desktop\gp45-winbin\dati.txt' using 1:2 with yerrorbars

```

assuming column 3 are the errors on y.  But it is entirely up to you.

---

### Post by Biblion on 2011-04-07
Alright, thanks a lot.
I have one more question, can I save the gnuplot session file and then open it on the other computer to view commands?

---

### Post by Lateralis on 2011-04-07
In Linux you can write scripts which you can execute using he command line.  Here is an example script I use on a computer cluster at work:

```


#!/home/spja/bin/gnuplot/bin/gnuplot
plot '[data file]' using 1:3  w lines, '[data file]' using 1:4 w lines, '[data file]' using 1:5 w lines
set size 1.0, 0.6
set terminal postscript portrait enhanced mono dashed lw 1 'Helvetica' 14
set output '[output filename].ps'
replot
pause -1

```

Executing this code creates an output file with the specified name and filetype, in the above case .ps.  

You can change the script to be whatever you need it to be.  The first line should point to the location of the gnuplot binary (which in my case is in my home directory as gnuplot is not installed by default on the cluster front end), and I'm sure you can work the rest out.

---

### Post by Biblion on 2011-04-08
Thank's a lot!
But today I have tried to load gnuplot session file in 2 other gnuplot versions (earlier ones) and it didn't load.
When I type load command it says:
gnuplot> set style ellipse size graph 0.05, 0.03, first 0 angle 0 units xy
                   ^
         "Graph_1", line 39: expecting 'data', 'function', 'line', 'fill
', 'rectangle', or 'arrow'

---

