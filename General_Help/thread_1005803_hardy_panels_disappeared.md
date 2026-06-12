---
title: "hardy panels disappeared"
date: 2008-12-08
forum: General Help
---

### Post by CEB2nd on 2008-12-08
My panels disappeared after installing the awn repos.  I tried
the alt-f2 but no box appeared, what happened?. Help! :confused:

---

### Post by MarblePanther on 2008-12-08
Have you tried right-click add panel?

---

### Post by ghantoos on 2008-12-08
If your are able to open a terminal, run:

```
gnome-panel
```Hope this helps,
Cheers,

---

### Post by MarblePanther on 2008-12-08
Do what ^ suggested or restart x if it doesn't work and login again

---

### Post by fooman on 2008-12-08
if you can't get a dialog box with alt-f2 and you can't get to a terminal,  try this:

press alt-ctrl-f1 to drop to a console session (no gui so remember the following).  log-in with your user name and password,  then type this command and press enter:

```
sudo apt-get install nautilus-open-terminal
```

once its done installing, reboot.  when you get back to the desktop,  right click anywhere on it and choose "open in terminal" from the menu.  in the terminal type or copy/paste:

```
gnome-panel &
```

press enter.

---

