---
title: "Execute gnome-power-cmd.sh from PHP script"
date: 2008-10-01
forum: Desktop Environments
---

### Post by abePdIta on 2008-10-01
Hi everybody, sorry for my English!
I need to shutdown a computer using a PHP script.

If I execute 'sudo /sbin/shutdown -h now' it works, but I would like to use '/usr/bin/gnome-power-cmd.sh shutdown' to let Gnome power manager handle the event.
People say that this is the right way, to avoid filesystem corruptions and so on..

But '/usr/bin/gnome-power-cmd.sh' uses D-Bus to send the command to the power manager and it seems that PHP (Apache module) doesn't have access to the D-Bus session (the Gnome-power-manager one) because it says: "Failed to open connection to session message bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed."

Well, I know nothing about D-Bus..
Someone knows a way to get it working?

---

### Post by abePdIta on 2008-10-23
Ok! Founded a solution, thanks to [fede@E-pillole.com]("http://www.e-pillole.com/linux/post/69/cron-rhythmbox-scriptino-sveglia/").

```
#!/bin/bash

user=`whoami`
pid=`pgrep -u $user gnome-panel`

for dbusenv in $pid; do
	DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
	/proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
	
	DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
	/usr/bin/gnome-power-cmd.sh shutdown
done

exit 0
```

PHP calls this script and it just works..
Improvements are welcome!

---

### Post by Endolith on 2009-01-07
Hmmm... there are two commands on [https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager). Which is better?

  ```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
``````
gnome-power-cmd.sh reboot
```Which is more like the behavior of the *Restart* command in the System menu?  Is the first more cross-platform, or should we find whether the user is running Gnome or KDE first?

---

