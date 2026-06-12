---
title: "notify-send (libnotify-bin) doesn't care about --expiry-time"
date: 2009-11-08
forum: Desktop Environments
---

### Post by lol24h on 2009-11-08
I don't know if it's only for me, but since Ubuntu 9.04, and even now in 9.10 the option 
```
-t, --expire-time=TIME            Specifies the timeout in milliseconds at wh...

```
doesn't work at all, the notification expires always after about 10s. I've seen some bug report from the past, but they seemed to be fixed. Why it still doesn't work for me ?

$ aptitude show libnotify-bin
Packet: libnotify-bin
State: installed
Installed automatically: no
Version:  0.4.5-1ubuntu1

---

### Post by BobvanderPoel on 2009-12-01
I found a long thread on this. Seems the developers think it's fine and not a bug. I don't understand the attitude, but I guess I'm free to write my own notify code if I'm really upset. But, really, either this should be fixed or the manual for notify-send should be updated.

---

### Post by sisco311 on 2009-12-01
The new notification daemon, [notify-osd]("https://wiki.ubuntu.com/NotifyOSD"), by design, does not support the --expire-time parameter.

---

### Post by BobvanderPoel on 2009-12-01
That's fine. The point that I'm making here (and several made in the thread that I've lost the pointer to) is that the manual page for notify-send clearly states that -t sets a timeout value. Perhaps that should be fixed? Or is this program not part of gnome/ubuntu?

---

### Post by sisco311 on 2009-12-01
> **BobvanderPoel said:**
> That's fine. The point that I'm making here (and several made in the thread that I've lost the pointer to) is that the manual page for notify-send clearly states that -t sets a timeout value. 


notify-send sends desktop notifications to **a** notification daemon (like notification-daemon, xfce4-notifyd, notify-osd... ), as defined in the Desktop Notifications spec.

> **BobvanderPoel said:**
> 
Perhaps that should be fixed? Or is this program not part of gnome/ubuntu?

Nope, not all of the notification daemons support all the features, but that's fine.

---

### Post by AndThenWhat on 2009-12-22
I am trying to use notify-send to send an icon and none of the icons I specify work.  Only stock icons error, info, and desktop have worked using my -i parameter.  So on Ubuntu 9.10 what daemon is used by default?  I want to find a list of stock icons that work by default.

---

