---
title: "I do not want to see icons, only the wallpaper..."
date: 2006-08-17
forum: Desktop Environments
---

### Post by leo_m on 2006-08-17
If I would like to see icons, I can navigate to the Desktop folder.  I do not want the icons in ~/Desktop folder to appear in front of the wallpaper.  At the same time, I do not want to delete those icons form the ~/Desktop folder either.

---

### Post by flaming_monkey on 2006-08-17
open a terminal and type:
```
gconf-editor
```
then navigate to apps > nautilus > desktop, there you can un tick icons that appear on your desktop.

---

### Post by Ramses de Norre on 2006-08-17
```
gconf-editor /apps/nautilus/preferences
``` and uncheck "show_desktop", I'm not sure about the effect and I'm on fluxbox now so I can't try but it might do what you want.

Otherwise: maybe you can rename Desktop to desktop and make an empty Desktop folder.. I don't think you can just change the desktop path..
But try my first suggestion first;)

---

### Post by leo_m on 2006-08-17
the gconf-editor method worked.  Thanks.

---

### Post by ardchoille on 2006-08-17
> **Ramses de Norre said:**
> ```
gconf-editor /apps/nautilus/preferences
``` and uncheck "show_desktop", I'm not sure about the effect and I'm on fluxbox now so I can't try but it might do what you want.



What that does is stops nautilus from showing the desktop (icons, desktop right-click menu). I use this method to keep nautilus from showing desktop icons and the desktop right-click menu because I use openbox as my window manager in gnome and I need the openbox desktop menu.

If someone wants to get rid of the desktop icons and keep the desktop right-click menu, it's probably best to go into gconf editor and un tick the icons they don't want.

---

### Post by Chemroydal Tissue on 2006-08-19
> **ardchoille said:**
> What that does is stops nautilus from showing the desktop (icons, desktop right-click menu). I use this method to keep nautilus from showing desktop icons and the desktop right-click menu because I use openbox as my window manager in gnome and I need the openbox desktop menu.

If someone wants to get rid of the desktop icons and keep the desktop right-click menu, it's probably best to go into gconf editor and un tick the icons they don't want.

Quick question: How do I get the right-click menu back?

---

### Post by Ramses de Norre on 2006-08-19
Recheck the "show_desktop" option..
And I use fluxbox and I just changed every instance of "nautilus" in my menu into "nautilus --no-desktop", that way nautilus still takes care of the desktop in my gnome and compiz sessions.

---

### Post by Chemroydal Tissue on 2006-08-20
> **Ramses de Norre said:**
> Recheck the "show_desktop" option..
And I use fluxbox and I just changed every instance of "nautilus" in my menu into "nautilus --no-desktop", that way nautilus still takes care of the desktop in my gnome and compiz sessions.

Er, tried that, of course. :p Didn't work.

---

