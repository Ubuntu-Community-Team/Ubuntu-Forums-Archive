---
title: "TightVNC Server on Ubuntu 18.04"
date: 2021-08-15
forum: Desktop Environments
---

### Post by stephenstark on 2021-08-15
[SIZE=2][FONT=arial]I am attempting to get TightVNC Server running on a headless Ubuntu 18.04 machine running the Unity desktop.  I am able to login using VNCViewer, but each time I get a blank Unity desktop and cannot right-click or launch anything.  Here is a copy of my current xstartup file:

[/FONT][/SIZE][COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]#!/bin/sh[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]export XKL_XMODMAP_DISABLE=1[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]export XDG_CURRENT_DESKTOP="GNOME-Flashback:Unity"[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]export XDG_MENU_PREFIX="gnome-flashback-"[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]unset SESSION_MANAGER[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]unset DBUS_SESSION_BUS_ADDRESS[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial][ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial][ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]xsetroot -solid grey[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]vncconfig -iconic &[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]gnome-panel &[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]gnome-flashback &[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]unity-settings-daemon &[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]metacity &[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times][SIZE=2][FONT=arial]nautilus &

What am I missing?

Thanks.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-08-16
What are you wanting to do on the remote system? There may be a sleeker solution to what you want to achieve which means that VNC simply isn't needed

---

### Post by ActionParsnip on 2021-08-16
This guide can help with VNC but just because you want to use a remote system in some way doesn't mean you should automatically grab VNC.
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
It's not always the best solution

---

