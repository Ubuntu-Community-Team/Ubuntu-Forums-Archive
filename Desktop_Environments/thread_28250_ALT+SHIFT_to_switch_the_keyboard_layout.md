---
title: "ALT+SHIFT to switch the keyboard layout"
date: 2005-04-19
forum: Desktop Environments
---

### Post by SGC on 2005-04-19
I want to change keyboard shortcut for switching the keyboard layout to use "alt+shift" instead of the default one "alt+ctrl+k" in KDE
 
when i changes the key shortcut in:
control center > regional & accessibility > keyboard shortcut

**alt+shift** becomes **alt+iso_prev_group**  :-? 

And even when i choose any other combination it changes the layout from English to Arabic but it does not change it back from Arabic to English unless i clicked on language indicator in the system tray.

---

### Post by prattler on 2006-10-06
Need something like that for xfce, too.

---

### Post by Jandark on 2008-03-22
EDIT /etc/X11/xorg.conf

do some thing like
```

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xorg"
    Option      "XkbModel"  "pc105"
    Option      "XkbLayout" "us,ir"
    Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

```

restart X

---

