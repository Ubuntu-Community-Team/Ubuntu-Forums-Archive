---
title: "Nautilus doesn't work from user (Unique-DBus-WARNING)"
date: 2011-08-23
forum: Desktop Environments
---

### Post by vyahhi on 2011-08-23
Can't run *nautilus* from user (from root is OK). Here's output from the console:

```
[15:04:12] vyahhi@vyahhi-laptop:~$ nautilus

(nautilus:5642): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[15:04:38] vyahhi@vyahhi-laptop:~$ 
```

I've removed *~/.ICEauthority*, *~/.nautilus*, *~/.gconf/app/nautilus*, but it didn't help. I've upgraded Ubuntu from 10.04 to 10.10 to 11.04, but this error remains the same.

*dbus* service works well:

```
[15:14:12] vyahhi@vyahhi-laptop:~$ sudo service dbus start
start: Job is already running: dbus
```

Configuration:
[LIST]
[*]GNOME nautilus 2.32.2.1
[*]Ubuntu 11.04 x86_64
[*]linux-2.6.38-11-generic
[/LIST]

---

