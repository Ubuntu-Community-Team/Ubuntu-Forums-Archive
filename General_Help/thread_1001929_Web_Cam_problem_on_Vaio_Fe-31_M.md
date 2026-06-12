---
title: "Web Cam problem on Vaio Fe-31 M"
date: 2008-12-04
forum: General Help
---

### Post by Elvin Mammadov on 2008-12-04
Hello,

I'm new to Ubuntu and Linux. I installed Ubuntu 8.10. Most everything is working! However, on my Sony VAIO notebook model VGN-FE31M, I do not now how to use the my Web camera. I can not use my web cam on MSN or SKYPE program? Do I need to install a driver or something. I basically want to use it as a web cam or just to take pictures. Any help is greatly appreciated.

Thanks!

Elvin

---

### Post by blueridgedog on 2009-01-06
Ignore - I posted to an old thread....and started it up again

---

### Post by spiderbatdad on 2009-01-06
could you post the output of command:```
lsusb
```This might be a microdia cam, in which case, you may find a driver and instructions here: [http://groups.google.com/group/microdiaTo](http://groups.google.com/group/microdiaTo) use with skype you will likely need to preload libv4l. there is a brief discussion here:[http://ubuntuforums.org/showthread.php?t=1026188](http://ubuntuforums.org/showthread.php?t=1026188)

---

### Post by bigbrovar on 2009-01-06
try if this works for you 
[http://ubuntuforums.org/showpost.php?p=6101912&postcount=5]("http://ubuntuforums.org/showpost.php?p=6101912&postcount=5")

---

### Post by Elvin Mammadov on 2009-01-16
> **spiderbatdad said:**
> could you post the output of command:```
lsusb
```This might be a microdia cam, in which case, you may find a driver and instructions here: [http://groups.google.com/group/microdiaTo](http://groups.google.com/group/microdiaTo) use with skype you will likely need to preload libv4l. there is a brief discussion here:[http://ubuntuforums.org/showthread.php?t=1026188](http://ubuntuforums.org/showthread.php?t=1026188)

Bus 005 Device 004: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 005 Device 003: ID 054c:0281 Sony Corp.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Elvin Mammadov on 2009-01-16
I tried this one : [http://ubuntuforums.org/showthread.php?p=6560957#post6560957](http://ubuntuforums.org/showthread.php?p=6560957#post6560957)

It works.Now I can use Webcam On skype..

But only in skype not Amsn or even when I signed my facebook try to capture photo with my camera it shows me CAMERA NOT FOUND!...

Do you have solution for them?
If you have plz share it with me I need to fix it and Continue with UBUNTU.

---

