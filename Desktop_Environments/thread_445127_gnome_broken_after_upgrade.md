---
title: "gnome broken after upgrade"
date: 2007-05-15
forum: Desktop Environments
---

### Post by ugarth on 2007-05-15
Oh well, I just did a apt-get upgrade, using 6.10, and after rebotting my pc, I can't login to gnome. The normal user accounts screen pops up, but if I try to log in I get a error popup which cuickly dissapears and gnome reboots.
My.xsession-errors contains
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jce"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mors:/tmp/.ICE-unix/4581
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
X connection to :0.0 broken (explicit kill or server shutdown).
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```
I've used both the xorg.conf file after the installation and the backup.
I'm using beryl too, but I don't know how to disable it from the console.

I eagerly wait your assitance... :(

edit: I found the problem partially. It's beryl. I disabled it and I'm able to log into gnome just fine.
However, if I try to use wine or boot beryl gnome will restart.

---

