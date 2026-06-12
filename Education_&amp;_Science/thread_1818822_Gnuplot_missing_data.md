---
title: "Gnuplot missing data"
date: 2011-08-05
forum: Education &amp; Science
---

### Post by Senplanet on 2011-08-05
Hello,
I am trying to plot my data with gnuplot while I have some missing values in dataset. I want to keep the gaps in the plot. With the option: set datafile missing "" it does the opposite want I need. It skips the missing data but it also connect the lines between last and next available values.
Is there any trick how to do it? 
Thanks

---

### Post by Senplanet on 2011-08-05
Solved! 
uhhh spent almost whole day...
The trick was just to use $ for the column with missing values. For example 
>plot "gap.dat" using ($2) lines 2
instead of 
>plot "gap.dat" using 2 lines 2

---

