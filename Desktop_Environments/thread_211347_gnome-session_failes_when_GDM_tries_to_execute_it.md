---
title: "gnome-session failes when GDM tries to execute it"
date: 2006-07-08
forum: Desktop Environments
---

### Post by mgor on 2006-07-08
yesterday everything worked fine. today when i started my laptop and tried logging into gnome i get an error saying that gnome-session failed to execute and i get a failsafe session instead. the strange thing is that if i execute `gnome-session' in xterm it starts without a problem.

i didn't do anything special yesterday, i think there was a couple of package updates, but i can't really remember what it was, one of the packages might have been libgtk-pixbuf-*.

~/.xsession-error (i added a couple of echo statements in /etc/gdm/Xsession for more verbose debug info):
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "micke"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: command are /usr/bin/gnome-session
/etc/gdm/Xsession: XKB are not in use
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator

```

i'm out of ideas of what i can be. ](*,)

---

