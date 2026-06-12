---
title: "ubuntu Mate 386 - cant add battery monitor to panel"
date: 2018-05-22
forum: Desktop Environments
---

### Post by jay-mcml on 2018-05-22
greetings!
This is with a fresh install of 18.04 (Not an upgrade)
If I try to  'add to panel' the battery monitor item, nothing happens.

there is mate-power-manager in ps -ef output
and 
systemd[1]: Starting Daemon for power management...
dbus-daemon[624]: [system] Successfully activated service 'org.freedesktop.UPower'
 systemd[1]: Started Daemon for power management.
in syslog

nothing suspicious in dmesg or kern,lod

pakage installed:
i   wmbattery                                      - display laptop battery info, dockable in WindowMaker     


gkrellm    is    able to show battery power.

what's broke??

Thanks in advance,
Jay

---

### Post by kerry_s on 2018-05-22
mate is iffy, run-> killall mate-panel <-in terminal, don't worry it'll come right back.

---

