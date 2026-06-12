---
title: "Cannot load Xubuntu"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pjomara on 2010-05-03
I cannot seem to load Xubuntu onto Dell Latitude laptop.  When ever I try, the installer freezes at 15% (Detecting file systems).

The computer specs are:
Dell Latitude 110L, Intel Celeron 2.4 GHz processor, 256 Mb RAM

I get the same results with versions 8.04 LTS, 9.04, and 9.10.

I tried to load Xubuntu onto several other identical laptops with the same result.

When attempting to load ver. 10.04, I don't even get to 15%.  After clicking install Xubuntu, the CD spins for several minutes and then stops, black screen, nothing.  I've verified the checksum and loaded 10.04 onto other computers (desktops)

Any and all help is appreciated.

---

### Post by gordintoronto on 2010-05-03
Your computer almost certainly uses some of the memory for video, which means it doesn't have enough system memory to meet the minimum requirements.

See: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

For the current release, the memory requirement has grown to 384 MB:
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)
(It's right at the bottom of the page.)

There might be a BIOS setting to reduce the amount of memory used for video, enough to install the 8.04 "alternate CD."

Or you might be happier with another version of Linux, such as Puppy Linux.

---

### Post by pjomara on 2010-05-03
Thanks for the information.  Currently I run ZenWalk Linux on the laptops.  It runs fine except for that the wireless will not work.

Thanks again.

---

