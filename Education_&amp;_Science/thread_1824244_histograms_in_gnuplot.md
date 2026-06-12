---
title: "histograms in gnuplot"
date: 2011-08-13
forum: Education &amp; Science
---

### Post by 1cookie on 2011-08-13
hi

Ive searched countless of gnuplot examples of histograms but all assume too much (for me at least). I'm looking for a gnuplot script that will generate something similar to:

[http://www.gcsemathstutor.com/histograms.php](http://www.gcsemathstutor.com/histograms.php)

a nice simple GCSE data plot with variable bin widths. I've been following: [http://gnuplot.sourceforge.net/demo/histograms.html](http://gnuplot.sourceforge.net/demo/histograms.html) but this doesn't show any 'data.file' and without this the example is useless really. I am familiar with gnuplot for functions in 2D, but the histogram defeats me.

Can anyone offer a script that explains the datafile, gnuplot script and an output to a png or a jpeg file?

;)

---

### Post by PC_load_letter on 2011-08-14
did you look [here]("http://gnuplot.sourceforge.net/demo/histograms.html")?

---

### Post by 1cookie on 2011-08-15
> **PC_load_letter said:**
> did you look [here]("http://gnuplot.sourceforge.net/demo/histograms.html")?

Ive seen that, it doesn't explain the data set; or anything for that matter!...

---

### Post by PC_load_letter on 2011-08-16
Here it is:
[http://212.182.0.171/cgi-bin/dwww/usr/share/doc/gnuplot-doc/examples/immigration.dat](http://212.182.0.171/cgi-bin/dwww/usr/share/doc/gnuplot-doc/examples/immigration.dat)

You can find the file on your hdd at the same location if you have the package gnuplot-doc installed. 

Hope this helps.

---

### Post by PC_load_letter on 2011-08-16
Also, in the gnuplot code, replace the immigration.dat by the path to the file. 
In my case I copied the file to the home folder and my last line in one of the examples was: ```
plot **'~/immigration.dat'** using 6:xtic(1) ti col, '' u 12 ti col, '' u 13 ti col, '' u 14 ti col
```

and it worked!

---

### Post by 1cookie on 2011-08-16
> **PC_load_letter said:**
> Also, in the gnuplot code, replace the immigration.dat by the path to the file. 
In my case I copied the file to the home folder and my last line in one of the examples was: ```
plot **'~/immigration.dat'** using 6:xtic(1) ti col, '' u 12 ti col, '' u 13 ti col, '' u 14 ti col
```and it worked!

Edit

That was a big help, thanks. But I'm trying to get something similar to: [http://www.gcsemathstutor.com/histograms.php](http://www.gcsemathstutor.com/histograms.php)

I have (ignore the titles for now):

```

# If we don't use columnhead, the first line of the datafile
# will confuse gnuplot, which will leave gaps in the plot.
set key top left outside horizontal autotitle columnhead

#set xtics rotate by 90 offset 0,-5 out nomirror
set ytics out nomirror
set ylabel 'frequency density'
set title 'House Prices in Manchester £000s'

set style fill solid border -1
# Make the histogram boxes half the width of their slots.
set boxwidth 3

# Select histogram mode.
set style data histograms
# Select a row-stacked histogram.
set style histogram clustered

plot "~/Desktop/data" using 2:xticlabels(1) lc rgb 'green'

```with data 

```

Date          Level_0_Mins  Level_1_Mins  Level_2_Mins
2011-01-08    0.2         161.08        22.58
2011-01-15    0.4         104.00        70.33
2011-01-22    0.6         79.75         16.17
2011-01-29    0.3         99.25         21.74
2011-02-05    0.1         155.33        33.33

```What im really trying to emulate is:

I'll try to attach a screenshot, one moment.

---

### Post by 1cookie on 2011-08-16
Screen shot attached. You see, I dont need all the bells and whistles, just a straight forward plot, with joined-up bin values. Thanks.

---

### Post by PC_load_letter on 2011-08-16
This is what I'm getting with your code, could you list the changes that you want to make? Here:

---

### Post by 1cookie on 2011-08-17
> **PC_load_letter said:**
> This is what I'm getting with your code, could you list the changes that you want to make? Here:


Hi
I need a histogram which:

The histogram shows the price distribution of houses in an area
of Manchester. Prices are given in thousands of pounds (to the nearest thousand).

see screenshot attached: (data included)

:D

---

### Post by PC_load_letter on 2011-08-17
> **1cookie said:**
> Hi
I need a histogram which:

The histogram shows the price distribution of houses in an area
of Manchester. Prices are given in thousands of pounds (to the nearest thousand).

see screenshot attached: (data included)

:D

I can probably take a closer look and see how to tweak your code to fit your needs, but in all honesty, gnuplot would not be my 1st choice for this task from the start. You can EASILY do this in LibreOffice Calc, Gnumeric, R (but it's not as easy as Calc), or even Python's Matplotlib.

---

### Post by 1cookie on 2011-08-18
> **PC_load_letter said:**
> I can probably take a closer look and see how to tweak your code to fit your needs, but in all honesty, gnuplot would not be my 1st choice for this task from the start. You can EASILY do this in LibreOffice Calc, Gnumeric, R (but it's not as easy as Calc), or even Python's Matplotlib.

hi
Why didn't I think of that - 'a spreadsheet'! thanks. I'll answer that for you: I was looking for consistency. So if i plot a quadratic eq in gnuplot I'd get the same style axis and layout for a histogram. Well that was my thinking. I'll have a look at those tips though, thanks. :confused:  And if you could find a gnuplot for the data i shown, well, I'd buy you a beer sir! :D

---

### Post by 1cookie on 2011-09-02
Going back to post #9 - the histogram 'how it should look.' Ive come pretty close to what I'm trying to achieve using LibreOffice 3 - (see attached screen shot).

The only problem with this is the columns don't have variable width like the original question! I think this is a problem inherent in spreadsheets in general?

The spreadsheet allows for various formatting on individual elements; but has no way of variable column widths. :(

---

### Post by qinjieli on 2011-09-19
This may be what you are looking for--[http://gnuplot-surprising.blogspot.com/2011/09/plot-histograms-using-boxes.html](http://gnuplot-surprising.blogspot.com/2011/09/plot-histograms-using-boxes.html). The histogram plotted in this article looks like this:[ATTACH]202470[/ATTACH]

---

### Post by 1cookie on 2011-09-19
> **qinjieli said:**
> This may be what you are looking for--[http://gnuplot-surprising.blogspot.com/2011/09/plot-histograms-using-boxes.html](http://gnuplot-surprising.blogspot.com/2011/09/plot-histograms-using-boxes.html). The histogram plotted in this article looks like this:[ATTACH]202470[/ATTACH]


That certainly is an improvement, thanks. But when it comes to statistics and euclidean geometry, nothing is close to **Autograph**. Ive downloaded a free 30 day trial, and its a stunning piece of mathematical software (example files attached). I bet there are open source gurus out there who know of something similar, maybe not? I'd love to hear from you if you do...:)

---

### Post by memilanuk on 2011-09-19
Is something like this what you're trying to do?

[http://stackoverflow.com/questions/5787096/normalizing-histogram-bins-in-gnuplot](http://stackoverflow.com/questions/5787096/normalizing-histogram-bins-in-gnuplot)

---

### Post by 1cookie on 2011-09-19
> **memilanuk said:**
> Is something like this what you're trying to do?

[http://stackoverflow.com/questions/5787096/normalizing-histogram-bins-in-gnuplot](http://stackoverflow.com/questions/5787096/normalizing-histogram-bins-in-gnuplot)


Not really. I'm targeting a GCSE (higher) audience. This graph is nothing like one would see in an actual UK maths exam paper. Thanks all the same. =;

---

