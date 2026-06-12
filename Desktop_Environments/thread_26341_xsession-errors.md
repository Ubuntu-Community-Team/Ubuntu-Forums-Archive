---
title: "xsession-errors"
date: 2005-04-12
forum: Desktop Environments
---

### Post by strawberry on 2005-04-12
There is the copy of the first few lines of my .xsession.errors file:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xxxx"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5699
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

(gnome-panel:5804): GLib-GObject-CRITICAL **: g_object_unref: assertion `object->ref_count > 0' failed

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030

** (gnome-cups-icon:5816): WARNING **: failed request with status 1030
The 'gnome-cup-icon' line is repeated several times. (cc. on 60kB)

How can I avoid this error message? 

Thnx in advance any help.

---

### Post by strawberry on 2005-04-13
I've found this clue in the net:
> gnome-cups-icon is quering every 5 seconds the cups daemon.
gnome-cups-icon is started by default by gnome-session. To disable
it delete the lines regarding gnome-cups-icon from /usr/share/gnome/default.session.
So it solved this matter but I should check the reason...
 8-)

---

