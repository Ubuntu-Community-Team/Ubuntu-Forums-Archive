---
title: "Cannot start automount daemon..."
date: 2006-09-20
forum: Desktop Environments
---

### Post by kszys on 2006-09-20
I have setup autofs to mount automagically remote filesystems over sshfs. This worked fine until recently. Now I cannot start the automount daemon at all :confused: 

It does not work either by running [FONT="Fixedsys"]/etc/init.d/autofs start[/FONT], nor by manually trying to start the automount daemon. Everything appears to be fine, there are no error messages logged in /var/log/messaages, yet the [FONT="Fixedsys"]ps aux | grep auto[/FONT] does not show the daemon to be running, nor there is any automagic mounting...

At the same time, I can mount manually the remote filesystems over sshfs just fine... It is just annoing to have to do it manually... 

Any ideas where to look?

Kszys.

---

### Post by kszys on 2006-09-21
Nobody could suggest anything...?
:confused:

---

