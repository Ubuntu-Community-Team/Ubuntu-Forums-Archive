---
title: "Install problem"
date: 2008-03-04
forum: Desktop Environments
---

### Post by Mehtras on 2008-03-04
Hey everyone,

I downloaded the Ubuntu iiso and burned it to a CD, all's well so far.

I'm able to boot to the CD and see the options menu and when i select install ubuntu, it starts running, just onto the part where ubuntu should appear. At that point it just shows some weird screen for a split second and then my monitor says i should adjust the resolution.. After that, it just stops at the last line it processed (*loading local boot record    [OK])

My system is a Dell dimension E521 i have the latest BIOS. It contains a Ati Radeon X1300 Pro video card and i suppose the problem is located around this card. Actually, i know it is, since i tried booting without this card and everything went fine.. except for the max resolution of 800X600 which made it impossible to press OK on the install screen..

I hope anyone can help me with their simmilar experiences or just their experience.

Thanks in advance.

---

### Post by cmnorton on 2008-03-04
If a safe mode install won't work, try a text mode install. I was about to try a command line install with the intent of building up from a running system, but the text mode install worked for me after a lot of tweaking. 

Perhaps you will not need that level of tweaking, because you have a desktop, not a laptop. Please bear in mind that the link below points you to my experiences installing Ubuntu 7.10 a Thinkpad T61p laptop. I'm pointing you there, because you mentioned graphics. It might be a long shot.

[http://ubuntuforums.org/showthread.php?t=712118](http://ubuntuforums.org/showthread.php?t=712118)

All in all, I've found Dell hardware very accommodating for  Linux installations, but I have not yet installed Ubuntu on a Dell, just RH EL 3 and 4 and Fedora 6. 

As is stated in many forums, no less in the Ubuntu forums, graphics can cause you a lot of trouble.

Good luck.

---

### Post by Mehtras on 2008-03-05
hey, thanks,

the text install form the alternative cd worked, but the problem persists, as soon as i select ubuntu from grub, everything runs fine untill ubuntu is loaded and is supposed to start the gui. My screen blacks out, telling me is should adjust my resolution and then it all stops, i can enter commandline by pressing alt F2 or something, but this basically just isn't nice..

Any ideas?

---

### Post by taurus on 2008-03-05
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Mehtras on 2008-03-06
well, thanks for all the support. I tried all that and some things worked, others didn't.. In the end, the problems persisted and i was left with a 800X600 resolution. 

I think the problem is, that ubuntu won't recognise my monitor and my graphix card at the same time..

still stuck..

EDIT:

Never mind, all of a sudden it all worked, i messed some with the xorg settings, did some tweaking here and there and voila, it worked.. I have no idea what i did, but it worked, so thanks all!

---

