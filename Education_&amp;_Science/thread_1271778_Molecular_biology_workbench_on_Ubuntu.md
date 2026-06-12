---
title: "Molecular biology workbench on Ubuntu"
date: 2009-09-21
forum: Education &amp; Science
---

### Post by bubblehead74 on 2009-09-21
I stumbled upon a free molecular biology software from CLC bio. All their software is cross-platform, written in Java. However, only CLC bio Sequence Viewer is available free of charge:

[http://www.clcbio.com/index.php?id=28](http://www.clcbio.com/index.php?id=28)

Although the website states that Redhat/Suse is required, their sh package can be installed fine on Ubuntu. After you download the package, change permissions to allow executing the file. Then double-click it and run in terminal.

---

### Post by bubblehead74 on 2009-10-01
OK. Forget about this software. It is only a viewer with no functionality. It is useless. What was I thinking.

---

### Post by Miche on 2009-10-06
.. and the license costs thousands ...
the viewer is no better than APE. Any suggestion on how to use Ubuntu for sequences analysis? Tnx!

Miche

---

### Post by Warthaug on 2009-10-08
Depends on what kind of analysis you're trying to do.

A lot of basic stuff can be done using [Bioedit]("http://www.mbio.ncsu.edu/BioEdit/bioedit.html"), run under wine.

There is also the [EMBOSS suite]("http://emboss.sourceforge.net/"), which is very powerful, but command-line driven and has a real steep learning curve.  There are some GUI's for it (links on the homepage) that supposedly make it easier, but I've yet to get one to work.

Bryan

---

### Post by Goatrancer on 2011-03-09
CLC viewer (converted to DEB using Alien) was working for me for a couple of weeks, then it started acting flaky (sometimes the window would disappear after startup), now it doesnt work at all (program starts up, then window and program icon disappear).

---

### Post by mr chip on 2011-03-11
Depending on what you want, [Ugene]("http://ugene.unipro.ru/") or [Mesquite]("http://mesquiteproject.org/mesquite/mesquite.html") might be useful for sequence analysis.  I was looking for something to help assemble and manage large sequence matrices for phylogentic inference, and ended up using these two most.

---

