---
title: "ubuntu 7.10/dvi switch problem"
date: 2007-11-03
forum: Desktop Environments
---

### Post by corbosman on 2007-11-03
I have a really weird problem, that almost looks like voodoo. Setup:

2 computers. 1 is Acer L100 running Ubuntu 7.10. Nvidia 6250 onboard. Other computer is Dell XPS720 running XP, with Nvidia 7950gx2. Both are connected to 1 Dell 2407fwp, using an Avocent switchview dvi switch.

This has worked flawlessly for months and months. Until a few days ago. Suddenly my Dell monitor would go into powersave mode permanently when switched to the XPS720. Linux would work fine. And if I connect the XPS to the monitor directly, also fine. So my first instinct is something is broken in the DVI switch. But, I could it to work if I removed both host dvi plugs, and switch them around. Then suddenly the XPS would show again, until I reboot. Then it stays in powersave again. 

So I kept thinking, what changed? Then it hit me, I upgraded to Ubuntu 7.10 a few days ago, from 6.10 (->7.04 -> 7.10). So..I dpkg-reconfigure xorg, and pick the nv driver instead of nvidia, and suddenly..*poof* no more problem.

So get this..the nvidia driver is doing something to my dvi switch, that makes it not want to go out of powersave (ie: doesnt see a signal) when _windows_ is booting. Ok..I know the linux community dislikes windows..but geez :)

So what has changed between 6.10 and 7.10 when it comes to the nvidia third party driver? 

Anyone that has an idea what could be going on here?

Cor

---

