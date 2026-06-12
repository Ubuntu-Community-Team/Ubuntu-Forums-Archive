---
title: "keymap can't be altered or all options loaded"
date: 2005-10-19
forum: Desktop Environments
---

### Post by BROKEN_LADDER on 2005-10-19
after upgrading to breezy, my keymap is very broken.  i can't make any changes to it, and i can't set my third level chooser in order to use the accented characters that i've set up.  this had always worked in warty and hoary.

the error i get is as follows:

> Error activating XKB configuration.
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

And so here's that output:
> 
xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "dvorak", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "dvorak", "", ""


> 
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = [us,dvorak]
model =
overrideSettings = false
options = [lv3 lv3:switch,grp  grp:alts_toggle]


---

