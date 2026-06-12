---
title: "gtk menu delay"
date: 2009-12-09
forum: Desktop Environments
---

### Post by Spaceboy on 2009-12-09
In older versions of ubuntu I was able to set the pop-up delay for the gnome menus and gtk apps simply using the following command:

echo "gtk-menu-popup-delay = 0" >> ~/.gtkrc-2.0

However, this doesn't seem to have any effect with the latest Ubuntu version.  Does anyone have another hack that will speed up the gnome menu's?

---

### Post by wojox on 2009-12-09
Work's here, try:

```
echo "gtk-menu-popup-delay=0" >> ~/.gtkrc-2.0
```

Leave out the spaces. If you don't want Recent Documents displayed, clear them out and use

```
echo "gtk-recent-files-max-age=0" >> ~/.gtkrc-2.0
```

---

