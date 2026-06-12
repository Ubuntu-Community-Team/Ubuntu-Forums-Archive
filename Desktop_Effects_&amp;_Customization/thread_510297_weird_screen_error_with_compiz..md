---
title: "weird screen error with compiz."
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by dashnak on 2007-07-26
Hello, I have a problem with compiz.
When I do compiz --replace, the top left quarter of my screen remains, and the other three quarters turn black.
Furthermore, the visible quarter has all the effects enabled and works perfectly fine. This happened after an update. I'm using treviño's packages.
Any ideas?

---

### Post by benx009 on 2007-07-26
what video card and video drivers are you using?

---

### Post by dashnak on 2007-07-27
I'm using ATI Xpress 1150. The drivers are the latest from ubuntu's official repos.... It worked at one time you know, 1 day later, I updated, and bam!

---

### Post by elenothar on 2007-07-27
i am also having this, however not on ubuntu (sorry, found this with google)
screenshot: [http://www.opsat.net/temp/compiz-uhoh.png](http://www.opsat.net/temp/compiz-uhoh.png)

it worked last week and not after a checkout today. i posted a bug on the compiz fusion tracker.
[http://bugs.opencompositing.org/show_bug.cgi?id=273](http://bugs.opencompositing.org/show_bug.cgi?id=273)

AMD Athlon XP 2400+ 2.0GHz
nVidia GeForce 6600GT OC 256MB, 100.14.09 Drivers.

---

### Post by elenothar on 2007-07-28
Fixed. Not really, it is just a bad option setting.

>   ------- Comment  #1 From Danny Baumann  2007-07-28 12:25:13  [reply] -------

You have to enable the option "Detect Outputs" (CCSM -> General Options ->
Display Settings).

---

### Post by dashnak on 2007-07-28
Hey!! This is great!! Thanks!!

---

