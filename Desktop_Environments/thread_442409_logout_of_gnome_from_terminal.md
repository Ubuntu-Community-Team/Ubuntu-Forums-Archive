---
title: "logout of gnome from terminal"
date: 2007-05-13
forum: Desktop Environments
---

### Post by aanderse on 2007-05-13
so you know the "quit" or "logout" or "shutdown" buttons that can appear in your system menu?  are they a program which i can just call from the terminal, or call from somewhere other than the system menu?

---

### Post by Mr Greencastle on 2007-05-13
Are you running Xgl with Gnome? It could be a glitch with that similar to the reset/shutdown thing.

If your running Xgl, try adding this to your startxgl.sh script

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"


Edit: haha I realize what your asking now, far from what I posted :P

---

### Post by finer recliner on 2007-05-13
to shutdown/restart the comp from terminal

```

man shutdown

```

---

### Post by aanderse on 2007-05-13
shutdown requires you to be the root user to use it.  i'm looking to make a menu item in the xfce menu to directly shut the computer down or directly log out.  gnome has these menu items ... i'm just wondering what command they are actually calling, i want to copy the buttons and put them as a menu item.

---

