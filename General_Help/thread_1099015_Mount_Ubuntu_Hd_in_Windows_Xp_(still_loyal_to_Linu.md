---
title: "Mount Ubuntu Hd in Windows Xp (still loyal to Linux)"
date: 2009-03-17
forum: General Help
---

### Post by sushemsu on 2009-03-17
Okay even though I'm a Hardcore Linux Lover there are just some apps that are windows only that I need to run.. With this being said there are media files that I have put onto my Ubuntu Hard drive, that I need to access on windows... I cannot seem to mount it via disk management... how can i access the files without having to use another bit of hardware (IE PC/usbdrive)?

---

### Post by taurus on 2009-03-17
Windows will not recognize and read ext2/ext3 filesystem.  Therefore, you cannot access your files on Ubuntu.  However, fs-driver would let you do just that.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by AboveTheLogic on 2009-03-17
Here is another possible solution:
[http://en.wikipedia.org/wiki/Explore2fs](http://en.wikipedia.org/wiki/Explore2fs)

---

### Post by sushemsu on 2009-03-17
Thank you Both Very much : D

---

### Post by gladson1976 on 2009-03-27
hi all

try the Ext2Fsd driver at
[http://ext2fsd.sourceforge.net](http://ext2fsd.sourceforge.net)
it works with both read and write support.

---

