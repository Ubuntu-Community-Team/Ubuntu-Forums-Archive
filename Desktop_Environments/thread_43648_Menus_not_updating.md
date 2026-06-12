---
title: "Menus not updating"
date: 2005-06-22
forum: Desktop Environments
---

### Post by jesusrop on 2005-06-22
Hi all

I've noticed that when I install some applications, they don't appear in my GNOME menu (applications menu).

I've also noticed that all the .desktop files that those applications create are in ~/.gnome/apps, but the menu is not showwing them.

I don't know what to do to make those entries appear, because Smeg is not working propperly.

Thenks everybody

---

### Post by FLeiXiuS on 2005-06-22
Try giving this a shot.

$ sudo killall gnome-panel

This briefly restarts your gnome panels.  Hopefully this'll do the trick.

---

### Post by jesusrop on 2005-06-22
no...killall gnome-panel didn't fix the problem

any other solution?

---

