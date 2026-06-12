---
title: "gnome session won't login"
date: 2005-05-26
forum: Desktop Environments
---

### Post by bobgreen5s on 2005-05-26
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bobgreen5s"
/etc/gdm/Xsession: Beginning session setup...
Could not set mode 0700 on private per-user gnome configuration directory `/home/bobgreen5s/.gnome2_private/': Operation not permitted

```


This is the error message that I get when I try to login. It also said 'Your session only lasted less than 10 seconds.'


Any help would be appreciated

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=bobgreen5s]```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bobgreen5s"
/etc/gdm/Xsession: Beginning session setup...
Could not set mode 0700 on private per-user gnome configuration directory `/home/bobgreen5s/.gnome2_private/': Operation not permitted

```


This is the error message that I get when I try to login. It also said 'Your session only lasted less than 10 seconds.'


Any help would be appreciated[/QUOTE]
 What are permissions on this directory (i.e. output of ls-l /home/bobgreen5s/.gnome2_private/)
? And permisions of /home/bobgreen5s/ ?

If this is a new installation, you can just remove .gnome2_private directory - you have nothing to lose. It will be recreated at login. 

You can do it from text-based console (switch to it with Ctrl-Alt-F1, switch back with Alt-F7)

---

