---
title: "XGL session lasts less than 10 seconds"
date: 2007-09-02
forum: Desktop Environments
---

### Post by bohsocks on 2007-09-02
Hey... I've seen similar things posted here... but no resolutions to the problem.... 

I'm running Feisty with ATI cards and MergedFB.  I installed fglrx to see if I can get compiz-fusion working.

When I try to login to XGL, the session lasts less than 10 seconds, and I get this error:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0 Xservers" -h "" -l ":0" "rob"
/etc/gdm/Xsession : Beginning session setup...

Fatal sever error:
no screens found

(gnome-session:27704): Gtk-WARNING **: cannot open display:
```

I had written this down so I could type it, so if something doesn't look right I can re-try it and get the correct wording.

Please help :(

---

### Post by mobad on 2007-09-29
I have the same problem as you and sadly I have no fix.  But it may have something to do with dual monitors, if you have dual monitors enabled, then try disabling them.  It could also be a problem with the newer FGLRX drivers so try switching to the official ubuntu FGLRX restricted driver if you are using newer ones.  Also upgrading to Gusty did not solve this problem.

---

