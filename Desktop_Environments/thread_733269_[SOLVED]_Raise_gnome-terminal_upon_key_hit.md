---
title: "[SOLVED] Raise gnome-terminal upon key hit"
date: 2008-03-23
forum: Desktop Environments
---

### Post by crocowhile on 2008-03-23
I am a gnome user on ubuntu hardy, with compiz enabled.
Is there a way to associate a living instance of gnome-terminal to a specific key binding?
I know that by default compiz will open a new terminal window whenever I press Ctrl-Alt-X; what I would like to know, though, is if there is a way to associate a keybinding to raise an already existing terminal without opening a new one.

---

### Post by szim90 on 2008-03-23
Go to System > Preferences > Keyboard Shortcuts. You can then set a key to launch a terminal.

---

### Post by Tenken on 2008-03-23
There isn't a keybinding like that I know of, you best bet is probably to Alt+Tab to it.

---

### Post by spupy on 2008-03-23
The command is:
```
wmctrl -a qwe
```
and replace "qwe" with some string that appears in the window title of gnome-terminal.

---

### Post by crocowhile on 2008-03-24
Thanks! That will do it and much more.

---

