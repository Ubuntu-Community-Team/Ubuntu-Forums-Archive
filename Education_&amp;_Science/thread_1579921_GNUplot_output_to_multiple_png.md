---
title: "GNUplot output to multiple png"
date: 2010-09-22
forum: Education &amp; Science
---

### Post by owenlinx on 2010-09-22
Hello,
   I am trying to plot the output of an antenna designed with the program yagiuda. It produces a file 'antennaname'.glog I have no problem running the command ```
gnuplot antennaname.glog
```
that outputs the data in a nice plot. My problem is that I am running plots across 200Mhz with a data point at every 1Mhz.

   What I would like to do is have gnuplot run its course and put the plot in png's so I can make an animation using imagemagick.

Thanks for any help.

---

### Post by lordhaworth on 2010-09-27
Hi,

you will have to write a script for it to use. Everything that you need is at the following page

[http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html](http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html)

---

