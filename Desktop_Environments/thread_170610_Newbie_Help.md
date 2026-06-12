---
title: "Newbie Help"
date: 2006-05-04
forum: Desktop Environments
---

### Post by Yaholo on 2006-05-04
I am a bit new to the Linux/Ubuntu scene.  I have installed Ubuntu on a new laptop I have.  It is a Gateway MX3228 (similar to the NX200), is has an S3 integrated video card and a RealTek wireless card (g).  Right now, I cannot get it to recognize the card to let me use a wireless network, and it won't give me any widescreen resolution options.  

Does Ubuntu not support by hardware, or do I not know where to look?  If Ubuntu does not support my hardware, is there a Linux desktop that does?

---

### Post by Qrk on 2006-05-05
The graphics card may be tricky... I'm not familiar with S3. It does look like they provide drivers, though.

[http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580](http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580)


Your wireless card should work with ndiswrapper, read a how to here:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by Yaholo on 2006-05-05
Ok, I was able to find linux drivers for just about every piece of hardware that isn't working.... I have no idea how to install them.  Is there a good tutorial somewhere for installing drivers on linux?

---

### Post by conedude13 on 2006-05-05
There should be some README.txt files (or README.html) in the downloaded packages.  Just make a new folder, copy the package into the newly created folder, and extract.  You may even be able to navigate with the "explorer"-type window to the area and right-click on the package and see what your options are for extracting.  Then just look through the newly extracted data and find some sort of a readme file for installation instructions.  Or their might be instructions on the site that you did the download from.

---

