---
title: "Unable to install on 9200c"
date: 2007-08-12
forum: Dell  Ubuntu Support
---

### Post by nedrick on 2007-08-12
Hi,

No matter what I try I cannot install on a partition on my 9200c. Ubuntu, Kubuntu, alternate cd, etc etc. 

I found another post suggsting 'changed the value of "SATA Operation" from AHCI (was the default) to ATA' which solved it for another 9200c owner but as soon as I do tha I cannot boot into Vista.

Please help.

Thanks in Anticipation!

---

### Post by ridgeland on 2007-08-16
Does the live CD boot OK?
Did you check md5sum of your download vs source's md5sum, also check the CD's md5sum?
Do you have other Linux OSs installed on your PC?  Experienced with Linux or new to it?

---

### Post by daageep on 2007-08-17
From my experience it is usually better to install Linux after windows anyway. Linux installs will write over the MBR and also let you boot windows after. The converse is not true.

If you have a spare partition already to go for Linux, I would suggest disabling the SATA and installing Linux. After that just turn the SATA back on.

---

### Post by nedrick on 2007-09-05
> **daageep said:**
> From my experience it is usually better to install Linux after windows anyway. Linux installs will write over the MBR and also let you boot windows after. The converse is not true.

If you have a spare partition already to go for Linux, I would suggest disabling the SATA and installing Linux. After that just turn the SATA back on.

Thanks for the reply. I disabled SATA and installed ubuntu. Everything is working fine except that I have to disable sata in order to go into ubunto and enable it again in order to go into vista.

Any ideas?
thanks!

---

