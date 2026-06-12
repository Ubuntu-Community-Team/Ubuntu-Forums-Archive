---
title: "simple graphing package for experimental data"
date: 2007-03-22
forum: Education &amp; Science
---

### Post by junior aspirin on 2007-03-22
does anyone know of a good graphing package that i can do this in:

i have some results from an experiment i did at uni, for this i need to plot these results on a graph, but i need to plot 2 different variables against each other and also it needs to be plotted on log scaled axis.

i tried doing this in calc but couldn't work out how to have one variable set for the x axis and another for the y axis.

any help is very welcome, be it a linux or windows program, even one you have to pay for, since it may be on my university's computers.

---

### Post by louis_nichols on 2007-03-22
I'm at work now and only have Excel, so I will explain in Excel, although I'm very sure ooocalc can do this as well. Here goes:
> [LIST=1]
[*]Place your data in two columns in a worksheet
[*]Go to Insert>Chart, pick the kind of chart you wish and press Next
[*]On the next window, go to the TAB that sais Series. You will se a small window that lets you choose series. There, you pick the values you want on the Y axis.
[*]A little bit lower, on the same Series TAB, you will have a field called "X axis", where you will choose the values from another column than in Series.
[*]That's it.
[/LIST]

As I said, calc can do this as well, and in a very similar manner, but I can post about that only when I get home.

---

### Post by ahmatti on 2007-03-22
There are almost limitless options.

Read this thread:

[http://www.ubuntuforums.org/showthread.php?t=383180](http://www.ubuntuforums.org/showthread.php?t=383180)

---

### Post by akniss on 2007-03-22
> **junior aspirin said:**
> does anyone know of a good graphing package that i can do this in:

i have some results from an experiment i did at uni, for this i need to plot these results on a graph, but i need to plot 2 different variables against each other and also it needs to be plotted on log scaled axis.

i tried doing this in calc but couldn't work out how to have one variable set for the x axis and another for the y axis.

any help is very welcome, be it a linux or windows program, even one you have to pay for, since it may be on my university's computers.

Try gnumeric.  It takes a little while to get used to, but the plotting capabilities are extremely customizable once you learn it.

---

### Post by WW on 2007-03-22
You can use **gnuplot**.  For example, suppose you want to plot this data:
```

  1.1    18.0
  4.4    40.0
  8.3    89.0
 21.1    90.0
 44.0   249.7
 50.0   409.4
112.1   703.0
211.0  1310.0
300.0  2300.0
433.0  3015.0

```
Suppose this data is in a file called "data".  In the directory that contains this file, run **gnuplot**:
```

$ gnuplot
gnuplot> set logscale xy
gnuplot> set title "The Title"
gnuplot> plot "data" using 1:2 with linespoints

```
You can set many more attibutes and styles, and you can then output the plot in a variety of formats (postscript, jpeg, pdf, and many more).  For example, I have attached a PNG version of the plot. It was create with these commands:
```

gnuplot> set logscale xy
gnuplot> set title "The Title"
gnuplot> plot "data" using 1:2 with linespoints
gnuplot> set terminal png
gnuplot> set output "data.png"
gnuplot> replot

```
You can install gnuplot from Synaptic, or from the command line with the command
> 
sudo apt-get install gnuplot

Here is a web page with many useful tips for using gnuplot: [http://t16web.lanl.gov/Kawano/gnuplot/index-e.html](http://t16web.lanl.gov/Kawano/gnuplot/index-e.html)

---

### Post by raja on 2007-03-23
There are multiple ways to do this. It should be possible in Calc. However, I regularly use gnumeric for this - you can select a scatterplot and select the data for the x and y axes. Once done, you can save it as a bitmapped or vector image.

---

### Post by junior aspirin on 2007-03-23
oooo thanks, just been playing about with gnumeric, looks like just what im looking for, its come a long way since i last used it.

---

### Post by NikoC on 2007-03-26
Using RLPlot which is available from the repos, very nice basic thingy with GUI... the equivalent of graphpad in windows! Highly customizable charts!

---

