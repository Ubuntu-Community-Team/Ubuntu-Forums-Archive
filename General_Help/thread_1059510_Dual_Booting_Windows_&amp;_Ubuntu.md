---
title: "Dual Booting Windows &amp; Ubuntu"
date: 2009-02-03
forum: General Help
---

### Post by SCGhst1 on 2009-02-03
Hey again everyone:)

I was wondering if someone could point me in the right direction to installing ubuntu on the same harddrive as windows but i wanted to be able to do either A) or B)

A.) I wanted to keep the windows boot loader and load ubuntu from the Windows boot loader but still have Windows be the first boot as
      1. Windows
      2. Ubuntu

OR

B.) Install GRUB or LiLo and have Windows be the first boot OS on the boot loader menu instead of auto-booting into Ubuntu


Thank you for the help:)

---

### Post by edwardTheGreat on 2009-02-03
This is a good resource for option a)

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

---

### Post by gradysghost on 2009-02-03
The first thing I want to say is that the best way to do this is to

[LIST=1]
[*]Back up all of your data
[*]Reinstall Windows, and create a partition for Windows, leaving at least 4 gigs unpartitioned
[*]Install Ubuntu in that extra partition
[*]Move your data back
[/LIST]

However, Ubuntu does provide the option of decreasing a partition's size during installation.  I've done it once to great success, but I don't know how much stuff you have on your Windows partition and how fragmented and spread out it is.  Resizing partitions can be tricky and dangerous, and I personally don't recommend it.  Either way, back all of your stuff up first.

After installing Ubuntu, do the following:

[LIST=1]
[*]Boot into Ubuntu
[*]Press Alt+F2 from the desktop
[*]Type "gksudo gedit" into the box, without the quotes, and press Enter
[*]Type your password and press Enter
[*]Open the file /boot/grub/menu.lst
[*]Scroll all the way to the bottom of the text file and count the number of boot options, taking note of which number falls on your Windows partition
[*]Scroll back to the top and look for the line that says "default 0"
[*]Change the number to whatever number you counted Windows at
[*]Save the file
[/LIST]

When you boot, GRUB will automatically choose Windows and give you a few seconds to change your mind (you can just use the arrow keys to change, then press Enter).

Hope this helps.  It's really quite simple.  I don't know how familiar you are with Linux in general, but most operations can be controlled completely through simple configuration files like this one.

---

### Post by 1ronlung on 2009-02-03
[http://ubuntuforums.org/showthread.php?t=1057367](http://ubuntuforums.org/showthread.php?t=1057367)

Tips on exactly how to do it.  Was a few threads down ;-)

---

### Post by SCGhst1 on 2009-02-03
So if i keep my windows partition (hda1) as my first partition on the hard drive, then GRUB should boot it first?

---

### Post by SCGhst1 on 2009-02-03
Thank you so much 1RonLung! that helped me tremendously! And thanks to Guriman who originally posted it. You guys are always great! thanks :)

---

### Post by cph05a on 2009-02-03
.

---

