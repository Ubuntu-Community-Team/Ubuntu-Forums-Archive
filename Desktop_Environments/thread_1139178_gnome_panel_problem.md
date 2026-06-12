---
title: "gnome panel problem"
date: 2009-04-26
forum: Desktop Environments
---

### Post by beil on 2009-04-26
i have problem with gnome-panel i can`t move panel ,add new panel , add apps when click right mouse i have only help and about gnome panel

---

### Post by ryno519 on 2009-04-26
Looks like it might be locked down. Try opening a terminal and running 'gconf-editor'. There will be a tree list on the left. Open 'apps->panel->global' and there should be a parameter named "logged_down". If it's checked, uncheck it.

---

### Post by beil on 2009-04-27
10x

---

