---
title: "Window access problems after remote vino session"
date: 2009-11-03
forum: Desktop Environments
---

### Post by MgFrobozz on 2009-11-03
In my ubuntu workstation, using gnome as a dm, I recently ran vino-preferences to enable remote desktop (allowing control, with a passwd). I then ran a remote desktop session from a windows machine for about 10 minutes, and then closed the remote session. 

When I resumed using my workstation through its console, I found I was unable to restore minimized windows (by clicking on the name of the window in the task bar, or by right-clicking and selecting maximize), and that using Alt-Tab to try to switch windows did not show the window. 

After I logged out and logged back in, and restored all the windows and then all the tabs in the console window, everything worked ok, but I'd hate to have to do that after every remote session.

Any ideas on how to prevent this, or an easier way to recover operation (other than logout/login) when it does occur?

> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

> dpkg --list | grep vino
ii  vino                                       2.26.1-0ubuntu1                           VNC server for GNOME

---

