---
title: "GDM crashing on startup"
date: 2018-04-20
forum: Desktop Environments
---

### Post by Geosearchef on 2018-04-20
I'm using Ubuntu Gnome 16.04. After installing an update (nvidia driver and kernel update), my Desktop Environment stopped working. When starting the system, gdm tries to start but fails to do so which results in the monitor flickering at 0.5 Hz. If I uninstall (using TTY, which is very hard to access as gdm tries restarting all the time) the nvidia driver, the flickering increases to 5-10 Hz.

Reinstalling the nvidia driver fixed the
```
Failed to initialize the NVIDIA kernel module
```
error in the xorg log.

The problem of crashing gdm/xserver persisted.
Dmesg output can be found here: [URL="https://geosearchef.de/dmesg.log"]https://geosearchef.de/dmesg.log
[/URL]Syslog after enabling gdm debug logging: [https://geosearchef.de/gdmSyslog.log](https://geosearchef.de/gdmSyslog.log)

---

### Post by Geosearchef on 2018-04-20
Reinstalling gdm3 did it.

---

