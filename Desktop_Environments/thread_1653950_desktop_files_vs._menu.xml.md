---
title: "desktop files vs. menu.xml"
date: 2010-12-27
forum: Desktop Environments
---

### Post by MichaelBurns on 2010-12-27
Apparently, there are two ways to make a menu item: create a .desktop file for it in the /usr/share/applications/ directory, or add an entry for it in the /etc/xdg/xfce4/desktop/menu.xml file.  Is the choice just a matter of preference, or do these two approaches provide different functionality?

---

### Post by mcduck on 2010-12-27
.desktop files are a common standard between different desktop environments, so creating a menu entry that way would work no matter if you use XFCE, Gnome, KDE or some other DE/window manager that uses the standard.

They also support internationalization and other features like that.

Adding the entry to XFCE4's own menu.xml will, of course, only work for XFCE4.

If you are not creating installer for a program but instead just wish to modify your current menu, and you only use XFCE4 and know you are not going to install any other environment in the future, then it of course makes no difference which way you use.

---

### Post by MichaelBurns on 2010-12-27
That makes perfect sense.  Thank you.  BTW, I only read about the menu.xml file online (searching for how to tweak my menus), but when I finally tried to open 'er up, I don't even seem to have that on my system, and instead my system just uses the .desktop files anyway.

---

