---
title: "Can't single-click after upgrade to 8.04"
date: 2008-04-24
forum: Desktop Environments
---

### Post by jazzgossen on 2008-04-24
I just finished upgrading from 7.10 to 8.04 and rebooted, and now I can't single-click with the mouse anymore. Clicking the left mouse button generates a double-click. I have no idea where to look for the source of this. Do you have any ideas?

---

### Post by jazzgossen on 2008-04-24
Sorry. I *had* been searching through the forums and Google for answers, but shortly after posting my quesion I found a post that suggested that it had to do with duplicate Mouse entries in xorg.conf. I did have two mouse sections there: Mouse1 and Mouse2. I commented out the section regarding Mouse2 and also a line saying
   InputDevice	"Mouse2" "SendCoreEvents"
and now everything seems to be OK again.

---

### Post by whoelse on 2008-04-24
Hi, I have the same problem, but I do not have two mices in my xorg.conf.

This thread is great, seconds after writing here, I have found a solution (I hope it still works tomorrow)


sudo dpkg-reconfigure -phigh xserver-xorg
 
then restart the gdm

---

