---
title: "Different startup apps for Gnome and XFCE"
date: 2009-09-13
forum: Desktop Environments
---

### Post by lobonegro.rlopez on 2009-09-13
I recently installed XFCE along side gnome in Ubuntu for media center purposes. When I start xfc, I don't want the same applications starting up as I do when I start gnome. Is there any way tomake that happen?

---

### Post by Brandon Williams on 2009-09-13
Your autostart applications are represented by *.desktop files in ~/.config/autostart/. In those files, look for the variables OnlyShowIn and NotShowIn (if they don't exist, you can add them). Use these to limit the environments that the app is started in. For example:
```
OnlyShowIn=GNOME;XFCE;
OnlyShowIn=XFCE;
OnlyShowIn=GNOME;
```

The GUI apps for autostart apps might handle this correctly, but I'm not sure.

---

### Post by lobonegro.rlopez on 2009-09-13
Thanks, I'll try it out.

---

