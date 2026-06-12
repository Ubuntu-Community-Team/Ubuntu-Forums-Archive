---
title: "Ternary Plot Software"
date: 2008-11-14
forum: Education &amp; Science
---

### Post by epitaph on 2008-11-14
I must have wasted over an hour today trying to find a super-simple way to generate decent looking ternary plots on my laptop install of Ubuntu.

There are quite a few spreadsheets (xls) floating around that can generate ternary plots, but a lot of them didn't work adequately in OpenOffice.

I just want a super-simple free program that lets me paste in data and generates a visually acceptable ternary plot.

Does anyone have any recommendations or experience with this? Thanks in advance.

---

### Post by jbrefort on 2008-11-14
May be gnuplot can do that? When I find time, I'll try to implement them in gnumeric, but clearly a low priority task for me, sorry.

---

### Post by hzambran_cl on 2008-11-19
You can try with R ([http://www.r-project.org/](http://www.r-project.org/)) + the 'ternaryplot' included in the 'vcd' package.

If you are new to R, you could go to [http://cran.r-project.org/doc/manuals/R-admin.html](http://cran.r-project.org/doc/manuals/R-admin.html) for installing instructions and first steps. 

Once you have installed R, you can install the 'vcd' package with:

> install.packages("vcd")

I hope this be useful for you.

Mauricio

---

### Post by epitaph on 2008-11-20
Thanks for your suggestion, I'll keep it in mind and try it out if I get the time before this semester ends.

For now, my solution was to run TriDraw in wine. The bad part? Only 2.9 would run, which has a limit on the amount of data points you can input.

I have some functions that will do ternary plotting in MATLAB, but I really just need to be able to copy+paste and get an output to see trends and classify the data.

Thanks again!

---

### Post by sputnik on 2009-09-10
> **hzambran_cl said:**
> You can try with R ([http://www.r-project.org/](http://www.r-project.org/)) + the 'ternaryplot' included in the 'vcd' package.

If you are new to R, you could go to [http://cran.r-project.org/doc/manuals/R-admin.html](http://cran.r-project.org/doc/manuals/R-admin.html) for installing instructions and first steps. 

Once you have installed R, you can install the 'vcd' package with:

> install.packages("vcd")

I hope this be useful for you.

Mauricio

I have found that several R packages will produce ternary diagrams.  They all look better than anything I personally have seen in Excel. However, you may need to try some of them out to see the options (there is almost always an example to try with each package). Different options are good for different applications of ternary plot. Personally I have started to use triax.plot in plotrix. There are ternary plots in ade4 (triangle.plot), and also
plot.acomp in compositions
tri in cwhmisc.cwhtool
ternary in StatDA
ternaryplot in Zelig
I have not tried these last 4 yet.

---

### Post by sputnik on 2009-09-10
Try [http://addictedtor.free.fr/graphiques/]("http://addictedtor.free.fr/graphiques/") for examples  of many graphs in R

---

### Post by cholericfun on 2009-09-10
> **epitaph said:**
> 
I have some functions that will do ternary plotting in MATLAB, but I really just need to be able to copy+paste and get an output to see trends and classify the data.

Thanks again!

just open an editor and type
A=[

and then paste the date in, closing with ]
and  execute the "script" (mark all; F11)
then (modify and) execute the scripts for plotting the data

this should be quick enough?

---

### Post by epitaph on 2009-09-10
This thread came back from the dead!

Looks like R is probably the most preferred way of doing it -- I just have so much scientific/statistical software on my laptop it's getting ridiculous.

I discovered the really convenient import data wizard in MATLAB and have been making good use of it, too.

Thanks for the replies.

---

### Post by sputnik on 2009-09-11
Another good site for examples (in R) is [The R graphical manual]("http://bm2.genes.nig.ac.jp/RGM2/package.php?clear=all")

Plotrix triangular plots can be found at [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/plotrix/man/triax.plot.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/plotrix/man/triax.plot.html"). This has the normal help text and some images to show the results.

For ade4 see [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/ade4/man/triangle.plot.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/ade4/man/triangle.plot.html")

for compositions see [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/compositions/man/plot.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/compositions/man/plot.html")

ternary in Zelig [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/Zelig/man/ternaryplot.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/Zelig/man/ternaryplot.html")

ternary in vcd [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/vcd/man/ternaryplot.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/vcd/man/ternaryplot.html")

tri in cwhmisc [http://bm2.genes.nig.ac.jp/RGM2/R_current/library/cwhmisc/man/tri.html]("http://bm2.genes.nig.ac.jp/RGM2/R_current/library/cwhmisc/man/tri.html")

---

### Post by epitaph on 2009-09-11
I had no idea there were so many different packages that supported ternary plotting in R.

Ugg, another thing that has to go on my list of things to learn...

Thanks a lot, I appreciate it.

---

