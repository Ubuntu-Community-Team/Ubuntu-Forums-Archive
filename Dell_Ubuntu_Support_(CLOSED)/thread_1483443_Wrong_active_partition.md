---
title: "Wrong active partition"
date: 2010-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bubblehead74 on 2010-05-14
I tried to install Ubuntu on a Dell notebook from a USB flash drive that I prepared using Unetbootin. When I booted from USB I got "no bootable partition in table". I then activated dev/sda1 using fdisk, but that was a mistake, because now Dell starts some Tests when start the computer, and I cannot boot up Ubuntu at all. Please tell me I can fix this. There is no CD drive, but I can plug the HDD into my desktop, if necessary.

Actually, when I think of it, it must be Unetbootin bug. I should be able to boot from the flash drive.

---

### Post by C.S.Cameron on 2010-05-14
Sometimes the startup disk creator that comes with Ubuntu works better than UNetbootin.
It is best to check the MD5SUM of the iso before making a bootable thumbdrive.
One little error can mess things up.

---

### Post by gbrainin on 2010-05-14
/dev/sda is the hard drive in the computer, not the flash drive.  You basically made the Dell hardware test partition the bootable partition in your drive.

If you boot off of a live CD, you should be able to fix this using fdisk, or gparted.

---

### Post by bubblehead74 on 2010-05-15
Thanks for your answers. When I used Startup Disk Creator with the same iso and the same flash drive, it became bootable and I installed 10.04 without any problem. This leads me to believe that the problem in my case was caused by UNetbootin.

---

