---
title: "how to add wine shortcut in xfce menu?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-11-08
i installed a windows program using wine, how do i add it to the xfce menu? i tried to use the menu editor and i put a shortcut with this command 


wine "C:\Program Files\....etc.exe"

but it wont show up in the xfce menu...

---

### Post by DarkManX4lf on 2005-11-09
anyone?

---

### Post by aysiu on 2005-11-09
I don't know. That's the one thing that bothers me with XFCE. Try as I might to use the "menu editor," my changes just don't show.

You can, however--in the "window manager settings"--define keyboard shortcuts for commands.

---

### Post by davebgimp on 2008-03-16
In a terminal, type:
**xfce4-menueditor**

Add an entry, name it utorrent and in the command field, put:

**wine "/home/[user]/.wine/drive_c/Program Files/uTorrent/uTorrent.exe"**

Replace "[user]" with your own username.

Save the menu and it should work.

---

