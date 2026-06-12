---
title: "How should I process my graphs?"
date: 2010-03-07
forum: Education &amp; Science
---

### Post by goseph on 2010-03-07
I am doing a project at the moment that generates some amount of data.

I need to automate what I am currently doing by hand with spreadsheets:

- read in a plain text file of data

- parse it into two arrays of corresponding data series

- perform some simple numerical adjustments and do some calculations and output a graph with labels of what is going on.

What is the best way to go?

SciPy or... ?

---

### Post by not_a_phd on 2010-03-07
depending on the nature of the numerical adjustments and calculations, you may be able to use **gnuplot** for the whole thing.

---

### Post by ssam on 2010-03-08
scipy (really you probably just need the matplotlib and numpy parts) are great for this, and very flexible.

see
[http://www.scipy.org/Cookbook/InputOutput](http://www.scipy.org/Cookbook/InputOutput)
[http://matplotlib.sourceforge.net/](http://matplotlib.sourceforge.net/)

---

### Post by anoop999 on 2010-03-08
You can also use R.

---

### Post by anoop999 on 2010-03-08
[FONT=Lucida Console]# Sample R code for generating multiple graphs
# Assume you have a vector 'filenames' with text file names, and 'graphnames' with your desired graph file names
# THIS CODE WAS MADE UP OF THE TOP OF MY HEAD AND HAS NOT BEEN TESTED AND MAY HAVE BUGS! USE AT YOUR OWN RISK!

# Use the grDevices package to enable PDF output
library(grDevices)

for (i in 1:length(filenames)) {
    data <- read.delim(filenames[i])

    # Do your data processing

    # Produce the graph in PDF format with your preferred size and options
    pdf(graphnames[i], height=6, width=7)
    plot(data$x, data$y, xlab="X data", ylab="Y data")

    # Title of graph incorporating filename (if you wish)
    title(paste(c("Graph of ", filenames[i]), collapse=""))

    # Close and save the PDF
    dev.off()
}[/FONT]

---

### Post by ngrieb on 2010-03-08
If you are familiar with Matlab at all, Octave is a very good way to go as well, it plots using gnuplot, but might be useful for the calculations / editing of the data that you need done.

---

### Post by goseph on 2010-03-09
wow everyone thanks for the great responses. I do already know MatLab so I will probably look into using Octave. Although I am fairly tempted to learn SciPy and R just for kicks. Not enough hours in a day! Thanks for your time.

---

