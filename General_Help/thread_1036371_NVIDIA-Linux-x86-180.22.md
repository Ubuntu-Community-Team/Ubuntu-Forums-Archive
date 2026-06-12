---
title: "NVIDIA-Linux-x86-180.22"
date: 2009-01-10
forum: General Help
---

### Post by OffHand on 2009-01-10
Did anyone try the latest nvidia driver (NVIDIA-Linux-x86-180.22) yet? X fails to start on my machine. Fatal error: no screens found. .11 works perfectly. Nvidia 8600M GT

Anyone else having issues with this driver?

---

### Post by thomasbaker on 2009-01-10
I had the same problem this worked for me

[http://ubuntuforums.org/showthread.php?t=1035873&highlight=nvidia+driver+problems](http://ubuntuforums.org/showthread.php?t=1035873&highlight=nvidia+driver+problems)

---

### Post by pissedoffdude on 2009-01-10
It's working fine here. I've seen people with this issue on previous beta releases.  Looks like it has to do with the way it was installed.  Install it with the methods mentioned on this page and you should be good [http://ubuntuforums.org/showpost.php?p=3194822&postcount=1]("http://ubuntuforums.org/showpost.php?p=3194822&postcount=1")

---

### Post by OffHand on 2009-01-10
Thanks for your replies guys.... appreciated. I don't think I can be arsed to go through all of that 'cause all the previous drivers worked fine. I think it's a bug with the driver.

---

### Post by hotweiss on 2009-01-10
Try rebuilding your xorg, that fixed the problem for me:

sudo dpkg-reconfigure xserver-xorg

(you have to boot in to terminal via recovery mode)

---

### Post by OffHand on 2009-02-15
For anyone experiencing the same problem... I was able to solve it by:
```
sudo rm /lib/modules/2.6.27-11-generic/updates/dkms/nvidia.ko
```

---

