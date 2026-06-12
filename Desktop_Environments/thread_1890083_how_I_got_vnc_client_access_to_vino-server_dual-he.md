---
title: "how I got vnc client access to vino-server dual-head working cleanly"
date: 2011-12-02
forum: Desktop Environments
---

### Post by tazzarias on 2011-12-02
I wanted to share the work I did, perhaps it'll help someone else out there.

summary of my setup:
pc with ATI radeon video card
dual-head setup with desktop spanning, both monitors are 1280x1024
ubuntu 11.04
vnc server: vino-server
vnc client: tightvnc

summary of problem:
connecting tightvnc client to vino-server with dual-head monitor setup led to many artifacts and problems with display drawing that rendered dual-head unusable.  Initially my workaround was to undo the dual-head config to single-head config.

final solution:
After doing a lot of research, I learnt that the even though xorg.conf is deprecated in 11.04 and onward, the settings therein are still in use at some level if the file exists in /etc/X11/xorg.conf

I removed /etc/X11/xorg.conf (of course, I made a backup first), and restarted my X server.  I then re-enabled the dual-head monitor configuration.

Thereafter, I can use tightvnc to connect to my dual-head unbuntu workstation with vino-server and it is completely issue free.

Not sure if other clients than tightvnc would work as well, but this worked for me.

Cheers, Tazzarias

---

