---
title: "always sends wrong paper size?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by kddoj on 2006-08-09
Hi all

I've installed Ubuntu 6.06 which installed fine. I've managed to get our network printer detected and installed (hp laserjet 4), but no matter how I set the paper size (I want letter size), I always get the "load A4" message on the printer. I had tried the latest version of Suse as well and got the same error, is this a problem on the machine sharing the printer or something with the print service in Ubuntu or Suse?

The printer is shared on a machine running win2k server and all the other windows pc's in the shop print to it fine, any suggestions would be welcome...

thanks in advance!


Kris

---

### Post by kddoj on 2006-08-09
nm, found the solution in on of the "similar threads" that popped up after I posted the message...:-)



Kris

---

### Post by PcPixel on 2006-08-09
What thread was the answer in?

---

### Post by zitch on 2006-08-09
Most likely this one: [http://www.ubuntuforums.org/showthread.php?t=4235](http://www.ubuntuforums.org/showthread.php?t=4235)

The fix is to change the value in /etc/papersize to letter then reinstall the printers.

---

