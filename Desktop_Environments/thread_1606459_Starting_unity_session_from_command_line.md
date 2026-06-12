---
title: "Starting unity session from command line?"
date: 2010-10-26
forum: Desktop Environments
---

### Post by debb1046 on 2010-10-26
Is there a way to start a unity session from the command line? I am running maverick in chroot, therefore cannot start gdm. That is to say: log out, choose session type, log back in, is not possible. startx starts a regular gnome session, as does gnome-session

---

### Post by Halverneus on 2010-11-16
Ctrl+Alt+F1
login name
password

xinit -- :1

(In the console window that pops up):
    unity

You can toggle back to your original desktop with Ctrl+Alt+F7 and back to Unity with Ctrl+Alt+F8

---

