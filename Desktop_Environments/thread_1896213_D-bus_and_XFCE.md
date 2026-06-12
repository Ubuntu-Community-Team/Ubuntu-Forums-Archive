---
title: "D-bus and XFCE"
date: 2011-12-16
forum: Desktop Environments
---

### Post by JasonFWard on 2011-12-16
Is dbus part of XFCE, my research seems to say it is.

But I'm getting some errors suggesting applications can't talk to dbus.

Is there anyway for me to check the health of dbus?

---

### Post by 2F4U on 2011-12-16
I am pretty sure it is part of Xubuntu but it seems that you have kind of a custom installation. Is that true? You can also check what

whereis dbus-launch

returns.

---

### Post by JasonFWard on 2011-12-16
Default install from Xbuntu ISO.

Am running XFCE desktop though, not Xbuntu as Xbuntu desktop really doesn't like my 3 monitor setup, but XFCE is fine with it.

The installation is only a few days old, and as yet has very little installed that isn't default.

Only thing I've uninstalled is file-roller as I find it way too bug ridden to be usable.

```
jason@Penny:~$ whereis dbus-launch
dbus-launch: /usr/bin/dbus-launch /usr/share/man/man1/dbus-launch.1.gz
```

Is there a way for me to test is dbus is working properly?

Hmmmm, is this normal?```
jason@Penny:~$ ps -A | grep 'dbus'
  822 ?        00:00:19 dbus-daemon
 1476 ?        00:00:00 dbus-launch
 1477 ?        00:00:04 dbus-daemon
10283 ?        00:00:00 dbus-launch
10284 ?        00:00:00 dbus-daemon

```In XFCE's taskmanager they only show up once with PID's of 1476 and 1477.

---

### Post by JasonFWard on 2011-12-16
Right, so the sbackup log says```
(process:25941): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Unable to autolaunch a dbus-daemon without a $DISPLAY for X11

(process:25941): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
```
and
```
No desktop session found
No desktop session found
No desktop session found
No desktop session found
No desktop session found
No desktop session found
Error while getting gconf setting: No D-BUS daemon running

Default value is used.
Error while setting gconf value: No D-BUS daemon running

Error can be safely ignored: setting is not being changed.
D-Bus session bus launched
	DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-UILWX7SkyX,guid=01fed7d0d52030c991dc93320002d272
	DBUS_SESSION_BUS_PID=25969
Attempt to launch indicator application (status icon).
No desktop session found
No desktop session found. Indicator application is not started.
```

I checked $DISPLAY```
jason@Penny:~$ echo $DISPLAY
:0.0
```

I wonder if this is something to do with the RandR error I get regularly.```
Xlib:  extension "RANDR" missing on display ":0.0".
```

Which is turn is something to do with my multi-monitor setup, but I've had that RandR error on previous installs where sbackup worked... so Im not sure.

---

### Post by 2F4U on 2011-12-16
Seems to be a bug. You may wish to add your information to the bug.

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/812940](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/812940)

---

### Post by JasonFWard on 2011-12-16
Hmmm, thanks for that.

The suggested work arounds are...not very helpful to say the least.

I also want to know why when the job is run manually it works great, but fails when cron runs it.

---

