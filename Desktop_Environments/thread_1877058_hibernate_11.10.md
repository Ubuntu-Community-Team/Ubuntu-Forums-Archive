---
title: "hibernate 11.10"
date: 2011-11-07
forum: Desktop Environments
---

### Post by giannig on 2011-11-07
Hi, I'm using ubuntu 11.10 with unity 2d, and the hibernate as non root doesn't work anymore (it did work in 11.04).
I've tried visudo and the solution highlighted below but it doesn't work either

visudo:
username  ALL = NOPASSWD: /usr/sbin/pm-hibernate, /usr/sbin/pmi, /usr/sbin/pm-is-supported, /usr/sbin/pm-powersave , /usr/sbin/pm-suspend , /usr/sbin/pm-suspend-hybrid 



[http://ubuntuforums.org/showthread.php?t=813387&highlight=pm-hibernate](http://ubuntuforums.org/showthread.php?t=813387&highlight=pm-hibernate)
#!/bin/bash # # gnome-power-control # Author: AgenT  case $1 in suspend) echo Suspending     dbus-send --print-reply \         --system \         --dest=org.freedesktop.DeviceKit.Power \         /org/freedesktop/DeviceKit/Power \         org.freedesktop.DeviceKit.Power.Suspend ;; hibernate) echo Hibernating     dbus-send --print-reply \         --system \         --dest=org.freedesktop.DeviceKit.Power \         /org/freedesktop/DeviceKit/Power \         org.freedesktop.DeviceKit.Power.Hibernate ;; *) echo Not supported command: '"'$1'"' echo Usage: $0 '<suspend|hibernate>' exit 1 ;; esac

---

