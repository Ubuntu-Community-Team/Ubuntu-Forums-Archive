---
title: "keyboard layout choosing"
date: 2009-01-19
forum: General Help
---

### Post by joey santiago on 2009-01-19
hi everybody

i am using xubuntu 8.10 that runs with Sun VirtualBox on a windows pc (the only way i found to have linux on my office computer).

- whether i switch the keyboard layout through Applications, Settings,  Settings Manager, Keyboard, Layouts (choosing fi, classic) then i can't use Altgr as third level selector. That's quite frustrating 'cause i can't type the at symbol, some parenthesis...

- i tried to use X11 configuration typing in /etc/xorg.conf and /etc/default/console-setup:

```
Section "InputDevice"
   Identifier   "Generic Keyboard"
   Driver    "kbd"
   Option    "XkbRules"   "xorg"
   Option    "XkbModel"   "pc105"
   Option    "XkbLayout"   "us, fi"
   Option    "XkbOptions"   "compose:ralt"
EndSection
```

and it resulted into an american keyboard layout...

does anyone have a clue?

thank you very much!:)

---

