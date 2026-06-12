---
title: "Driver Paradox"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by (-NINJ4-) on 2007-09-17
I recently reinstalled ubuntu on my Dell Inspiron 530 using the disc provided for me with my dell, only to find that I needed specific drivers to use my network card to connect to my lan.  So I downloaded them from the dell website on my laptop, moved them via flashdrive, and attempted to install them only to find out that I need the newer kernel version or else I can't install the drivers.  

So to summarize, to update the kernel I need to get on the internet, and to get on the internet I need to update the kernel.

Is there any way to either update the kernel manually or find the old dell drivers?
Any help is greatly appreciated.

---

### Post by gbrainin on 2007-09-17
If you did not delete it, the computer came with a restore partition which will put the entire hard drive back to factory settings (including the necessary drivers and kernel upgrades).  You should be able to access this through the grub menu while booting.

If that fails, Dell has just last week released a modified CD that includes the necessary drivers but does not include some programs (OpenOffice, etc.) to make the necessary space.  There is also a modified DVD that has both.  You can download these by linking to [http://linux.dell.com/wiki/index.php/Ubuntu_7.04]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04").

There is also a page on that wiki which lists all the changes made to the standard Feisty install, and you could recreate those manually if necessary.

---

### Post by (-NINJ4-) on 2007-09-18
Thank you very much, the remastered CD worked perfectly. :)

---

