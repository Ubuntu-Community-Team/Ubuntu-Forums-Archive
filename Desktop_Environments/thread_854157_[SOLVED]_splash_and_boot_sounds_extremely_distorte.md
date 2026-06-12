---
title: "[SOLVED] splash and boot sounds extremely distorted..."
date: 2008-07-09
forum: Desktop Environments
---

### Post by buccaneere on 2008-07-09
The drum roll that plays as the logon screen comes up is very fast, and distorted, and also the jingle that plays as the desktop displays is distorted (but not fast).

All web-streaming audio has the same distorted sounds, just as tho' the volume is maxed.

The machine is an almost new HPdv9000 64 bit AMD. Version is 8.04.

2 other machines that have 8.04 do not display this problem.

I think drivers are incorrect. Any ideas?

Also, possibly related, is the shutdown screen; it slowly fades black to white, distorted, not evenly.

---

### Post by sayakb on 2008-07-09
At a terminal:
```
sudo apt-get install linux-backports-modules-hardy
```
And reboot your computer..

---

### Post by buccaneere on 2008-07-09
> **LinuxIsInnovation said:**
> At a terminal:
```
sudo apt-get install linux-backports-modules-hardy
```
And reboot your computer..

Thanks linux...

I got Vista booted now; I'll install next ubuntu boot. 

Do I need to un-install anything?

---

### Post by buccaneere on 2008-07-09
No joy LinuxII. Still just as distorted as ever. I thought maybe it was hardware, but while in Vista, all audio is just fine.

What are the backports modules? Is there a soundcard driver amongst those modules?

No matter... I just like knowin' what I'm doin' (see sig line). 

Any other ideas?

---

### Post by buccaneere on 2008-07-10
> **LinuxIsInnovation said:**
> At a terminal:
```
sudo apt-get install linux-backports-modules-hardy
```
And reboot your computer..


I knew I shouldn't execute without knowin' what I was doin'...

Anybody know what these backport modules are?

Help?

---

### Post by sayakb on 2008-07-10
Sorry for posting late. Yes, the backport modules do have soundcard drivers.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by buccaneere on 2008-07-12
Anyone here?

---

### Post by buccaneere on 2008-07-13
Anybody with a clue on this?

All sounds are distorted...

---

### Post by buccaneere on 2008-07-13
solved

---

