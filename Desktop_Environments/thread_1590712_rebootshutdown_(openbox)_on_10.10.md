---
title: "reboot/shutdown (openbox) on 10.10"
date: 2010-10-08
forum: Desktop Environments
---

### Post by ADcomp on 2010-10-08
Hello,

On ubuntu 10.04 (openbox as WM) I used these commands to reboot/shutdown :

```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
```
```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

But they don't work anymore (because no HAL in 10.10, right?). How can do the same stuff on 10.10 ? ( no "sudo shutdown .." without pwd )


ps: sorry for my poor english

---

### Post by hhh on 2010-10-08
[http://urukrama.wordpress.com/openbox-guide/#shutdown2](http://urukrama.wordpress.com/openbox-guide/#shutdown2)

---

### Post by ADcomp on 2010-10-08
Hi hhh,

Forgot to say I already try with gdm-control .. But it doesn't work. openbox'logout is ok , but gdm doesn't reboot/shutdown.

Thanks.

---

### Post by hhh on 2010-10-08
What about the "Other Options" part of that same section in urukrama's guide?

---

### Post by ADcomp on 2010-10-08
@hhh : sure , "sudo shutdown .." (without pwd) does the job. But I'm looking for something more user friendly. Btw, I don't know why gdm-control doesn't work.

---

### Post by ADcomp on 2010-10-11
ok .. finally found it!

To suspend:

```
dbus-send --system --print-reply  --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

To hibernate:

```
dbus-send --system --print-reply  --dest=org.freedesktop.UPower /org/freedesktop/UPower  org.freedesktop.UPower.Hibernate
```

To reboot:

```
dbus-send --system --print-reply  --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager  org.freedesktop.ConsoleKit.Manager.Restart
```

To halt:

```
dbus-send --system --print-reply  --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager  org.freedesktop.ConsoleKit.Manager.Stop
```

---

### Post by Rodney9 on 2010-10-27
> **ADcomp said:**
> ok .. finally found it!

To suspend:

```
dbus-send --system --print-reply  --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

To hibernate:

```
dbus-send --system --print-reply  --dest=org.freedesktop.UPower /org/freedesktop/UPower  org.freedesktop.UPower.Hibernate
```

To reboot:

```
dbus-send --system --print-reply  --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager  org.freedesktop.ConsoleKit.Manager.Restart
```

To halt:

```
dbus-send --system --print-reply  --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager  org.freedesktop.ConsoleKit.Manager.Stop
```

Thank You, I'm using Openbox on Xubuntu 64bit 10.10

---

