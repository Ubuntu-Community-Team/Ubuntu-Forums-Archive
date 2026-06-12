---
title: "GNOME not starting without net connection"
date: 2007-06-19
forum: Desktop Environments
---

### Post by HappyDude on 2007-06-19
I have a problem where GNOME is freezing on login when I don't have a working network connection.  For example, if I'm logging in from a location that my wireless connection is not setup for, GNOME will never finish loading.  However, if I go to the console and setup or fix my connection, it will suddenly finish loading.

Presumably everything is blocking on something that is trying to access the internet, but I have no idea what it is or how to fix it.  I know little-to-nothing about the GNOME startup process and how I figure out what stage it is on, so if someone could lead me through this process or link me somewhere I can find out about tracing it, it would be greatly appreciated.

Btw, I'm running Ubuntu 7.04 with all the latest updates installed.

Thanks!

---

### Post by mitch.c on 2007-06-20
I remember fighting something like this once, but can't remember the details. Make sure /etc/hosts has the following entries (where ubuntu matches the name of your host):
```
127.0.0.1 localhost ubuntu
127.0.1.1 ubuntu
```

Make sure the loopback interface is coming up as well:
```
$ ifconfig
```

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

