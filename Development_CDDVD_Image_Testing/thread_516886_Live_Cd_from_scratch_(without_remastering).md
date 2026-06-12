---
title: "Live Cd from scratch (without remastering)"
date: 2007-08-03
forum: Development CD/DVD Image Testing
---

### Post by az on 2007-08-03
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I started a wiki page which documents the procedure for making an Ubuntu remix from scratch.

It works for my purposes, which is making a data recovery toolikt ([http://rescubuntu.info/](http://rescubuntu.info/)).  In this case, it is easier and more flexible to start from scratch than to remaster an existing cd.  Especially when the end-product must be console-only and run in very little ram.

The page needs work, so if anyone is interested jump in.

The page does not describe how to make the remixed live system use any graphical boot and the ubiquity installer is not tested out.  Yet.

---

### Post by cetinf on 2007-08-06
I believe you started from the right point. 

Just a question, in case you may answer: Trying to build a custom and minimal CD, I started with modifying filesystem.squashfs-desktop, however ubiquity seems to install many X-related packages I do not need. The chrooted filesystem I work on is around 400 Mb, however ubiquity installs circa 900 Mb of file to the target directory.

I can later on delete the packages I do not need, but it's really too much of work: The number of packages I want to install is around 150, and ubuntu installs 350 (many of which consists of X packages).

Any hints?

---

### Post by az on 2007-08-06
> **cetinf said:**
> 
Any hints?

Well, Ubiquity only has two frontends, currently.  One is for Gnome (GTK, actually, which is what Xubuntu is based on) and the other for KDE.  If there were a console frontend to ubiquity, that would satisfy your needs.

---

