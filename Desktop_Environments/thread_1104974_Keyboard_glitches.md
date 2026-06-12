---
title: "Keyboard glitches"
date: 2009-03-24
forum: Desktop Environments
---

### Post by Flupke on 2009-03-24
I use a french layout keyboard, and have all kinds of problems since I upgraded to 8.10. The solution if I remember well was to change the keyboard layout from 'Generic/evdev' to 'Generic/Generic 105 keys (intl)' and set the layout in xorg.conf :
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fr"
    Option         "XkbVariant" "latin9"
EndSection
```

This worked for some time, but since the last xorg update, my keypad started to produce unicode characters instead of 'minus' (&#8722; instead of -) and 'slash' (now it works again and I can't paste the character, go figure...).

So I started tweaking the keyboard settings again, went by all the old bugs then some new ones (keys 5-0 not working at all, X server crashes with some keyboard combinations, etc...), and the solution now seems to be 'Generic/Generic 105 keys (intl)' with 'France (obsolete) Other' layout, combined with the xorg settings above. Well at least it works *now*, maybe it won't on the next reboot.

I wonder how the keyboard code got in such a broken state, does anyone have a solution that could make me forget about it, like I did for the past 10 years ?

---

