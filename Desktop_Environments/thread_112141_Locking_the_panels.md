---
title: "Locking the panels?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by xenoxaos on 2006-01-03
I have a Ubuntu box set up for my grandfather. He seems to have no problem using it at all. Only one problem: he has a tendency to remove something from the panels..or removes the panel/menu all together.  is there any way to change it so that he can't change the panels.  Currently, the way I have to fix it, is I tar balled his home directory and when he screws it up I just untar it and overwrite all the files.  Since this seems to do it....is there a way to remove write permissions on the files that are the taskbar...and if so...which files are they???

-Mike

---

### Post by Sef on 2006-01-03
maybe you could disable the opposite mouse button or change it, so it doesn't bring up the menu.

---

### Post by xenoxaos on 2006-01-03
Nah....He'd find a way to kill it somehow.  Anyways my dad goes over there and he uses the right click.

---

### Post by brallan on 2006-09-21
yeah it would really be great to know how to solve this problem. if anyone understands how the gnome panel works and can tell us which files are involved i'd really appreciate it. 

And on a more general vein, if there is an easy way to investigate which files a specific program writes to (while running it) that would be good to know, as well.

---

### Post by brallan on 2008-05-10
hit Alt-F2 and run gconf-editor

when you run it navigate to

apps->panel->global

under lock_down click the checkbox

and restart gnome with Ctrl-Alt-Backspace

much thanks to ##gnome and #ubuntu on irc.freenode.net for help with this one

---

