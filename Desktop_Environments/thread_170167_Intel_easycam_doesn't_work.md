---
title: "Intel easycam doesn't work"
date: 2006-05-04
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-05-04
I have a Intel PC Camera CS110 on the usb.after using easycam to compile the drivers i started camorama to test the webcam.now whenever i start camorama the computer just hangs and i have to restart it.anybody know how to install this webcam in ubuntu??

---

### Post by Sef on 2006-05-04
Here's a driver for your cam.

[http://sourceforge.net/project/shownotes.php?group_id=28498&release_id=144949]("http://sourceforge.net/project/shownotes.php?group_id=28498&release_id=144949")

What one person had to do to get it running (use the top one first; use this only if you can't get the top one to work.)

[http://www.linuxquestions.org/hcl/showproduct.php?product=676&cat=477]("http://www.linuxquestions.org/hcl/showproduct.php?product=676&cat=477")

---

### Post by louis_nichols on 2006-05-04
I think this thread [http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

is for you. I had the exact same problem till I followed it. The spca module is actually included in ubuntu, just doesn't work properly until recompiled according to these instructions.

---

### Post by akshaysrinivasan on 2006-05-04
It worked ,Thanks a lot.i found another problem ,you see i have a tv cpture card with saa7134 chipset so camorama thinks that is the webcam,but camstream detects the webcam,do you know how to change the device for camorama??

---

### Post by akshaysrinivasan on 2006-05-04
got it working with camorama.i used -d tag

---

### Post by louis_nichols on 2006-05-05
:)

glad to read all this. you're good to go now!

messenger support for video/audio is almost here (well... kopete already has webcam support for yahoo and msn, actually)... can't wait!

---

