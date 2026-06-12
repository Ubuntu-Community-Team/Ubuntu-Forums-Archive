---
title: "Keyboard errors"
date: 2006-02-19
forum: Desktop Environments
---

### Post by frostie on 2006-02-19
I have started getting the following show up when I log in:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The results requested are:

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb", "gb", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb", "gb", ""

and 

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = logicdp
 overrideSettings = true
 options = []

The keyboard is a Logitech Cordless Desktop Pro.

I've also noticed that if I try to key the pound sterling sign, 'shift 3' it just prints a '3'. All the other symbols print normally.

If I try to use System>Preferences>Keyboard I just get the same error message and no change.

---

### Post by frostie on 2006-02-19
From what I can gather on this, I've read a lot of posts/messages before and after posting here, this seemsto be some sort of unfixed bug with Gnome.
The only solution I've found that actually works is to switch to KDE, so I think I'll do that for now and wait to see if a fix becomes available.

Maybe when 2.14 comes along? I'm new to Ubuntu so I'm not sure how these things work.

---

### Post by ioliver on 2006-04-13
I've had this on every Dapper install I've done.  You don't seem to be able to switch to a UK keyboard.

I'm going to have to stick with Breezy until this gets fixed.

Ian

---

### Post by Ben C on 2006-05-10
Same problem here. I just filed a bug report.

[https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/44014](https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/44014)

---

### Post by Ben C on 2006-05-13
This is fixed now for me. :)

---

### Post by ray_seys on 2006-05-18
xmodmap -e "keycode 12 = 3 sterling" 

will enable £ sign

---

