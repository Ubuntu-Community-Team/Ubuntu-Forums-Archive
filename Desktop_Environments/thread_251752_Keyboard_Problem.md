---
title: "Keyboard Problem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by wvernon on 2006-09-05
Ever since the x-server problem (I think), my keyboard has not been able to produce the pound sterling sign usually obtained by pressing shift-3.

Any ideas as to what I can do to get it back? :-?

---

### Post by meng on 2006-09-05
Does it produce anything at all, maybe the hash sign #  ?
I wonder if it's just a keyboard layout issue, I guess you want UK.
You can change keyboard layout from GNOME, under System somewhere.

---

### Post by wvernon on 2006-09-05
Meng,

Thanks for the reply. No, nothing appears.

If I go into the keyboard selector via system-preferences, I get the following popping up on a new window:

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


:confused: 

Any ideas as to what's happening?

---

