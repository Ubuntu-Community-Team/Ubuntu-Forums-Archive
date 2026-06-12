---
title: "Screensaver + lock-screen works, but idle time not detected"
date: 2010-12-06
forum: Desktop Environments
---

### Post by jedibrand on 2010-12-06
I am running 10.04 (i686) inside kvm-qemu client. The host is a headless 10.04 (x64).

The issue is that the screensaver does not activate after a certain period of idle time (1 min). I can successfully activate the screensaver by running gnome-screensaver-command -a. It appears, then, that idle time is not being registered correctly.

There are some very sporadic logs in daemon.log:

```
./daemon.log.1:Dec  1 11:01:24 myserver gnome-session[2166]: WARNING: GSIdleMonitor: IDLETIME counter not found
./daemon.log.1:Dec  2 12:35:53 myserver gnome-session[19953]: WARNING: GSIdleMonitor: IDLETIME counter not found
./daemon.log.1:Dec  3 09:43:39 myserver gnome-session[6771]: WARNING: GSIdleMonitor: IDLETIME counter not found
./daemon.log.1:Dec  3 22:33:21 myserver gnome-session[18819]: WARNING: GSIdleMonitor: IDLETIME counter not found
./daemon.log:Dec  6 11:07:16 myserver gnome-session[4634]: WARNING: GSIdleMonitor: IDLETIME counter not found
```

gnome-settings-daemon is running fine, btw. As well, I access the qemu client via nomachine client, and run freenx-server on the VM.

---

### Post by jedibrand on 2010-12-21
bump.

---

