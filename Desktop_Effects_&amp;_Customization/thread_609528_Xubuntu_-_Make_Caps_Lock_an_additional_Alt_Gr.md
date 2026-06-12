---
title: "Xubuntu - Make Caps Lock an additional Alt Gr?"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by SakJur on 2007-11-11
How do i make so that Caps Lock is an additional Alt GR?
This is because i got no Alt Gr :P :KS

---

### Post by rubo77 on 2008-02-09
i would like to know as well.
i need it for my one-hand-writing keyboard-layout:
[www.entikey.z11.de](www.entikey.z11.de)

---

### Post by rubo77 on 2008-02-12
i found out myself:

in ~/.Xmodmap
```

!! Make caps lock an additional Alt_Gr
remove Lock = Caps_Lock
keysym Caps_Lock = ISO_Level3_Shift
```
it should load when x starts, but you can manually start it with:
```
xmodmap ~/.Xmodmap
```
see
[http://www.eigenheimstrasse.de:8668/comments/Computerecke/NEO-Tastaturlayout/Verbesserungsvorschl%C3%A4ge/CapsLock+durch+AltGr+ersetzen](http://www.eigenheimstrasse.de:8668/comments/Computerecke/NEO-Tastaturlayout/Verbesserungsvorschl%C3%A4ge/CapsLock+durch+AltGr+ersetzen)

---

