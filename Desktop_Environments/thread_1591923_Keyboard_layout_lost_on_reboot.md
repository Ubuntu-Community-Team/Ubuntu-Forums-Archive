---
title: "Keyboard layout lost on reboot"
date: 2010-10-10
forum: Desktop Environments
---

### Post by grovitch on 2010-10-10
Hi all,

I am having trouble setting up my keyboard to the right layout. Strangely, it keeps switching back to Gbr after each reboot, eventhough I set it to Fr through System.Preference/Keyboard, delete the Gbr layout, have only Fr used and apply system-wide.

Editing my /etc/X11/xorg.conf doesn't seem to help either. (I have tried with:

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fr"
EndSection

but it doesn't change anything.

Anyone could help on this? Thx

---

