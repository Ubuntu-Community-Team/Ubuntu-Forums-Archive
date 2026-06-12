---
title: "Menu Editor"
date: 2005-12-15
forum: Desktop Environments
---

### Post by johnhedge on 2005-12-15
Hi,

I'm having trouble with the menu. Specifically, I've used Add Applications to install Gambas. I rebooted expecting to see it under Applications/Programming but no luck.

Checking with Applications Menu Editor, sure enough Gambas is ticked sitting as a sub menu item to Programming but Programming isn't showing under Applications.

Q. How do I get a new menu item (Programming) to show?

TIA

John

---

### Post by cstudent on 2005-12-15
You could try in the terminal:

**killall gnome-panel**

Or log off and back on.

If that doesn't work try:

**sudo gedit /usr/share/applications/gambas.desktop**

and enter the following:

[B][Desktop Entry]
Name=Gambas
Exec=gambas
Icon=/usr/share/pixmaps/gambas.xpm
Terminal=false
Comment=Gambas Visual Basic
Type=Application
Categories=Application;Development;[/B]

---

### Post by johnhedge on 2005-12-16
Thanks for the suggestions but no result, I'm afraid.

I tried killall and rebooted.

The gambas.desktop had a number of [es_Es] which I removed and Categories only had Categories=Application; so I added Development;

I think my problem maybe more to do with 'Programming' the head menu item than Gambas. Can I get at 'Programming' through the command line config file?

I've also added/installed phppgadmin and pgadmin3 which don't show up anywhere.

Thanks for your assistance in this.

John

---

### Post by johnhedge on 2005-12-16
of course phppgadmin is a browser utility, sorry.

---

