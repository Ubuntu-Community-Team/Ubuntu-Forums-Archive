---
title: "[SOLVED] Why is VNC so much slower on Ubuntu?"
date: 2009-01-03
forum: General Help
---

### Post by the real omni on 2009-01-03
I have RealVNC set up on my XP machine as a service. When I connect from another XP machine on my LAN it's super fast. When I boot the same machine to Ubuntu and try to VNC into the XP machine (still over the LAN) it's WAY WAY slow. It draws the desktop, then it takes about 1 minute of redrawing the desktop before it accepts input. Once it starts accepting input, if I move the screen I can literally watch it redraw one inch at a time and it takes about 30 seconds to fully redraw the screen.

Obviously since the XP partition has NO latency issues at all when VNCing, it must be something wrong with the Ubuntu VNC client. 

Can anyone explain why the Ubuntu VNC client performs so poorly? Or, more importantly, can anyone explain how I can get its performance to increase to the point where it's at least usable? I've already tried reducing colour depth and removing the remote desktop background - still have to wait at least 1 min before it accepts input and it still draws super slow.

---

### Post by Polygon on 2009-01-03
maybe you could try another vnc client, i havent heard great things about vinagre (the default one)

---

### Post by CrusaderAD on 2009-01-03
RealVNC works great when you go Linux to Linux... but Linux to Windows does have performance problems. Not sure why... probably because windows reserves the best speed and ports for their own Remote Desktop Client. I've tried many vnc clients and they all do the same thing.

---

### Post by the real omni on 2009-01-04
Okay I've found something that seems to work very well.

The solution isn't to hunt out an alternative linux VNC client. The solution is to ditch RealVNC as an XP VNC host and replace it with TightVNC.

Running the TightVNC server on an XP machine, and connecting using vncviewer with ubuntu. Super super fast, everything works the way it should, keyboard special keys are passed properly.

In general, it's wayyyyy better than RealVNC.

---

### Post by johnnyw on 2009-05-26
which server can i reaplce VNC with?

---

