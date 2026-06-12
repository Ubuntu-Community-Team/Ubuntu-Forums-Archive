---
title: "What is the gksudo window's class name?"
date: 2010-07-30
forum: Desktop Environments
---

### Post by Stuart P. Bentley on 2010-07-30
How can I get the window class info for the desktop-dimming window that comes up when gksudo is used?

---

### Post by hhh on 2010-07-30
I think it's gnome-keyring-prompt.

The way I got that was first to enter, for example, gksu gedit in the run dialog (Alt+F2). I use Xfce so I'm not sure if it's the same with Gnome, but the run dialog should keep a record of that entry in ~/.cache, so the next time you bring up the run dialog it's already filled in with that entry.

Next, I went to this page...
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)
.. and I copied the command for class into a terminal...
```
xprop WM_CLASS | cut -d\" -f2
```
When you enter it, your cursor changes to a crosshair. Now hit Alt+F2 and then enter to run gksu, and the dialog window opens. Click that window and the class appears in terminal.

HTH

---

