---
title: "Ubuntu 18.04 running LightDM, light-locker won't start"
date: 2018-06-05
forum: Desktop Environments
---

### Post by rwalkerIII on 2018-06-05
Running LightDM on Ubuntu 18.04.  This is a 64-bit desktop server with 32GB RAM and  Intel Core i7-6700 4 core, 8 threads
      Linux walkubu 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Video card:
sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: GM206 [GeForce GTX 960]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:131 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:c0000-dffff


Have all GDM screensaver settings off.
     gsettings get org.gnome.desktop.screensaver idle-activation-enabled 
     false

     gsettings get org.gnome.settings-daemon.plugins.power active 
     false

When I run light-locker from my user (not sudo):

light-locker --debug
[gs_debug_init] gs-debug.c:106 (09:09:37):	 Debugging enabled
[main] light-locker.c:142 (09:09:37):	 initializing light-locker 1.8.0
[main] light-locker.c:164 (09:09:37):	 Platform:
gtk:        3
systemd:    yes
ConsoleKit: yes
UPower:     yes
[main] light-locker.c:196 (09:09:37):	 Features:
lock-after-screensaver: yes
late-locking:           yes
lock-on-suspend:        yes
lock-on-lid:            yes
settings backend:       GSETTINGS
[main] light-locker.c:198 (09:09:37):	 lock after screensaver 20
[main] light-locker.c:199 (09:09:37):	 late locking 0
[main] light-locker.c:200 (09:09:37):	 lock on suspend 1
[main] light-locker.c:201 (09:09:37):	 lock on lid 0
[main] light-locker.c:202 (09:09:37):	 idle hint 0
[query_session_id] gs-listener-dbus.c:2101 (09:09:37):	 org.freedesktop.login1.NoSessionForPID raised:
 PID 5982 does not belong to any known session


[init_session_id] gs-listener-dbus.c:2193 (09:09:37):	 Got session-id: (null)
[query_sd_session_id] gs-listener-dbus.c:2177 (09:09:37):	 Couldn't determine our own sd session id: No data available
[init_session_id] gs-listener-dbus.c:2198 (09:09:37):	 Got sd-session-id: (null)
[init_seat_path] gs-listener-dbus.c:2279 (09:09:37):	 Got seat: /org/freedesktop/DisplayManager/Seat0
[gs_listener_delay_suspend] gs-listener-dbus.c:449 (09:09:37):	 Delay suspend

** (light-locker:5982): WARNING **: 09:09:37.118: screensaver already running in this session

There is a Gnome screensaver running that I don't know how to disable:
rwalk     1729  1032  0 08:03 ?        00:00:00 /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy

How do I get light-locker working?

---

### Post by again? on 2018-06-09
What session are you trying to run it in?
Is it already running?
```
ps aux | grep [l]ight-locker
light-locker-command --lock
```

---

### Post by greyhatbbx on 2018-12-23
i dont use light locker any more. xscreenseaver do the job.

---

