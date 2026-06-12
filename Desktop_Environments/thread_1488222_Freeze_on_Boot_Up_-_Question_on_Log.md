---
title: "Freeze on Boot Up - Question on Log"
date: 2010-05-19
forum: Desktop Environments
---

### Post by heitjer on 2010-05-19
When I shut down the machine yesterday all was well. Today I can not boot any more. I assume it may have been one of the updates from yesterday. 

Here are my questions:

1) Can I revert back to a state before yesterday? These are the logged upgrades from yesterday (dpkg.log). Any culprits in your mind?

```
2010-05-18 20:31:44 status half-installed spideroak 9643
2010-05-18 20:31:44 status triggers-pending man-db 2.5.5-1build1
2010-05-18 20:31:44 status half-installed spideroak 9643
2010-05-18 20:31:44 status triggers-pending menu 2.1.41ubuntu1
2010-05-18 20:31:44 status half-installed spideroak 9643
2010-05-18 20:31:46 status half-installed spideroak 9643
2010-05-18 20:31:47 status triggers-awaited menu 2.1.41ubuntu1
2010-05-18 20:31:47 status unpacked spideroak 9658
2010-05-18 20:31:47 status unpacked spideroak 9658
2010-05-18 20:31:47 upgrade xserver-common 2:1.6.0-0ubuntu14 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:47 status half-configured xserver-common 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status unpacked xserver-common 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status half-installed xserver-common 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status half-installed xserver-common 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status half-installed xserver-common 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status unpacked xserver-common 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:47 status unpacked xserver-common 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:47 upgrade xserver-xorg-core 2:1.6.0-0ubuntu14 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:47 status half-configured xserver-xorg-core 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status unpacked xserver-xorg-core 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status half-installed xserver-xorg-core 2:1.6.0-0ubuntu14
2010-05-18 20:31:47 status half-installed xserver-xorg-core 2:1.6.0-0ubuntu14
2010-05-18 20:31:48 status half-installed xserver-xorg-core 2:1.6.0-0ubuntu14
2010-05-18 20:31:48 status unpacked xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:48 status unpacked xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:48 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2010-05-18 20:31:48 status half-configured man-db 2.5.5-1build1
2010-05-18 20:31:48 status installed man-db 2.5.5-1build1
2010-05-18 20:31:48 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1
2010-05-18 20:31:48 status half-configured menu 2.1.41ubuntu1
2010-05-18 20:31:49 status installed menu 2.1.41ubuntu1
2010-05-18 20:31:50 startup packages configure
2010-05-18 20:31:50 configure spideroak 9658 9658
2010-05-18 20:31:50 status unpacked spideroak 9658
2010-05-18 20:31:50 status unpacked spideroak 9658
2010-05-18 20:31:50 status unpacked spideroak 9658
2010-05-18 20:31:50 status unpacked spideroak 9658
2010-05-18 20:31:50 status half-configured spideroak 9658
2010-05-18 20:31:50 status installed spideroak 9658
2010-05-18 20:31:50 status triggers-pending menu 2.1.41ubuntu1
2010-05-18 20:31:50 status triggers-awaited menu 2.1.41ubuntu1
2010-05-18 20:31:50 status triggers-pending libc6 2.9-4ubuntu6.1
2010-05-18 20:31:50 configure xserver-common 2:1.6.0-0ubuntu14.2 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status unpacked xserver-common 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status half-configured xserver-common 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status installed xserver-common 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 configure xserver-xorg-core 2:1.6.0-0ubuntu14.2 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status unpacked xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status unpacked xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status half-configured xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 status installed xserver-xorg-core 2:1.6.0-0ubuntu14.2
2010-05-18 20:31:50 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1
2010-05-18 20:31:50 status half-configured menu 2.1.41ubuntu1
2010-05-18 20:31:50 status installed menu 2.1.41ubuntu1
2010-05-18 20:31:50 trigproc libc6 2.9-4ubuntu6.1 2.9-4ubuntu6.1
2010-05-18 20:31:50 status half-configured libc6 2.9-4ubuntu6.1
2010-05-18 20:31:51 status installed libc6 2.9-4ubuntu6.1
```


2) What other logs should I look at? 

3) What does this mean? Quoted from auth.log

```
May 19 18:57:36 MACHINENAME dbus-daemon: Rejected send message, 5 matched rules; type="error", sender=":1.10" (uid=0 pid=3672 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.8" (uid=0 pid=3654 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
```

---

### Post by heitjer on 2010-05-20
This solved the issue!

Must have been associated with the NVIDIA driver!

[L I N K]("http://ubuntuforums.org/showthread.php?t=1362931")

---

