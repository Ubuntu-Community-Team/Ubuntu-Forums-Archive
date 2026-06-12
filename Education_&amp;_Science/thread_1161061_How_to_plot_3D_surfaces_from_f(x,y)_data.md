---
title: "How to plot 3D surfaces from f(x,y) data"
date: 2009-05-16
forum: Education &amp; Science
---

### Post by leandromartinez98 on 2009-05-16
I'm trying to plot a 3D surface from f(x,y) data, such as:

```

 x              y               f(x,y)
0.0            0.8               10.2
0.3            1.2               0.89
1.1            2.6               3.50
3.6            1.4               0.56
...

```


This should be the most natural way of providing data for ploting
a surface in 3D. However, most packages (all I've tried) do not 
use this kind of input for ploting surfaces, because they seem
to require a regularly spaced grid.

Does anyone knows a package that is able to plot a surface using
the data provided as above?

Thanks.

---

### Post by jbrefort on 2009-05-17
gnumeric in latest development versions (1.9.x) does something like what you want. There is a debian package for sid, but no ubuntu package for now (only 1.8.4) which makes sense, so you'll have to compile it yourself along with the appropriate libgsf and goffice versions if you want to try it.

---

### Post by aJayRoo on 2009-05-17
You can do this with gnuplot.
```
set dgrid3d
splot "yourdatafile" using 1:2:3 with lines
```
This grids the data for plotting. You can use the help command in gnuplot, eg.:```
help dgrid3d
```to find out more about what this does and decide if this is what you need.

Hope that helps.

---

### Post by leandromartinez98 on 2009-05-17
Thanks aJayRoo, that is exactly what I need. The only drawback is
that I'm not very familiar with gnuplot and so my control over the
graphic looks is too rusty. Is there a way to export the grid
to a file in order that I can open the matrix on, lets say,
qtiplot, so I can control the looks from there?

---

### Post by aJayRoo on 2009-05-18
I'm not sure that you can do that. It would probably best to use some package that you are familiar with (octave/matlab etc.) to do the interpolation on to a regular grid and save that to an output file.  I think most data anlysis packages will have the capability to do this. Then you are free to use whatever software you want to plot it.

---

### Post by hubie on 2009-05-19
I like to use R and the package [scatterplot3d]("cran.r-project.org/web/packages/scatterplot3d/vignettes/s3d.pdf").  It will take data in your data format.  Check out the examples in the pdf to see what it can do and how to use it.  You'll need to add the package to your default R installation, but that is easy to do from within R.  

The other R package you can use is [cloud]("http://astrostatistics.psu.edu/datasets/R/html/lattice/html/cloud.html"), but I've never tried that one.

---

