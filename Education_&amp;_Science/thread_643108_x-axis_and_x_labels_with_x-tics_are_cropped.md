---
title: "x-axis and x labels with x-tics are cropped"
date: 2007-12-17
forum: Education &amp; Science
---

### Post by Aramis on 2007-12-17
Dear all,

I have a very simple problem, and yet I cannot find a solution.

I have created a GnuPlot script with the following instructions:

```

set xtics ("Some Label" 0, "Another Such label = 500" 1, "And again
and again = 1000" 2, \
"There is more text = 2000" 3, \
"And even more here = 4000" 4, "Label must be chosen wisely = 8000" 5,
\
"Labels must mean somthing = 16000" 6, "Be self-explainatory = 32000"
7, \
"This one should not fit = 64000" 8)
set xtics rotate by -45

```

The code above is followed with plot instructions that assign
numerical values to each of the defined labels. You can see the actual
output at the following URL : [link ]("http://www.dcs.napier.ac.uk/~cs205/_x-axis_problem.png")

As you can see the last label does not appear in full in the image,
and thus my question is simple:
what is the procedure that I must follow to prevent this problem.

Here are the instructions that use to save the plot as a PNG file, but
please note that the axis is cropped even in the default terminal ( I
would have assumed that the default output window would auto-stretch
to fit the plot but no :( )

```

set term png size 1024, 768 font "Arial.ttf" 12
set output "_x-axis_problem.png"

```

Thank you for reading this message.

Ar@mi$ - Researcher in desper

---

### Post by meatpan on 2007-12-17
If you post the entire script, I will try to reproduce and debug this problem.

I have a hunch that you will need to manually set the margins.  Here is some potentially relevant text from the gnuplot 4.2. docs:  [http://www.gnuplot.info/docs/node200.html#set_margin](http://www.gnuplot.info/docs/node200.html#set_margin)

> Normally the margins of a plot are automatically calculated based on tics, tic labels, axis labels, the plot title, the timestamp and the size of the key if it is outside the borders. If, however, tics are attached to the axes (set xtics axis, for example), neither the tics themselves nor their labels will be included in either the margin calculation or the calculation of the positions of other text to be written in the margin. This can lead to tic labels overwriting other text if the axis is very close to the border.

---

### Post by Aramis on 2007-12-18
Hi Meatpan,

the "** set rmargin x**" command does indeed solve my problem.

Thank you for your help.

Aramis

---

