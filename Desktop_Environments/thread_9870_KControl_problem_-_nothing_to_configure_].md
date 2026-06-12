---
title: "KControl problem - nothing to configure :]"
date: 2005-01-02
forum: Desktop Environments
---

### Post by acidnoizz on 2005-01-02
Hi every1!
I have installed almost everything needed for KDE, but still when I run kcontrol there is nothing in the tree/icon view at the left. The terminal output is:
```
(...)
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/text not valid.
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
```
Can anyone tell me what to do?

---

### Post by Kauderwelsch on 2005-03-07
Hi!
I nearly got the same problem. Installed KDE dependencies and got the following Terminal Output. I read about intalling the  kdeartwork package would help and installing the gnome-menu package but nothing works.

 

```
(...)kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.calc.template'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.lotus-1-2-3'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'text/x-comma-separated-values'
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
```

Pls help.

---

