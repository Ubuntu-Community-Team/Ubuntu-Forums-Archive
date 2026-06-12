---
title: "Different Keyboard"
date: 2010-10-10
forum: Desktop Environments
---

### Post by funalien on 2010-10-10
Multiple Keyboard Layouts

When I was using Gnome I had 3 layout by default: Polish, Russian and Lithuanian. Then, I've installed awesome wm. Now I can't change keyboard layouts anymore. To solve this problem, I checked my xorg.conf file, but there wasn't any section like "InputDivice", so I've created one.
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
     Option        "AutoRepeat" "500 30"
    Option         "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option         "XkbLayout" "us,ru(winkeys)"
    Option         "XkbVariant" "base"
    Option         "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll,compose:ralt"
EndSection
```
After restarting X server, nothing changed.
So I'm using gnome-settings-daemon to use multiple layout.
It seems like ubuntu stores and reads configurations in a different way which I don't know.

Please, give me advice to solve this question. Thanks.

---

