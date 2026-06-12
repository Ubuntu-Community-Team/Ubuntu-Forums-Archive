---
title: "Problem with Keyboard (no @ # keys)"
date: 2005-08-18
forum: Desktop Environments
---

### Post by daurelio on 2005-08-18
Hi Everybody

I have a problem with my spanish keyboard (Laptop Toshiba Satellite SM30X-166). On Ubuntu I can't use "@" "#" "|" keys because "Alt Gr" as none efect on the keyboard.
On windows i don't have this problem...
Can anyone give a hand with this anoying problem?

Thanks
Dany

---

### Post by DeliMart on 2005-12-13
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
same problem.....
AAAAAAAAAAARRRRRRRRRGGGGGGGGGGGGGGHHHHHHHHHHH
no solution

---

### Post by DeliMart on 2005-12-13
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
--->
 _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "dk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "dk", "", ""

- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
--->
 layouts = [dk]
 model = pc104
 options = [grp grp:alts_toggle,lv3     lv3:ralt_switch,lv3     lv3:alt_switch]
 overrideSettings = true

---

### Post by daurelio on 2005-12-14
The problem was solved when I upgrade to Breezy...
Thanks for your reply

Daniel

---

