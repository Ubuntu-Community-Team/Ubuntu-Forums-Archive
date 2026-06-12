---
title: "Beryl and Xgl with ATI problem"
date: 2007-03-17
forum: Desktop Environments
---

### Post by g0ng on 2007-03-17
I just installed ubuntu, and I have a ATI sapphire 1650X video card. I have desabled composite extensions in xorg.conf and when my server starts fglrxinfo gives:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

If I log in with an Xgl session
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

the it sais extensions are missing. beryl can be loaded (with beryl-manager & bery-xgl --use copy only because else I get a white screen) but its slow and hangs.

What's the problem? 
Thanks

---

### Post by Patrick-Ruff on 2007-03-17
I don't think I can even voice how many things could potentially be going wrong here . . .


try the new ATI drivers at ati.amd.com and then post back. many people with newer cards have better luck with those drivers.

---

