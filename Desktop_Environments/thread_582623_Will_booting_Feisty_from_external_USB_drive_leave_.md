---
title: "Will booting Feisty from external USB drive leave internal drive untouched?"
date: 2007-10-20
forum: Desktop Environments
---

### Post by john3333 on 2007-10-20
I successfully installed 7.04 to an external USB drive, after first disconnecting my internal hard drive, to make sure it would remain untouched. (Computer is a Toshiba Satellite AH9, Core 2Duo, 2GB RAM, with Vista on internal drive).
I can boot and run Feisty with no problem from this external USB drive with my internal drive disconnected. 
So far, I have been afraid to try booting from the USB drive with the internal drive connected, for fear it will write something to this drive, or its MBR, or otherwise alter it.
When I installed Feisty to the external USB, I did not give it any instructions about loading GRUB, so I don’t know if GRUB is installed somewhere on it or not.
My question is: Does anyone know for sure if I can safely boot Feisty from my external USB drive while I have the internal drive connected, without any danger of this making any changes to my internal drive which has Vista on it????

---

### Post by Ceemee on 2007-10-20
I do this all the time with no issues at all.  I have ACCESS to the internal drive, so I could change something there if I wish, however, Its never changed my MBR or anything.

I disconnected my internal drive during installation, to ensure that my MBR on that drive stayed un-touched.

But now, I merely plug in my USB drive for Ubuntu, unplug for XP, and I've never had any problems at all.

Grub is installed, but is probably just showing you a screen like "Press _ key to view boot options".....5, 4, 3, 2, 1..  Ubuntu loading screen.  Its grub, but less visible because its only job is to load the only OS it knows of on the system, Ubuntu.

and make sure that your BIOS is set to boot in the correct order.  (I recommend this)

CD-Rom
USB
>>> Network if you will ever boot off of a network, otherwise HDD (if you dont know, use HDD.)
>>> HDD if you chose Network Above.

The reason for this is that your system will boot the first bootable device it comes to -

so if your list looks like this - 

CD-Rom
HDD
USB
Netowrk

Your system will try to boot cd-rom first, if it doenst find anything, then it will try HDD, rinse and repeat.  Where you could have an issue is if you havent changed this, your system was never finding anything on your HDD before (you where disconnecting it).  But it will always find something there now.  so even if you plugged in your USB drive in this scenario, you would always boot Windows, without ever having the option for Ubuntu.

Make sure USB is above HDD, but below CD-Rom (so you can boot off other CD's if needed)

---

### Post by john3333 on 2007-10-21
Thanks for the reassurance and extra advice, Ceemee.

---

