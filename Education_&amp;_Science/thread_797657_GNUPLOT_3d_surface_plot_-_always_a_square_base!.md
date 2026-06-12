---
title: "GNUPLOT 3d surface plot - always a square base!"
date: 2008-05-17
forum: Education &amp; Science
---

### Post by swharden on 2008-05-17
contents of data.txt:
    0    1    4    9
    1    2    5   10
    4    5    8   13
    9   10   13   18
   16   17   20   25
   25   26   29   34

GNUPLOT COMMAND:  splot "data.txt" matrix with lines

PRODUCES: [http://t16web.lanl.gov/Kawano/gnuplot/fig/sample7.1g.png](http://t16web.lanl.gov/Kawano/gnuplot/fig/sample7.1g.png)

PROBLEM:  There are 4 columns of data and 6 rows, so the base of the graph SHOULD be a rectangle, but no matter what I do the base of the 3d graph is always a square!  How do I correct this?

Ultimately, I want to use a 5x200 matrix to produce a very long, very thin, 3d graph and contour map.  I can't figure it out for the life of me.  Thanks!!!  --Scott

---

### Post by mister_pink on 2008-05-18
I've not had much experience with gnu plot but a quick play indicates that it scales it to fit the window, so if you want it more rectangular, resize the window then click the "apply autoscale" button on the toolbar (next to the magnifying glasses)

---

