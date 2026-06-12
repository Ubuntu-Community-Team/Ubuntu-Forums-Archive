---
title: "xfce keyboard layouts can't be changed"
date: 2007-11-19
forum: Desktop Environments
---

### Post by tetrafuran on 2007-11-19
I tried to edit xorg.conf but it didn't have any effect on the layout languages. Here's what I have in there at the moment.

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fi,us"
# Option         "XkbOptions" "lv3:ralt_switch"
# This is the line that used to be there, 
# but most threads and guides didn't mention this line. 
# I added the one you see on the next line.
    Option         "XkbOptions"  "grp:alt_shift_toggle"
EndSection
```

I have tried looking for help from several sources and I still haven't found a solution to this.

---

### Post by tetrafuran on 2007-11-22
Any ideas? Should I just simply re-install xfce-desktop?

---

