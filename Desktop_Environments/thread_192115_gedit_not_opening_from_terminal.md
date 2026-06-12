---
title: "gedit not opening from terminal"
date: 2006-06-08
forum: Desktop Environments
---

### Post by chaosblue on 2006-06-08
Hey all,

I've searched for a couple of days for this problem, but haven't quite seen anything like it.  I've been trying to edit files with gedit from the terminal, but every time I attempt to open something, I get
> gedit (19740): Gtk WARNING **: cannot open display:

The number varies every time I make an attempt.

I've tried using sudo and switching to root, but neither method works.  Neither does gksudo.  Help please?

Char

---

### Post by taurus on 2006-06-08
You need first log in to some type of window manager like Gnome, KDE, XFce, fluxbox, etc. first before you can run gedit!  You can't run it from a terminal (text base).  Therefore you have to use nano instead...

---

### Post by chaosblue on 2006-06-08
[QUOTE=taurus]You need first log in to some type of window manager like Gnome, KDE, XFce, fluxbox, etc. first before you can run gedit!  You can't run it from a terminal (text base).  Therefore you have to use nano instead...[/QUOTE]

Mmmm, not quite what I meant!  I'm running it from the desktop, trying to use the command line in the terminal window.  I can get gedit to open from the applications menu, but it only opens as read-only.

Char

---

