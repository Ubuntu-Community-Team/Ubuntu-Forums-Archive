---
title: "X11 login doesn't assign groups, logout brings me back to desktop"
date: 2018-07-25
forum: Desktop Environments
---

### Post by ryancerium on 2018-07-25
The system boots up normally, and I log in. I open an xterm and this happens:
```
$ groups
rphelps

$ su rphelps
Password:

$ groups
rphelps adm cdrom sudo dip www-data plugdev lpadmin sambashare kismet docker
```
If I log in via SSH, my groups are set correctly. If I log into a tty instead of X, my groups are set correctly.
When I try to log out of the X session or hit Ctrl+Alt+L, it closes the session, but then it seems like the greeter can't be (re)started, or the lockscreen doesn't work, and it brings me back to my desktop.
I was recently mucking around with screen savers (xscreensaver, gnome-screensaver, etc.) trying to get the screen to lock after 30 minutes (no luck). Did purging those have remove something vital for logging out?
I haven't modified any /etc/ files manually.
Xubuntu 18.04

---

### Post by TheFu on 2018-07-27
What is returned by these commands:
```
getent passwd rphelps
getent group rphelps
id
```

Please use code tags.

---

### Post by jamesjones01 on 2018-07-31
I'm having the "logout brings me back to desktop" issue on my wife's desktop, which I got out of its box after a long time and upgraded first from 15.10 to 16.04, and then from 16.04 to 18.04. After reading this thread, I checked and found that I was having the groups issue, too.

In case it's of help, here's what I see for those commands, *mutatis mutandis, *plus one other:
```

[FONT=monospace][COLOR=#000000]jejones@pooh:~$ getent passwd jejones[/COLOR]
jejones:x:1000:1000:James Jones,,,:/home/jejones:/bin/bash
jejones@pooh:~$ getent group jejones
jejones:x:1000:
jejones@pooh:~$ id
uid=1000(jejones) gid=1000(jejones) groups=1000(jejones)
jejones@pooh:~$ grep jejones /etc/group
adm:x:4:syslog,[COLOR=#FF5454]**jejones**[/COLOR]
cdrom:x:24:[COLOR=#FF5454]**jejones**[/COLOR]
sudo:x:27:[COLOR=#FF5454]**jejones**[/COLOR]
dip:x:30:[COLOR=#FF5454]**jejones**[/COLOR]
plugdev:x:46:[COLOR=#FF5454]**jejones**[/COLOR]
lpadmin:x:113:[COLOR=#FF5454]**jejones**[/COLOR]
[COLOR=#FF5454]**jejones**[/COLOR][COLOR=#000000]:x:1000:[/COLOR]
sambashare:x:128:[COLOR=#FF5454]**jejones**[/COLOR]
jejones@pooh:~$ 
[/FONT]
```
I should add that all those groups predate the current session--I've read that if you add yourself to a group in the current login session, "groups" won't show you as member until your next login session.

---

### Post by steeldriver on 2018-07-31
I've been following this issue on a number of forums - it seems to be related to libpam-kwallet and/or libpam-kwallet5

[https://bugs.launchpad.net/lightdm/+bug/1781418](https://bugs.launchpad.net/lightdm/+bug/1781418)

---

### Post by jamesjones01 on 2018-07-31
Thanks, steeldriver. I commented out the two lines suggested. Groups now show up, and I can logout.

---

### Post by TheFu on 2018-07-31
> **jamesjones01 said:**
>   I've read that if you add yourself to a group in the current login session, "groups" won't show you as member until your next login session.

Session environments are picked up at login time, so that makes sense, but you can trick it from any terminal by running **newgrp**.  It will only take effect from that terminal and subprocesses run from that terminal, which is often enough for many needs.

There can be other reasons for getting kicked out immediately from login when some GUI programs cannot write their data to config files because "someone" ran a GUI program as root with sudo improperly.   Typically, it is something like *sudo nautilus* - **which should NEVER be used.**  Many other Gnome / KDE programs can cause the same issue.  I've seen this for years.

---

### Post by ryancerium on 2018-08-01
I gave up and reinstalled.  I'm very grateful for everyone's help nevertheless, and I'm glad at last one person was helped by this.

---

