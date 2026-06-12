---
title: "Keyboard going crazy - can't type gbp sign"
date: 2006-07-14
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-07-14
Today when I logged on to my machine I realised that I can't type the gbp sign. When using shift and 3 (like it normally is) I just get a 3. The rest of the number keys work with shift. 

What has gone wrong?

Can anyone help? I am using the GB layout or should be at least.

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-14
UPDATE: under System > Preferences > Keyboard I can't change anything I get errors saying

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



My super_l key does not work. Can anyone please please help me fix this. I don't want to have to reinstall.

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-14
Woah triple post terribly sorry but I fixed it. After a half arsed atempt to downgrade libxkbfileto libxkbfile1_7.0.0-3_i386.deb by following ancient Breezy intructions to fix the same bug I went to Synaptic to fix the broken package after unsuccesful downgrade. Updated and hey presto it worked.

How odd.

---

