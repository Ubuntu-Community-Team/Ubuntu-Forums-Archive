---
title: "Compiz Fusion ATI x1600 Pro + AIGLX"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by streetsurfer on 2007-08-31
Hi,
I just reinstalled my system cos i screwed up my Gconf.

I was previously using flgrx + compiz fusion on my desktop but i noticed my laptop is using AIGLX (X300 Mobility) and it supports direct rendering.

All the previous posts on this question were back about 7 months so

Would anyone know if it is possible to run Compiz Fusion on an ATI x1600 pro with AIGLX and not the closed-source drivers??

---

### Post by kellemes on 2007-08-31
> **streetsurfer said:**
> Hi,
I just reinstalled my system cos i screwed up my Gconf.

I was previously using flgrx + compiz fusion on my desktop but i noticed my laptop is using AIGLX (X300 Mobility) and it supports direct rendering.

All the previous posts on this question were back about 7 months so

Would anyone know if it is possible to run Compiz Fusion on an ATI x1600 pro with AIGLX and not the closed-source drivers??

AIGLX will not work.. use XGL instead, and yes, you want fglrx.

---

### Post by Rupertronco on 2007-08-31
I think you're getting confused with the differences between fglrx XGL and AIGLX. fglrx is a driver for your card. You will need it regardless of if you chose AIGLX or XGL. XGL and AIGLX allow openGL graphics acceleration. The regular X server only allows a small amount of 3-d acceleration. You will need the fglrx driver for ATi and you will need XGL (as said above) in order to get the effects to work. In short, your driver (fglrx) allows XGL to do all of the cool stuff you're after on your desktop.

---

### Post by streetsurfer on 2007-08-31
so by enabling AIGLX i wont actually get direct rendering?

Im just wondering cos my T43 laptop has direct rendering (cant remember how) even though its running compiz fusion (x300 mobility) - AIGLX support for < x400 cards?

---

### Post by hidden_leaf_sasuke on 2007-09-01
you should install XGL, trust me. I use ATI too and using XGL is the answer. There is tutorial on how to install Ati+XGL on my blog [HERE]("http://http://ubuntu4life.blogspot.com/2007/08/installing-atixglcompiz-fusion.html").

---

### Post by ricardoec on 2007-09-01
your link is gone or yur page does not exist

---

### Post by kellemes on 2007-09-01
This should work..
[http://ubuntuforums.org/showthread.php?t=511166]("http://ubuntuforums.org/showthread.php?t=511166")

---

### Post by streetsurfer on 2007-09-01
thanks. I got compiz fusion via the repositories now :D
Would anyone know if there is a way to get the s-video out working??

Would be nice to watch movies on the much bigger TV.

---

### Post by khaoss on 2007-10-15
> **ricardoec said:**
> your link is gone or yur page does not exist

Check the url is bad typed, the reasl URL is :lolflag:[THIS!!!]("http://ubuntu4life.blogspot.com/2007/08/installing-atixglcompiz-fusion.html")

---

