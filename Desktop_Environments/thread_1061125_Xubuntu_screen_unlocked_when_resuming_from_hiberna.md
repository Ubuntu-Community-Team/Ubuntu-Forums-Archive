---
title: "Xubuntu: screen unlocked when resuming from hibernate"
date: 2009-02-05
forum: Desktop Environments
---

### Post by draga on 2009-02-05
Hi. I've installed ubuntu and, then, "xubuntu-desktop" on my Acer Aspire one. It works like a charm, but I've a problem: when coming back from the "hibernate" status, no password gets asked. It works when suspending.
I've tried to add those lines:
```
for PID in `/usr/bin/pgrep xfdesktop`; do
DBUS_SESSION_BUS_ADDRESS=`(/bin/cat /proc/$PID/environ; /bin/echo)|/usr/bin/tr "\000" "\n"|/bin/grep DBUS_SESSION_BUS_ADDRESS|/bin/sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
LOGIN=`/bin/ps -ouser -p $PID --no-headers`
DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS /bin/su $LOGIN /usr/bin/xflock4
done

```
in /etc/acpi/hibernate.sh, as read in other older posts, but it didn't solve.
Any idea? XFCE on this hardware is better and faster, but I need the screen locked when resuming.
I've tried both with gnome-screensaver and xscreensaver with same results.

Thank you!

---

