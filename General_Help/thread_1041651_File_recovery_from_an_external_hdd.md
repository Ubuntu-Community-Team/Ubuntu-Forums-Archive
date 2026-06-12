---
title: "File recovery from an external hdd?"
date: 2009-01-16
forum: General Help
---

### Post by JDuc on 2009-01-16
Some how, one of my external drives has gone loopy.  When I plug it into my Windows laptop, and try to access it, it tells me that the drive is not formatted and asks if I would like to format it.  This is strange because the last time I used it (about 2 weeks ago) I was able to access all of the files on it fine.

Now, it's showing up as a RAW type file system.

Before I consider it a total loss, I want to see if there's any chance of recovering the files off of it (it was my back up drive).

Is there a suggested program for use in Ubuntu?

---

### Post by taurus on 2009-01-16
Maybe TestDisk can do something about it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by JDuc on 2009-01-16
Thanks for providing the suggestion.

Reading the instructions, I saw this:

> 
**  Linux and 48-bit LBA **

 Linux kernels since at least 2.4.19 have been able to access Large disks (drives over 137 GB using 48-bit LBA); and some earlier kernels, such as Red Hat 7.3's 2.4.18-x, were patched, so check the specific features of your install to know for sure. Linux kernels 2.2.x and older are limited to only 65,535 cylinders.


I'm trying to access a 500 GB external hard drive.  The thing is, it's not even showing up under Computer in Linux, but it's showing up under Device Manager (downloaded through Synaptic).


Is this normal for Linux considering the fact that the drive is showing up as a RAW file system type in Windows?

---

