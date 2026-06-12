---
title: "Interpolating Between Data points"
date: 2009-06-28
forum: Education &amp; Science
---

### Post by mdshaver on 2009-06-28
I am using QtiPlot 0.9.7 in Linux to plot input-output functions. It has worked well so far but I need to figure out how to interpolate between two discrete data points so that I can figure out numerical information between two measured data points. I thought the "interpolate" function would do the trick but I it only generates a curve but no data points. Is there any other software with a GUI where I can easily do this (e.g., Gnumeric, RLPlot, OpenOffice Spread, Grace?) Any help would be greatly appreciated.

Thanks in advance!

Mark

---

### Post by gunksta on 2009-06-29
Most any apreadsheet program should be able to do this.

---

### Post by jbrefort on 2009-07-03
gnumeric has an interpolation function supporting both linear and cubic spline interpolation (and more).

---

### Post by hzambran_cl on 2009-07-08
**R** ([http://www.r-project.org/]("http://www.r-project.org/")) has two functions that can be useful for you:

1) spline: [http://stat.ethz.ch/R-manual/R-patched/library/stats/html/smooth.spline.html]("http://stat.ethz.ch/R-manual/R-patched/library/stats/html/smooth.spline.html")

2) loess: [http://research.stowers-institute.org/efg/R/Statistics/loess.htm]("http://research.stowers-institute.org/efg/R/Statistics/loess.htm")

---

