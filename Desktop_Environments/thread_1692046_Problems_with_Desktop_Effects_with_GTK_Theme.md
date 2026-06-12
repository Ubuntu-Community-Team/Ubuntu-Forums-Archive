---
title: "Problems with Desktop Effects with GTK Theme"
date: 2011-02-20
forum: Desktop Environments
---

### Post by LionsTigersAndTrouts on 2011-02-20
Okay, so, I downloaded and installed GNOME Elegant theme, and I'm really enjoying it, but I found a snag. I had previously been using Emerald/Compiz as my theme and window decorator, and I had to revert back to Metacity to enable the window controls for Elegant. Because I'm using Metacity, I can't seem to enable any desktop effects (Wobbly Windows, etc) without reverting back to my previous Emerald theme. Does anybody know a work-around?

---

### Post by Krytarik on 2011-02-20
To use the Metacity theme (window decoration) after you enabled the desktop effects/Compiz, press Alt+F2 and enter:
```
gtk-window-decorator --replace
```Greetings.

---

