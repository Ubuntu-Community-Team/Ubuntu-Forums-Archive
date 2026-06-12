---
title: "Cannot start X; x-session-manager symbol lookup error"
date: 2007-06-05
forum: Desktop Environments
---

### Post by lehrin on 2007-06-05
Alright, I'm reasonably comfortable around Linux, having used it on and off a bit for the last few years, but I'm not terribly knowledgeable about the structure of Gnome or X etc.

I upgraded a few things, namely aircrack-ng and the new DivX codecs last night and when i booted this morning, first I got an error saying "Error loading theme Human" and "unrecognised file format bottom_bar.svg" then it loaded a different looking login, with a big daisy on the bottom right corner, and when I try to log it it says "session lasted less than 10 seconds" with some other info, and refers me to .xsession-errors, which is posted below. 

I'm a little overwhelmed by that output, I tried to search for what I thought the key terms were but couldn't find anything that matched:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "lehrin"
/etc/gdm/Xsession: Beginning session setup...

***MEMORY-WARNING***: x-session-manager[5671]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: gconf-sanity-check-2[5716]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
SESSION_MANAGER=local/VAIOx:/tmp/.ICE-unix/5671
x-session-manager: symbol lookup error: x-session-manager: undefined symbol: gnome_keyring_daemon_set_display_sync

If anyone has any ideas about where to start, thanks in advance for any help.
-Lehrin

---

### Post by mbsullivan on 2007-09-05
bump.

---

### Post by mbsullivan on 2007-09-05
> I got an error saying "Error loading theme Human" and "unrecognised file format bottom_bar.svg" then it loaded a different looking login, with a big daisy on the bottom right corner

I was getting the same error (and, regrettably, the daisy as well).  Try the following:

```
sudo aptitude reinstall librsvg2-common librsvg2-2
```

I was getting slightly different x-session errors, though, so there may be some other underlying problem as well.

Hope this helps!
Mike

---

