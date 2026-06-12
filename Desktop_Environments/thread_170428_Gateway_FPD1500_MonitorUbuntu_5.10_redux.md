---
title: "Gateway FPD1500 Monitor/Ubuntu 5.10 redux"
date: 2006-05-04
forum: Desktop Environments
---

### Post by pspotts on 2006-05-04
Folks,

I've installed 5.10 on a hand-me-down Gateway we got from a friend (and just finished with the on-line updates). It uses the FPD1500 monitor, which a previous poster had challenges with as well. And from the tail end of that set of postings, it doesn't look as if it his problem was resolved. So, in the interests of "if at first you don't succeed...":

I have tried to reconfigure xorg.conf manually, ensuring (I think) that the right resolution choices and correct sync frequencies are entered. When I reboot, I get the same oversized renderings on the screen -- looks like maybe 640x480. When I try to set the screen resolution using Ubuntu's tool, the only choice it gives me is 640x480. So, I ran sudo dpkg-reconfigure xserver-xorg to see if that approach would help. It didn't; in fact, once the computer started, and I looked at the screen rez tool again, it still only gave me 640x480 as a choice, even though I'd entered 1024x768 as a choice, as well as the correct sync frequencies. So...what should I try next? BTW, the video card is an ATI 3D Rage LT Pro (AGP).

With best regards,

Pete

---

