---
title: "Login problem w/ kernel 3.13.0.49 generic"
date: 2016-03-14
forum: Desktop Environments
---

### Post by nibal on 2016-03-14
Hi,

 I'm using 2 kernels in my Ubuntu 14.04. A custom llt 3.16 kernel and a generic 3.13.0.49-generic as failsafe. Doing most of my work in the llt kernel. I use this scenario for the past year with no problems. Have freezed updates after getting the gemeric kernel, because they mess up my custom kernel :(

Last week, and without any major changes, the generic failsafe kernel stopped logging me in. :( These are the relevant syslog entries:

Mar 14 05:49:14 DrWho colord: device removed: xrandr-Goldstar Company Ltd-W2286-718564
Mar 14 05:49:14 DrWho colord: Profile removed: icc-217075e2b43881773bd3a1eaa2bcb349
Mar 14 05:49:15 DrWho dbus[970]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Mar 14 05:49:15 DrWho dbus[970]: [system] Successfully activated service 'org.freedesktop.systemd1'
Mar 14 05:49:16 DrWho gnome-session[3420]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Mar 14 05:49:21 DrWho colord: Device added: xrandr-Goldstar Company Ltd-W2286-718564
Mar 14 05:49:21 DrWho colord: Automatic metadata add icc-217075e2b43881773bd3a1eaa2bcb349 to xrandr-Goldstar Company Ltd-W2286-718564
Mar 14 05:49:21 DrWho colord: Profile added: icc-217075e2b43881773bd3a1eaa2bcb349

My custom kernel has no problems with login. Any help will be appreciated.

TIA
Nikos

---

