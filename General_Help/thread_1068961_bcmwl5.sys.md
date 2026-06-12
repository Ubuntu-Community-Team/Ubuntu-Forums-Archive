---
title: "bcmwl5.sys"
date: 2009-02-13
forum: General Help
---

### Post by lms5yc13 on 2009-02-13
Does anyone have a link to where I can download the bcmwl5.sys file? I can't seem to find this file. Thanks

---

### Post by Kevbert on 2009-02-13
> **lms5yc13 said:**
> Does anyone have a link to where I can download the bcmwl5.sys file? I can't seem to find this file. Thanks

Looks like your trying to install a Broadcom wireless card. What version of Ubuntu do you have and what chipset is it ? You can get the chipset with
```
lspci
```
under Applications-Accessories-Terminal. There should be a line with your Broadcom chipset (eg bcm4306) and the revision.

---

### Post by lms5yc13 on 2009-02-15
I have the version 8.10 and the Chipset is the BCM4318 card. I tried the b43xcutter driver but when I connected it was very slow and I know the network isn't slow at all. My roommate connects with 100% signal strength and runs at like 40mb/s. For some reason when I connect the speed is 11mb/s - that's when I am able to connect too.

---

### Post by Kevbert on 2009-02-17
Have you seen this [[COLOR="Red"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560") ?
An alternate method is [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

---

### Post by theozzlives on 2009-02-17
Go to Google and search for bcmwl5.sys.

---

