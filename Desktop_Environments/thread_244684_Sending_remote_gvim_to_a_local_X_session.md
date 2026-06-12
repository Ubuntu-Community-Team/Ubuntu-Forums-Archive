---
title: "Sending remote gvim to a local X session"
date: 2006-08-26
forum: Desktop Environments
---

### Post by believekevin on 2006-08-26
I have a headless server and I'd like to use gvim rather than vim.

Steps I've already gone through:

Edit /etc/gdm/gdm.conf : DisallowTCP=false
Restarted X
LOCAL: xhost +remote_server
REMOTE: export DISPLAY=###.###.###.###:0.0

Here's the error:

me@remote_server:~$ xclock
Error: Can't open display: ###.###.###.###:0.0

What am I missing?

---

### Post by believekevin on 2006-08-26
Also...

Local machine is running a veteran Breezy
Remote is running Dapper (Xubuntu server install)

---

