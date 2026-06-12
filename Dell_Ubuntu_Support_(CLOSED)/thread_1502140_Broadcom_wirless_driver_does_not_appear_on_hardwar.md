---
title: "Broadcom wirless driver does not appear on hardware drivers list after install."
date: 2010-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thex707 on 2010-06-05
hi,


i upgraded to the new ubuntu 10.04 on a dell dimension 3000 .. i had other versions of ubuntu before and it worked well but now i have a problem. I cannot seem to get the wireless drivers to get going. There is no mention of any broadcom 43xx driver at all.. i installed ndiswrapper and it said the hardware was present but the hardware drivers list didn't have it enabled.. it showed nothing. I also installed fwcutter through the ubuntu cd and nothing (i've done this method before on an earlier version of ubuntu). I remember when i was getting ready to install through the live cd it showed the hardware drivers icon and when i fully installed it, that never appeared.. i have also another harddrive with XP on it not sure if that has anything to do with it.. what else can I do?  thanks in advanced.

---

### Post by howefield on 2010-06-05
Have you updated the software package lists since installing ?

```
sudo apt-get update
```

Then try hardware drivers again.

---

### Post by thex707 on 2010-06-05
I did that command and it wont let me as I need the internet for that.

---

### Post by wojox on 2010-06-05
You don't have an Ethernet cable you could use?

---

### Post by thex707 on 2010-06-05
nope i do not unfortunately..

---

### Post by wojox on 2010-06-05
Is 

```
bcmwl-kernel-source
```

On the CD?

---

### Post by thex707 on 2010-06-05
Yea and i installed it but it give errors of not retrieving or finding a file:

its seems its going good but then this shows:





> 

building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command found

Error! application of patch 0001-MODULE LICENSE.patch failed
Check /var/lib/lib/dkms/bcmwl/5.60.48.35+bcom/build for more information
dpkg: error processing bcmwl-kernal-source (--install)
subprocess installed post-installation script returned error exit status 5 
Errors were encountered while pressing
 bcmwl-kernel-source

---

### Post by wojox on 2010-06-05
Figures. Best bet would be find someone with an Ethernet cable and Internet connection.

---

### Post by thex707 on 2010-06-05
Yea I'll guess Ill have to do that then.. well thanks for your help!

---

### Post by ugm6hr on 2010-06-05
Try this thread:
[http://ubuntuforums.org/showthread.php?t=1477215](http://ubuntuforums.org/showthread.php?t=1477215)

---

### Post by fegster69 on 2010-06-09
> **howefield said:**
> Have you updated the software package lists since installing ?

```
sudo apt-get update
```Then try hardware drivers again.

I had the same problem. Just installed Ubuntu 10.04 on my Dell 1545 laptop with Win7 dual boot and my wireless wouldn't work. Did exactly as you said, and hey presto. worked straight away. 

Thanks 

Andy (Ubuntu newbie)

---

