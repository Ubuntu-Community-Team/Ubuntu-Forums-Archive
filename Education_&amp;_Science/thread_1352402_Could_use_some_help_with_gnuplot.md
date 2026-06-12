---
title: "Could use some help with gnuplot"
date: 2009-12-11
forum: Education &amp; Science
---

### Post by JPJones on 2009-12-11
Dear scientists/students,

I have been trying to work out how to process a data file using gnuplot without success and I am wondering if I can find some help in this forum.

The tricky part is the from of the data file:

Time - Signal1 - Signal2 - ... - Signal 20
1_______5______6__________7____
2_______4______5__________6____
3_______3______4__________5____
4_______2______3__________4____
5_______1______2__________3____

Note: The "_" character does not exist in the file, it is used for correct layout in this thread

There is a total of 20 signals that share a common Time axis. 

What I have been trying to achieve was to instruct gnuplot to use Column 1 (Time) as the X axis and create a plot for each of the columns (Signals) against that. That would mean 20 different plots Time/Signal1 Time/Signal2 Time/Signal3 etc.

I am hoping that I don't have to change the format of my data file, as it would take me way back in progress, diving me again into C++ coding with which I hoped that I was done with :)

Thanks in advance for any help.

---

### Post by mathyou on 2009-12-11
If my memory serves me:

plot 'filename' u 1:2
replot 'filename' u 1:3
replot 'filename' u 1:4
...etc

---

### Post by JPJones on 2009-12-11
It has actually worked, thanks a lot for your help.

---

