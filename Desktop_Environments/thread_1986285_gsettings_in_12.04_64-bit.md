---
title: "gsettings in 12.04 64-bit"
date: 2012-05-24
forum: Desktop Environments
---

### Post by atom715 on 2012-05-24
Hello, I need some help with my gsettings in ubuntu 12.04 64-bit.  I entered the command (gsettings set org.gnome.desktop.interface gtk-theme 'swar-light-blue').  I was wondering how I would change it to the default gsettings.  Any help would be greatly appreciated.

Thank You,
atom715

---

### Post by drs305 on 2012-05-24
The 'gtk-theme' default appears to be "Adwaita" for 12.04 Precise. You can check it afterward. Run:
```
gsettings reset org.gnome.desktop.interface gtk-theme
```

You can install 'dconf-tools' and then open 'dconf-editor' for a GUI way to make the same changes.

---

### Post by mc4man on 2012-05-24
There are actually 2 'Default's, the gnome one & seen in dconf would be as mentioned,  Adwaita

The shipped Default in Ubuntu would be,  Ambiance

---

### Post by atom715 on 2012-05-24
@drs305 Thank You it worked like a charm the first time

---

