---
title: "wxmaxima"
date: 2006-08-05
forum: Desktop Environments
---

### Post by calvinthomas on 2006-08-05
Can anyone give me step by step instructions of how to get wxmaxima working in Ubuntu 6.06? It seems that it is possible but I don't really understand how.

Calv

---

### Post by calvinthomas on 2006-08-29
bump from a long time ago!

Calv

---

### Post by jpkotta on 2006-08-31
Just got it working.  Let me know if you have trouble, and I'll update the instructions.

[https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima)

---

### Post by calvinthomas on 2006-09-01
Thanks for that! Its great, I can confirm it works with the very latest version of Maxima and the latest version of WxMaxima also!

Calv

---

### Post by klytu on 2006-09-02
> **jpkotta said:**
> Just got it working.  Let me know if you have trouble, and I'll update the instructions.

[https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima)

I found the HowTo to be very helpful! I recompiled maxima as described, then I installed wxmaxima from the repositories and it worked fine. Only adjustment I had to make was that I had to install also gnuplot-x11 in order for plotting to work. (I think wxmaxima from the repositories installs gnuplot-nox.) I had some difficulty when I tried recompiling wxMaxima. Maybe I missed installing a dependency? Anyway, in the end I didn't need to.

---

### Post by UltraMathMan on 2006-09-12
Thanks for the HowTo, complied and installed maxima but ran into trouble too with wxMaxima (xml2 I think?) anyway installed it from the repositories along with gnuplot-x11 and it works beautifuly.

---

### Post by UltraMathMan on 2006-09-16
Anyone know how to plot implicit bivariate functions, vector functions, and space curves with this?

---

### Post by silentb on 2006-09-16
Look here:

[http://t16web.lanl.gov/Kawano/gnuplot/implicit/solve-e.html](http://t16web.lanl.gov/Kawano/gnuplot/implicit/solve-e.html)

It's a guide for GNUPlot, but the way is the same in Maxima.

---

### Post by UltraMathMan on 2006-09-16
Thanks, I'll check it out! :)

---

### Post by villindesign on 2006-09-21
will this solution break or interfer with the maxima session inside of TeXmacs?

---

