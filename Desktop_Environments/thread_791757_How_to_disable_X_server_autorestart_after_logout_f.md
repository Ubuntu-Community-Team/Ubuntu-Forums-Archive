---
title: "How to disable X server autorestart after logout from Gnome"
date: 2008-05-12
forum: Desktop Environments
---

### Post by vrybas on 2008-05-12
Hi, everyone.
Sometimes I need to shut down Gnome and Xserver and leave only command line for my server work. But when i'm leaving Gnome with
```
gnome-session-save --kill --silent
```
or stopping X with Ctrl+Alt+Backspace combination
it brings me to tty1, but afer a few seconds Gnome(and X) starts again with graphical Welcome screen and asking me to log in.
So, is there any way to disable that autorestart? I'm sure when I'll need it I'll start it with
```
sudo gdm
```

Thank's for your help.

SOLVED:

Don't use GDM. Use xinit

In your home directory create .xinitrc file with 

gnome-session

and use xinit from console to start Gnome. When you will logout - it won't start X automatically

---

