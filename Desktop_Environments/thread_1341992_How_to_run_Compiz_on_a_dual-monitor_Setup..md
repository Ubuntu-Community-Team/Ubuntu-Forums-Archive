---
title: "How to run Compiz on a dual-monitor Setup."
date: 2009-11-30
forum: Desktop Environments
---

### Post by Masquerade on 2009-11-30
Hi everyone
(read original thread [here]("http://ubuntuforums.org/showthread.php?p=8408218"))
I have a HP Compaq Labtop With a 1280x1024 screen attached.
the graphics card is 
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```.

Everything works nice when using metacity. But, when i want to run compiz, i get the following output:
```
compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2304x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity
```

The script compiz-check says
```
Error: Your current resolution is too high to run Compiz.

Would you like to know more? (Y/n) y

Your resolution is 2304x1024 but the maximum 3D texture size that your
graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
on this setup. You have to decrease the resolution first (in case you are
using a dual-head setup, try disabling one monitor and run the script again). 
```

When i change the second (attached) screen's resolution from 1280x1024 to 1024x768, compiz-check says that my computer might be able to run compiz, but when runnning compiz --replace, it just freezes and deforms my screen.

---

### Post by Masquerade on 2009-12-03
mibmib?

---

