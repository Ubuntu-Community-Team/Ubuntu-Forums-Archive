---
title: "menu panel don't show the icons"
date: 2008-03-09
forum: Desktop Environments
---

### Post by guimenez on 2008-03-09
hello

my menu in gnome don't show the icons after the text

ex: icon Applications
ex: icon Local
ex: icon System

thanks

---

### Post by soldats on 2008-03-09
The menu is generated partially from .desktop files which have paths to icons that should be used. I'm not sure about Gnome but I'd suggest looking somewhere in /usr/share/app* maybe. Look for the .desktop files and see if icons are in the text files. If so make sure the paths to the icons are correct. Its the only solution I see since i havent used Gnome in a long time. Hope this helps.

---

### Post by guimenez on 2008-03-09
Thanks for replying

i can't find any solution. if a create a new user the icons in menu bar are OK, but in my user they disappear :(

---

