---
title: "[SOLVED] Some Application menu icons are shown as folders."
date: 2008-11-22
forum: Desktop Environments
---

### Post by VictorR on 2008-11-22
After upgrade from 8.04 to 8.10 four icons in Application menu - Accessories, Games, Internet and Multimedia were replaced by folder icons. Changing icon theme does not solve the issue - these four are always like the default folder icon in Nautilus for the applied theme.
Couldn't find that anybody mentioned this strange issue.

The desktop environment - Gnome, and I also use Gnome Menu Extended, which created sub-menus for KDE and Office entries.

Not a big deal, but would thank if someone suggested how to fix this.

---

### Post by Linteg on 2008-11-22
Run alacarte (from a terminal or press Alt+F2 and type it in), and either edit the specific entries by right clicking them in the right list and pressing properties, or try restoring the menu to its default settings.

---

### Post by VictorR on 2008-11-22
Sounds funny, but alacarte couldn't open properties dialogue for those abovementioned menu entries (only).

Solved by installing the latest 0.9.2-1 version of Gnome Menu Extended from [http://www.gtk-apps.org/]("http://www.gtk-apps.org/content/show.php/Gnome+Menu+Extended+(Debian+Package)?content=73515")

---

