---
title: "HELP!! Ubuntu will not boot and i cannot run it (or any other distro) as a live cd!!!"
date: 2008-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by plantboy1 on 2008-05-31
Alright, my ubuntu will not boot.  It gets to a certain point, and then just dies, saying something about a "readonly filesystem" and something needing recovery.  Now, the odd thing is, it worked fine, booted and all that, and i never changed anything, then literally, the next day it just would not boot.  I had been thinking it was the graphics, since ubuntu was having problems with the screen resolution and stuff right before it died. 

Today, i tried running the Ubuntu live cd, and it got to the same point as the normal boot (yes, i KNOW i am booting from the live CD) and hung.  I tried knoppix, and that got to where it was finding the partitions and creating Fstab, and it hung there.  (i have a dual boot setup, XP and Ubuntu, which was working fine till yesterday)  I'm assuming now that *maybe* it's the dual boot that's screwing it up, but i have no idea.

I'm running on a Dell Optiplex GX260, with Ubuntu 8.04, Ubuntu and XP dual boot.  Please help!!

NEW THEORY:  Knoppix uses swap partitions on the hdd when you boot it as a live cd.  Far as i know, so does Ubuntu.  If Ubuntu's swap space got messed up, then that would explain why i cannot boot any linux distros on this PC.  Uhh...any ideas how to fix that?

---

### Post by plantboy1 on 2008-06-01
I managed to fix it on my own, i blew ubuntu away then reinstalled.  Not what i wanted to do but it fixed it.

---

