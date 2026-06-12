---
title: "How to make USB bootable?"
date: 2008-06-30
forum: Debian
---

### Post by skymera on 2008-06-30
Hi

Im trying to install Debian Lenny and kinda run out of CDs..

Ive had my USB boot before but now it won't =\

I dont know if it's my files or the USB itself.

I used the HP format utility to make it bootable, and also grabbed boot.img from Debian site for usb etc.

Anyone have experience?

@not sure if this is in right section.

---

### Post by Lord Xeb on 2008-06-30
easy as pie, here: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by p_quarles on 2008-06-30
Moved to the Debian section. 

It's very easy if you have a CD: just install onto the pen drive and make sure the boot flag is on. I believe the procedure is a little more elaborate if you're trying to boot a CD image from a USB drive.

---

### Post by skymera on 2008-06-30
I extracted the ISO and placed the files on my USB and run syslinux like i read.

However it still wont boot!
I'll just have to wait for a CD.. or invest in a CD-RW xD

---

### Post by dptxp on 2008-07-01
If you have a grub it should be possible to do a "fromiso" installation first, then boot with "fromiso" and install.

I have done it with sidux (no CD/DVD drive needed if you can copy the iso or download it).

---

### Post by atomkarinca on 2008-07-01
Have you tried [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html")? It should support Lenny.

---

