---
title: "Going to switch video card"
date: 2008-12-04
forum: General Help
---

### Post by liniaal on 2008-12-04
First of all: i didn't know in which subforum this topic would fit best but i figured this is the one where most of the graphics cards talk is happening. If anyone feels the need to move it to, say, Hardware, it's ok with me of course.

Right now i work on a workstation with nothing more than a onboard intel graphics adapter (for workstation purposes btw, it works deliciously!). I recently got hold of a ATI Radeon 2400 pro. If i understood correctly, with the new Xorg version and stuff (i was coming from 7.10, now fresh install of 8.10) i can just shut the machine down, connect the new vid card, connect the monitor to that output, and boot back into xubuntu. Is it true that this *should* work?

thanks in advance

---

### Post by eternalnewbee on 2008-12-04
According to this link you can, but I suggest you do some research first:
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

---

### Post by liniaal on 2008-12-04
thanks for the quick reply. i have a radeon 2400 pro so i think that is not associated with the radeonhd driver?

---

### Post by eternalnewbee on 2008-12-04
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)
This worked like a charm for Sponzenbroekske in this link:
[http://ph.ubuntuforums.com/showthread.php?t=958815](http://ph.ubuntuforums.com/showthread.php?t=958815)

---

### Post by liniaal on 2008-12-06
well i did it and it worked deliciously :D as they say

just plugged in the ati, connected monitor to that output, boot ubuntu up, and it will automatically come up with the availability of a restricted driver. you have to type your password once for the install, reboot once, and it's done! amazing. now i can have compiz running :D

---

### Post by eternalnewbee on 2008-12-06
> well i did it and it worked deliciously  as they say
Excellent!
Don't forget (in your excitement) to mark the thread as solved:D

---

