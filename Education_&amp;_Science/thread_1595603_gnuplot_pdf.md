---
title: "gnuplot pdf"
date: 2010-10-13
forum: Education &amp; Science
---

### Post by ssam on 2010-10-13
a quick note for anyone trying to get gnuplot to give you a pdf and seeing
```

gnuplot> set terminal pdf
                      ^
         line 0: unknown or ambiguous terminal type; type just 'set terminal' for a list
```

this is because gnuplot before version 4.4 (lucid/10.04 has 4.2) used pdflib to make pdfs, which is not free software. since version 4.4 it uses cairo to draw pdfs, which is free.

if you can't upgrade to maverick/10.10 then the easiest thing to do is to install the gnuplot packages from maverick. get them from [https://launchpad.net/ubuntu/+source/gnuplot]("https://launchpad.net/ubuntu/+source/gnuplot") . you need the gnumplot-nox and gnuplot-x11 packages. eg
[https://launchpad.net/ubuntu/+archive/primary/+files/gnuplot-nox_4.4.0-1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/gnuplot-nox_4.4.0-1_i386.deb")
and
[https://launchpad.net/ubuntu/+archive/primary/+files/gnuplot-x11_4.4.0-1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/gnuplot-x11_4.4.0-1_i386.deb")

---

### Post by stats on 2011-10-02
Thank you so much for this!

---

