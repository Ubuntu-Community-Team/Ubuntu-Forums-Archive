---
title: "System hang caused by kmail"
date: 2012-01-11
forum: Desktop Environments
---

### Post by pwabrahams on 2012-01-11
I've been fiddling with the kmail folder structure in order to recover some old messages. At one point I decided to quit kmail and restart it.  Then my system ground to a halt.  The desktop environment froze, so I tried logging out.  That got stuck, so I tried going to a virtual terminal.  Shortly after that, the login screen came up on its own and the system was fully wedged; capslock wasn't working and only powering down would get me out.

Perhaps I made some mistakes with my kmail manipulations, but this seems like an overreaction!!  I looked in the system log and discovered that about the time of the crash, I was getting these repeated messages:

```
Jan 10 19:53:46 pwa-K60IJ dbus[994]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jan 10 19:53:46 pwa-K60IJ dbus[994]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jan 10 19:59:46 pwa-K60IJ dbus[994]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jan 10 19:59:46 pwa-K60IJ dbus[994]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jan 10 20:05:46 pwa-K60IJ dbus[994]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jan 10 20:05:46 pwa-K60IJ dbus[994]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Ja
```

There's surely some kind of bug here, but I don't know how to collect enough useful information to enable anyone to guess what it might be.  I don't even know how or where to report it.

---

