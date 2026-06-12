---
title: "Problem: &quot;Failed to load splash image...&quot;"
date: 2007-07-03
forum: Desktop Environments
---

### Post by Thistlewait on 2007-07-03
I've got Ubuntu and KDE running just about the way I want them. But for some reason when I resart my system, before it gets to the OS Boot selection screen, I'm getting the following message:

"Failed to load splash image (,1) /boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz" and then hangs until  I press "Enter". At which  time it will display the  OS selection screen and then do a normal boot.

I've looked in the directory mentioned and found the "KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz" archive, opened it and looked at the image. It  seems  to be just fine. Why is KUBUNTU telling me that it can't load the image?

This is not a major problem, but it is a bit of a nag. Can someone tell me  what's happening or how to fix this?

TIA,
thistlewait

---

### Post by mikeklemz on 2007-07-16
I am also experiencing this problem.

---

### Post by skibum1981 on 2007-08-13
I also have the same problem.  In terminal, I tried regenerating menu.lst by running ```
sudo update-grub
``` and the splash portion of my output was my output was 
```
Searching for splash image ... found: (sdb1,0)/boot/grub/blubuntu.xpm.gz 
```

Still have the same problem; still have the image loaded in the menu.lst.  What the devil?!

---

### Post by Gremlinzzz on 2007-08-13
if your talking grub background you can use this program to change it .or
maybe reinstall the original .
[http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml](http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml)

---

