---
title: "keyboard laout problem 8.04"
date: 2009-04-16
forum: Desktop Environments
---

### Post by ottosykora on 2009-04-16
On ubuntu 8.04 I am getting strange problem.
I am not able to set up keyboard layout other then the defoult us one.
I di dtry via the gui, I checked the obvious entries in the config files, all seem to be fine. Whe I start the ubuntu, I get:

Error activating XKB configuration.
It can happen under various circumstances:
-a bug in libxklavier library
-a bug in X server (xkbcomp, xmodmap utilities)
-X server with incompatible libxkbfile implementation

X server version data:
Colin Harrison
60900031

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


So I produced those outputs here:

 xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "de_CH", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "de_CH", "", ""



gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [de_CH]
 model = latitude
 options = [grp grp:alts_toggle]
 overrideSettings = true


any idea how to change the keyb layout to de_CH?

---

### Post by joseangelini on 2009-04-16
Did you edit the /etc/X11/xorg.conf file?
In it there is an InputDevice Section. My xorg.conf file has this 

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

You should change the XkbLayout to "de"

Good luck

---

### Post by ottosykora on 2009-04-17
I have tried to edit the xorg.conf.

Originally there were starnge entries there, but ok, I corrected all according your advise.
However no change at all.

All still writes in us keyboard.

Anybody having other idea how to force ubuntu to use other keyb layout?

---

### Post by joseangelini on 2009-04-17
Did you restart the X server or reinit your system?

---

