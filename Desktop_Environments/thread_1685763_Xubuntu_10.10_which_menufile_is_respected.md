---
title: "Xubuntu 10.10 which menufile is respected?"
date: 2011-02-11
forum: Desktop Environments
---

### Post by Wellconnected on 2011-02-11
Dear All, 
I would like to edit the main menu. I have so far found:

/etc/xdg/menus/xfce-applications.menu
/etc/xdg/xdg-xubuntu/menus/xfce-applications.menu
/home/ed/.config/menus/xfce-applications.menu

...and none of these seem to be respected...

which one do I need to edit?!

E

---

### Post by Brandon Williams on 2011-02-12
If it exists at login, ~/.config/menus/xfce-applications.menu will be used. Otherwise, /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu will be used.

---

### Post by y6FgBn)~v on 2011-02-12
I found this wiki helpful, perhaps you will also;

[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

---

