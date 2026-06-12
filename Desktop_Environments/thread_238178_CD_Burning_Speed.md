---
title: "CD Burning Speed"
date: 2006-08-17
forum: Desktop Environments
---

### Post by jhuff on 2006-08-17
I typically burn CDs using Nautilus CD/DVD Creator.  I am no longer given the option to pick a write speed.  It is set to "maximum possible" and can not be changed.  Can someone tell me how to get this option working again?

---

### Post by jhuff on 2006-08-22
Does anyone have any ideas on how to get this option working again?

---

### Post by missmoondog on 2006-08-22
edit:
oops! clicked wrong reply to!!

---

### Post by Dubbayoo on 2006-08-22
gconf-editor apps/nautilus cd burner

---

### Post by jhuff on 2006-08-23
I tried the gconf-editor and the speed was set to 0.  I changed it to 24 but it still does not allow you to select a speed.

---

### Post by drivel on 2006-08-23
> **Dubbayoo said:**
> gconf-editor apps/nautilus cd burner

nothing happen....

---

### Post by jhuff on 2006-08-23
Nothing, I have tried sudo as well. The speed changes in gconf-editor, but when I go to burn a disk the speed is still set to "maximum possible" and can not be changed. ](*,)

---

### Post by Carrot06 on 2006-11-22
Anyone work out how to fix this?. I have the same problem with my Lite-On LTR-52327S CD Burner, but don't have the same problem with my Pioneer DVR-107D DVD Burner. I have tried setting the write speed in gconf-editor but that only set the Pioneer drive speed not the Lite-On drive (which stayed at Maximum Possible).

---

### Post by digbysellers on 2007-03-26
It seems to be working in (tried K3b so far) now with the 6.06 update to 2.6.28! 
Can burn an 8X DVD-R video disc @ 4X on Sony DRU710A with latest firmware...

---

