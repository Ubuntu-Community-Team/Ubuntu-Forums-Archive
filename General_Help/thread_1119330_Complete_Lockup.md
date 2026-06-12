---
title: "Complete Lockup"
date: 2009-04-07
forum: General Help
---

### Post by Lucky75 on 2009-04-07
Hey all,

I've recently ran into an issue where I get a complete lockup on my system. Both the keyboard and mouse do not work, and the screen freezes where it is.

Nothing else seems to change in terms of disk speed/fans/etc, but I have to do a hard reboot to get back. I've checked /var/log/messages and /var/log/kern.log, but there doesn't seem to be any sort of message about an error?

Any ideas?

Gfx: Nvidia 7600GT using "nvidia" driver. 
Cpu: Core2Duo E6600@2.4Ghz


There really wasn't anything that changed, but in the past two days I've had this issue twice now. 

Thanks!

---

### Post by Sam Lars on 2009-04-09
I guess hardware is a possibility... any chance you could test with a different OS or installation?
You could also try not using Compiz (if you are).

---

### Post by Lucky75 on 2009-04-12
I'm using a default install of ubuntu, so I'm not sure if it's using compiz or not. I've tested a bit on XP (Dual boot), but so far nothing seems to be the matter. It's rather difficult to test though, since it happens so randomly...

---

### Post by coffeecat on 2009-04-12
One possibility is bad RAM. Windows and Linux use RAM differently, so with Linux you're more likely to be accessing memory at the top end of the available memory. If the faulty bit is there, you could have just been lucky with Windows never using that bit.

Have you got any spare RAM sticks to try? Or if you've got two sticks, take one out, try it, and then try the other. You don't say how much RAM you have. Ubuntu will run well enough in as little as 512 MB. The system might be slower but if only one of the sticks is faulty, at least you get to see which one.

---

### Post by Lucky75 on 2009-04-13
I actually have 4 gigs of ram, and it hasn't been an issue until recently (using Ubuntu for about a year now). I'm not sure, the problem is that it happens so randomly that it's difficult to pin down. Why wouldn't anything be written to error logs? Unless I'm looking in the wrong one?

---

