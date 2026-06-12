---
title: "sessions do not start op"
date: 2007-05-14
forum: Desktop Environments
---

### Post by totoubunturo on 2007-05-14
I receive this message error
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
and this is my xsession-errors file
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/username-desktop:/tmp/.ICE-unix/10381
Initializing gnome-mount extension

(update-notifier:10456): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
thanks in advance:)

---

