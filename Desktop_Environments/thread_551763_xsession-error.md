---
title: "xsession-error"
date: 2007-09-15
forum: Desktop Environments
---

### Post by Micha401 on 2007-09-15
:confused:  Yet another strike of the 10-seconds-error. System ubuntu 7.04, Gnome, packages up to date. I can log in into Gnome only with a secure session. Within, it seems that all progs and demons work well.
My ~/.xsession-errors file is
------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "michael"
/etc/gdm/Xsession: Beginning session setup...
bind: Permission denied 
-----------------
From all previous posts I couldn't figure out a solution. .ICEAuthority  and .XAuthority permissions are OK, i. e. user.user. Deleting both files didn't help.
Strange: "bind: Permission denied". I haven't set up bind.

I would be very glad if I get a solution.

BTW: It's a problem striking Ubuntu/Gnome since 2005. So I wonder if a general solution/bug fix is available.

And, why did this happen?

---

