---
title: "OpenGL Games Crash within 3 minutes of starting"
date: 2008-11-16
forum: Gaming &amp; Leisure
---

### Post by iradi8 on 2008-11-16
I have an Ubuntu system that I use for MythTV. Originally it was Ubuntu with Myth, however I just reloaded it with Mythbuntu. I want to run OpenGL games on it, but within a couple minutes of starting a game it crashes and returns me to the desktop. There is no error in the logs or if I run it from the command line. It just dies.

The game I test is Extreme Tux Racer or Planet Penguin Racer if you like. But I have seen the exact same behavior with TuxCart as well. Non OpenGL games seem to function fine though. Does anyone have any idea where I can start looking? I thought that it was due to system instability because of other Xine related problems, thus the reason I reloaded it from scratch with Mythbuntu, but alas the issue followed me through the reload.

Here is my system config:
OS: Mythbuntu Intrepid 8.10
Proc: AMD Sempron 2800+
Video: nVidia 7600 with the ubuntu provided restricted drivers enabled.
Mem: 1GB
SATA HD

Thoughts? I have tried getting the nVidia drivers through envy in the past but that made no difference.

---

### Post by mut4nt on 2008-11-17
bump

im havin the same problem!

---

### Post by crazyfuturamanoob on 2008-11-17
Do you got the restricted OpenGL drivers installed?

System->Administration->Hardware drivers

---

### Post by iradi8 on 2008-11-17
Yes I am using the "Restricted Drivers". I did not compile the nVidia drivers from source this time, but I have in the past with no effect.

---

### Post by iradi8 on 2008-11-17
I am thinking there are two possibilities, 1) it is a driver issue, possibly because I am using the svideo out on the nividia card as my "primary monitor". 2) it is a hardware failure somewhere in the box. Memory, Proc, Video Card, MB. OK MB might be a stretch but not impossible.

I am going to try to hook the box up to an LCD through the VGA interface and try running the games that way, if it still does it's trick I will see what I can do about a full hardware diagnostic.

I guess I was just hoping someone else had seen this and had some briliant insight I couldn't think of. If anyone does, I am all ears, but if not I will report back on my progress, in the interests of posterity, (and mut4nt).

---

### Post by eragon100 on 2008-11-18
Do you guys have desktop effects enabled? disable them, it (almost) always causes problems like this. (I don't know wether mythbuntu has desktop effects, but if it's anything like regular ubuntu it has, and they will be enabled by default.)

---

### Post by iradi8 on 2008-11-18
Mythbuntu has desktop effects disabled by default. Unfortunately I had already considered that and gone looking for it. Mythbuntu also uses the XFCE WM by default, if that makes a difference, but I doubt it.

---

