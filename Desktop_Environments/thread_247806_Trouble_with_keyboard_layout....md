---
title: "Trouble with keyboard layout..."
date: 2006-08-31
forum: Desktop Environments
---

### Post by szofiel on 2006-08-31
Hi! Right now I'm wondering how to retrieve the panel which allows to select the active keyboard layout between Xorg and Gnome. That's because I did already placed it to permanent instead of temporary for Xorg and now I'm getting messages like this one:


> 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd 

So far, I would like to restore it to the earlier configuration, but I don't know how to call that panel back, in order to unselect the "Don't ask anymore" option.

Thank you!!

---

### Post by Paul41 on 2006-08-31
Is this what you are looking for? 

Go to System->Preferences->Keyboard

---

### Post by szofiel on 2006-09-01
No. I've messed with another thing: 

> 
sudo gedit /etc/X11/xorg.conf


Option "XkbLayout" "es"

Restart X 

When gnome starts again it asks a question. Answer use X settings and DON'T mark remember answer.


---

