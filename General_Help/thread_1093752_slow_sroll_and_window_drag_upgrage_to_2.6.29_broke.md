---
title: "slow sroll and window drag: upgrage to 2.6.29 broke fglrx?"
date: 2009-03-11
forum: General Help
---

### Post by vforgetta on 2009-03-11
Hi all,

I recently upgraded to kernel 2.6.29-rc7 in order to get support for my Microsoft VX-1000 webcam.  The upgrade now broke support for the fglrx driver i.e. I can no longer activate it using the System > Administration > Hardware Drivers dialog.  As a result (I think), scrolling is slowed down in most programs (Firefox, Gedit), and window drags are also quite slow.  Is there a fix for this? Is there a suitable alternative video driver I can use? I'm not interested in getting 3d acceleration working, or compiz.  I just want smooth scrolling and dragging back!

Hardware:  Del Studio XPS, Core 2 Quad Q8200, 6Gb ram, ATI HD3450. 1TB RAID.


Thanks.

Vince

---

### Post by vforgetta on 2009-03-11
SOLVED! Just reverted to the open-source driver as specified here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Worked great. One more reason to endorse open-source!

Vince

---

### Post by MaxIBoy on 2009-03-11
FGLRX is a driver that you must compile into the kernel, so yes, when you update the kernel, you need to reinstall the driver.

---

