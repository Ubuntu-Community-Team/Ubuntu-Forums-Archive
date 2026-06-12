---
title: "Using high resolution(1366x768) in dell mini10 -?-"
date: 2009-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by userid0 on 2009-07-11
recently I installed ubuntu9.04 netbook remix on my mini10.
Is there any method I can use high resolution (1366x768) mode in
ubuntu. It seems ubuntu does not support mini's high res mode.
In XP, so far, the graphic is perfect for me.
 
Thank you.

---

### Post by mikewhatever on 2009-07-11
Apparently, 9.04 doesn't support neither 1366x768 nor 1024x576 resolutions out of the box on Dell mini 10s. There is a fix for that [HERE]("http://ubuntuforums.org/showpost.php?p=6512181&postcount=94"), and let's hope that by the time Karmic is out there is 3d acceleration too.

---

### Post by userid0 on 2009-07-11
Thank you,
Is there any linux supports mini10's high resolution?

---

### Post by mikewhatever on 2009-07-11
I suppose any Linux that has the appropriate driver should support the correct resolution. The package in question is xserver-xorg-video-psb, and the problem with Jaunty is, it doesn't have it. You can get the package from Ubuntu's mobile repository, which the above mentioned procedure deals with. Apparently, Hardy Heron has it, but I don't know about the other distros.

---

### Post by TakeLifeEasy on 2010-06-23
Just brought a new Dell Mini 10 and has a 1366 x 768 display but I only get 1024x600 with Ubuntu 10.04.  Anyone know if there is a fix for this?

---

### Post by mellowb on 2010-10-16
I had a similar problem in a EEE PC and it was fixed after I installed the video cards support poulsbo. Check the link [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/).

---

