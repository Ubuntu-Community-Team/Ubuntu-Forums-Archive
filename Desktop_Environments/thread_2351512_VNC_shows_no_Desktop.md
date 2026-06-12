---
title: "VNC shows no Desktop"
date: 2017-02-04
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-02-04
Folks,

I use a a 16:04 Laptop to access a remote Raspberry Pi running Ubuntu Mate.

Mainly I use ssh but on occasions require Desktop viewing but for some reason VNC connection only gives a file manager.

I have no .Xresourses file and the content of xstartup in the .vnc folder is as follows;

```
#!/bin/sh


def
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
 
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &
gnome-session &



```

I'm obviously missing something.

Geffers

---

