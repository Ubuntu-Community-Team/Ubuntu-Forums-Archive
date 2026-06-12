---
title: "GaussSum cannot call gnuplot"
date: 2006-10-23
forum: Education &amp; Science
---

### Post by MacKris on 2006-10-23
Hi all,

I've just installed GaussSum-1.0.5 along with gnuplot-4.0 on my ibook, and got to them to work separately, but am having trouble creating plots from within GaussSum.

The error message I get in my terminal window when I request "SCF.py" from the GaussSum GUI is:

```
sh: line 1: /Users/kristine/Desktop/GaussSum-1.0.5/gnuplot400/bin/wgnuplot.exe: No such file or directory
```

The problem I think is in the GaussSum.py script. At the moment, it has the wrong settings directory for calling gnuplot (gnuplot is installed in /usr/local/bin). 

Can anyone advise me on how to change those settings in python?

Thanks!

MacKris :KS

---

### Post by LaserJock on 2006-10-23
GaussSum 1.0.5 isn't in Ubuntu so I'm assuming you got it from the GaussSum website. It also would appear that you are using the Windows .zip file. I think you will find that if you install GaussSum from the Ubuntu it will work better for you.

On second thought, it looks more like you are running it in OS X. In that case I'd grab the Linux .tar.gz file from the GaussSum website. If it still can't find Gnuplot, go into File->Settings and change the path to gnuplot.

-LaserJock

---

### Post by MacKris on 2006-10-23
Thanks! I've gone to File>Settings and changed the directory and it works now! I completely overlooked that in the GaussSum gui :redface:

---

