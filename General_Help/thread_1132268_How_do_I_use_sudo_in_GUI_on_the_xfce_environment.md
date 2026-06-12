---
title: "How do I use sudo in GUI on the xfce environment?"
date: 2009-04-21
forum: General Help
---

### Post by translucent juicebox on 2009-04-21
I did a search and found results for Gnome, and KDE, but no Xfce.  For some tasks, I can't do them in the GUI because I need to use sudo, is there an equivalent to typing sudo before a command in the terminal for the GUI?  

For example, if I want to delete a file that requires root privileges to alter, I have to open terminal and do it from there, because If I try to rightclick and press delete in the menu, the delete  button is grayed-out because I don't have the privileges to do so.  How would I use sudo in GUI, so I can just press the delete button instead of going to the terminal?

---

### Post by sisco311 on 2009-04-21
You can run your file manager as root. Press Ctrl+Alt+F2 or open a terminal and type:
```
gksu thunar
```

BE CAREFUL, as root you can delete anything.
DON'T delete system files or your OS. :)

CLOSE the file manager immediately after you're done.

---

### Post by jsowoc on 2009-04-21
The command to execute a graphical application (both in Gnome and in XFCE) is "gksudo". To get a GUI file manager as root, simply type: "gksudo thunar".

Cheers.

---

### Post by Ptero-4 on 2009-04-21
Use gksudo (this is what gnome uses).

---

### Post by translucent juicebox on 2009-04-21
Thanks :), I didn't know that Gnome used the same command as Xfce, gksudo was exactly what I was looking for.

---

### Post by sisco311 on 2009-04-21
gksu (gksudo is just a symbolic link to gksu) is a GTK+ frontend for su and sudo. 
Both GNOME and Xfce are based on GTK+.


[http://en.wikipedia.org/wiki/GTK]("http://en.wikipedia.org/wiki/GTK")

---

