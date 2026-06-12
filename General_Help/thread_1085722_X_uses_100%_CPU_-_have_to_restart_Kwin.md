---
title: "X uses 100% CPU - have to restart Kwin"
date: 2009-03-03
forum: General Help
---

### Post by newlinux on 2009-03-03
I have recently switched to using KDE again on one of my computers, but there is annoying bug.

Anytime the machine has been left alone for a little bit (possibly when the screensaver is supposed to activate or when the monitor is put to sleep, havin't verified this is when it happens yet) X takes up 100% of one of my CPU cores and the desktop is basically frozen (kwin is frozen). The only ways out are to restart Kwin or X.

Any ideas on how to fix this?

This is on 8.04...

---

### Post by newlinux on 2009-03-04
bump

---

### Post by Crafty Kisses on 2009-03-04
A couple of questions here, how much RAM do you have? Have you checked the top output and see if X is actually using 100%? Post the results of this command:
```
top
```

---

### Post by newlinux on 2009-03-05
> **Codename said:**
> A couple of questions here, how much RAM do you have? Have you checked the top output and see if X is actually using 100%? Post the results of this command:
```
top
```

I am sure that it is using 100% of 1 core.  I use htop. Top doesn't show the separate cores, which is why I prefer htop. I've got a gig of RAM, so I doubt that's the issue. I've used machines with way less CPU and RAM with KDE without a problem.

---

### Post by newlinux on 2009-03-05
More info, this is the E2180 machine in signature... Uses an integrated intel GMA3100 GPU (intel driver), 1GB PC5400

---

### Post by newlinux on 2009-03-05
It also doesn't occur when I just leave the screen on KDM, or when I am consistently using the machine. Only if I leave it idle for a few minutes.

---

### Post by newlinux on 2009-03-09
bump any ideas? I've seen some bugs, but they seem to deal with various options within KDE, which I think I have disabled... not sure - I'm not extremely experienced with KDE.

---

### Post by newlinux on 2009-03-12
Still at a loss here... Done some more investigating, but still haven't turned up anything. It's gotta be something kwin is doing, because restarting it fixes the problem temporarily. I've been playing with various KDE configs, but to no avail.

---

### Post by newlinux on 2009-03-19
Gave up and went back to Gnome for this machine.

---

