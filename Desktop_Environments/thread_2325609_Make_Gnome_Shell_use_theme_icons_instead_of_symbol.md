---
title: "Make Gnome Shell use theme icons instead of symbolic"
date: 2016-05-23
forum: Desktop Environments
---

### Post by Imerion on 2016-05-23
I want to get rid of the ugly symbolic icons used in Gnome Shell and GTK3 themes and have them replaced with the icons from my actual selected theme.

I managed to do this for normal themes by adding "-gtk-icon-style: regular;" in the "gtk.css" of the theme. Save dialogs, Nautilus and other places now have the colorful icons I want.

Gnome Shell, however, seems harder. Any idea how I can make Gnome Shell use my icon theme instead of the built-in symbolic icons?

---

### Post by Joeb on 2016-05-25
Many icon themes include the gnome-shell icons and replace them automatically. If you are using a theme not designed for gnome-shell, then it is likely the theme doesn't include them and it is falling back to the original.  If you could determine what icons are currently being used from the default theme, you could copy the icons you want to use, renaming them in the process to the same name and place them in your current theme.  You'd probably have to restart gnome-shell for the changes to take effect.  Or, ask the theme developer to add the missing gnome-shell icons.

---

