---
title: "Tilt wheel quit working"
date: 2009-08-31
forum: Desktop Environments
---

### Post by fwiffo on 2009-08-31
Recently, after a reboot, suddenly the tilt wheel on my mouse (Logitech G5) just stopped working. I tried xev, but it doesn't show any event at all for the tilt, although the scroll wheel and all the other mouse buttons seem to work fine. It's been working fine for a long time. Was there a recent upgrade that changed something with this? Shouldn't it at least show an event in xev?

I have Kubuntu Gutsy 7.10 (have held off on upgrading because of a bad experience with an upgrade on a different computer).

---

SOLUTION:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 
```

---

### Post by drbcladd on 2009-09-02
Not sure if it is related but a sudden drop in some button sounds similar to this thread: the notifier is stealing events.

[http://ubuntuforums.org/showthread.php?t=1256008](http://ubuntuforums.org/showthread.php?t=1256008)

---

### Post by fwiffo on 2009-09-03
Hear Ye, Hear Ye! Let it be known throughout the internets, that drbcladd is full of win.

---

