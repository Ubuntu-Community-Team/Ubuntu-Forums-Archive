---
title: "Error message - Error activating XKB configuration."
date: 2009-05-07
forum: General Help
---

### Post by jakupl on 2009-05-07
Everytime I log in, I get the following error message:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

And I don't like it. Does anyone know how to get rid of it?
Any help is much appreciated.

---

### Post by scienceandcake on 2011-03-12
Same here. 

Error activating XKB configuration.
It can happen under various circumstances:
 • a bug in libxklavier library
 • a bug in X server (xkbcomp, xmodmap utilities)
 • X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10900000

If you report this situation as a bug, please include:
 • The result of xprop -root | grep XKB
 • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by scienceandcake on 2011-03-14
I use a Macbook 5,1. 

I installed the hid-apple-dkms on my computer yesterday. I didn't get the error when I started up.

---

