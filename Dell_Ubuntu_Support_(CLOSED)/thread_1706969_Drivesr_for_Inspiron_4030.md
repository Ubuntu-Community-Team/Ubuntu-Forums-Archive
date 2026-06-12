---
title: "Drivesr for Inspiron 4030"
date: 2011-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KeiNivky on 2011-03-14
The desktop edition of Ubuntu installed all my hardware perfectly, but now I am using server edition and both sound and wireless aren't working. How can I install them?

info from lspci:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio Controller (rev 05)

12:00.0 Network controller: Broadcom Corporation BCDM4313 803.11b/g LP-PHY (rev 01)

---

### Post by mörgæs on 2011-03-15
If you want server capabilities and sound and wirefree then I guess it is best to install the desktop edition first. After that you can install  LAMP (assuming this is what you want) with the command

```
sudo apt-get install lamp-server^
```Remember the hat at the end of the line.

---

### Post by KeiNivky on 2011-03-16
Actually I was using server edition because I don't want gnome. But I already switched back to Desktop edition. Now the problem is that the sound doesn't work when I am out of gnome.

---

### Post by mörgæs on 2011-03-17
Then it might be worthwhile to look in this forum:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

