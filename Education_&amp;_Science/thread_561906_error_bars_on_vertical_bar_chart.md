---
title: "error bars on vertical bar chart"
date: 2007-09-28
forum: Education &amp; Science
---

### Post by hollowhead on 2007-09-28
I want to plot a graph with my numerical data represented by vertical bars, with each bar having its own separate (different) standard error, both gnumeric and oO calc will plot this type of graph but only allow you to put a constant error amount on each bar (my error is different for each bar), in I've also tried RLplot and qtiplot but without success so far.

Incidentally I cannot get gnumeric (whose plotting features I like) to put axes names in -is this just me I've looked at the help pages online, but still cannot see anyway of doing it.  Using gnumeric  and oO calc feisty versions RLplot and Qtplot latest version.

Ta.  Neil

---

### Post by qazwsx on 2007-09-28
Try gnuplot. It's CLI program, but it can be very handy like in scripting. I like it a lot. Maybe this will help:
[http://t16web.lanl.gov/Kawano/gnuplot/intro/style-e.html](http://t16web.lanl.gov/Kawano/gnuplot/intro/style-e.html)

---

### Post by hollowhead on 2007-09-28
Thanks,  but I really don't want to work at the command line.

---

### Post by tweedledee on 2007-09-28
> **hollowhead said:**
> I want to plot a graph with my numerical data represented by vertical bars, with each bar having its own separate (different) standard error, both gnumeric and oO calc will plot this type of graph but only allow you to put a constant error amount on each bar (my error is different for each bar), in I've also tried RLplot and qtiplot but without success so far.

Incidentally I cannot get gnumeric (whose plotting features I like) to put axes names in -is this just me I've looked at the help pages online, but still cannot see anyway of doing it.  Using gnumeric  and oO calc feisty versions RLplot and Qtplot latest version.

Ta.  Neil

Gnumeric will do this, at least with XY plots (the only type I ever use): Just click on X or Y errors for the series of interest, choose Absolute, and provide it with the range(s) of cells containing the error values.

I'm not sure what you mean about "axes names."

---

### Post by hollowhead on 2007-09-28
Thanks for your reply "tweedledee", yes it does but it seems to put the same SEM value in for every column.  I tried it my first column has a  value of about 21 with an SEM of 2.1.  My first column had this value which is correct but it put his SEM for the next column in the chart which had a different SEM, you could see in fact every column in the graph had the same sized error bars.  Also I can find no way to label the axis, this seems to be missing from gnumeric although it did manage to import an xy chart from excel with them in.

---

### Post by machoo02 on 2007-09-28
To put axis labels on graphs, right click on your graph and select Properties.  This will bring up the "Customize Graph" dialog.  In the scrolling selection window in the upper left, scroll down and select the axis you would like to put a label on.  Click on the 'Add' button beneath the selection window: this will bring up a drop-down list.  Select 'Label' from the list, and either type the axis label into the dialog box, or use the navigation button to choose the cell containing your desired axis name.

hope this helps.

EDIT: I have attached a sample histogram that shows both axis labels as well as error bars.  Just right-click on the graph and select "Properties" to see how it is set up.

---

### Post by ssam on 2007-09-28
you could try labplot [http://labplot.sourceforge.net/](http://labplot.sourceforge.net/)

it is in the repos.

---

### Post by tweedledee on 2007-09-29
> **hollowhead said:**
> Thanks for your reply "tweedledee", yes it does but it seems to put the same SEM value in for every column.  I tried it my first column has a  value of about 21 with an SEM of 2.1.  My first column had this value which is correct but it put his SEM for the next column in the chart which had a different SEM, you could see in fact every column in the graph had the same sized error bars.  Also I can find no way to label the axis, this seems to be missing from gnumeric although it did manage to import an xy chart from excel with them in.

Are you providing an entire range for the error bars or just a single value?  I get the expected behavior (different error bars for each data point) as long as I provide a matching column of data.  I only can see what you are describing if I select a single cell as the error value.  The abiility to have different error values for each point is why I use Gnumeric as much as OO Calc.

---

### Post by hollowhead on 2007-10-01
Thanks machoo02 your instructions worked perfectly I pasted your "data" into a new sheet and followed your instructions-what you showed is exactly what I want , thanks everyone else for your help and suggestions.  Neil.

---

### Post by machoo02 on 2007-10-01
> **hollowhead said:**
> Thanks machoo02 your instructions worked perfectly I pasted your "data" into a new sheet and followed your instructions-what you showed is exactly what I want , thanks everyone else for your help and suggestions.  Neil.

No problem...glad I could help!

---

