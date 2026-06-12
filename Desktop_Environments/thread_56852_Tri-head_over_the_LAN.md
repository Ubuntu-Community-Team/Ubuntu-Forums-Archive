---
title: "Tri-head over the LAN?"
date: 2005-08-14
forum: Desktop Environments
---

### Post by OwlManAtt on 2005-08-14
Howdy,

I've got three monitors up on my desk here, with two of them connected to one box (with a GeForce FX 5200), and one on another box (GeForce MX 400). I was wondering if GNOME had any support for multiple monitors over a LAN?

For example, could I just use one mouse/keyboard for both, as if the third monitor was hooked directly up to the GeForce FX 5200? I don't even mind if I can't access the computer with the one monitor's drives directly, I can do that via ssh. 

Even if GNOME can't, is there any way to do it with X? As it stands right now, GNOME doesn't know anything about the dual-head, it just thinks I have one really wide monitor.

Thanks everyone.

---

### Post by kokiri on 2005-08-14
As crazy as it sounds, This is a possibility. This should do it:
[Trihead vnc stuff](http://www.ncsa.uiuc.edu/TechFocus/Deployment/DBox/Doc/vnc.html) 

I've never done it or seen it happen or work, Got the tip from a linux 3d webpage during my quest to get my twinview working on my nvidia card.

Good luck...

---

### Post by wmcbrine on 2005-08-15
VNC, x2x, or just a standard remote X session, are among the possibilities. But I wouldn't call any of these a "triple-head" configuration -- only three directly-connected screens would merit that label.

---

