---
title: "XMMS2 issue"
date: 2009-02-15
forum: General Help
---

### Post by fearful on 2009-02-15
I can't seem to find the solution for this anywhere but I'm getting this error when I try to start xmms2.
> benjamin@benjamin-laptop:~$ xmms2d
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
ERROR: ../src/xmms/ipc.c:938: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-benjamin'.
FATAL: ../src/xmms/main.c:484: IPC failed to init!


It's really annoying, any suggestions please!! Much appreciated
Thanks

---

### Post by fearful on 2009-02-15
Any help for this?

---

### Post by stucky on 2009-02-22
Same issue here.

---

### Post by stucky on 2009-02-22
Got is solved on mine. Looks like this is the error it throws if the daemon is already running. Check in something like htop and kill the process if it's there. Then just run xmms2-launcher to restart. Then you shouldn't get the errors.

Would it really have been that tough to have it display a useful error message?

---

