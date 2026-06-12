---
title: "Watchdog error reporting no internet connection"
date: 2009-01-01
forum: General Help
---

### Post by nrune on 2009-01-01
I have a mythtv box 64 bit amd that I wanted to load Boxee on. So I follwed this [thread]("http://forum.boxee.tv/showthread.php?t=2065&page=3") and using getlibs was able to install and run boxee.  The problem is that watchdog is reporting to boxee that it can not reach the server. 
From the boxee logs:
```
18:08:14 T:4077398928 M: 31465472    INFO: WatchDog Process - starting
18:08:14 T:4126000960 M: 31465472    INFO: Successfuly initialized boxee library
18:08:14 T:4077398928 M: 31272960 WARNING: WatchDog Process - no connection to server
```

the logs are filled with "WARNING: WatchDog Process - no connection to server" 

I modified watchdog.conf and the syslog shows this:
```
Dec 31 23:31:06 mythtv watchdog[21437]: starting daemon (5.4):
Dec 31 23:31:06 mythtv watchdog[21437]: int=10s realtime=yes sync=no soft=no mla=0 mem=140664473911296
Dec 31 23:31:06 mythtv watchdog[21437]: ping: 192.168.1.1
Dec 31 23:31:06 mythtv watchdog[21437]: file: /var/log/messages:0
Dec 31 23:31:06 mythtv watchdog[21437]: pidfile: no server process to check
Dec 31 23:31:06 mythtv watchdog[21437]: interface: eth0
Dec 31 23:31:06 mythtv watchdog[21437]: test=none(0) repair=none alive=/dev/watchdog heartbeat=none temp=none to=root no_act$
Dec 31 23:31:06 mythtv watchdog[21437]: cannot open /dev/watchdog (errno = 2 = 'No such file or directory')
```

but there are no listings for watchdog in /var/log/messages and boxee has he same error

I know that the machine has a internet connecton, I just do not know why watchdog is not reporting a connection to boxee.

Anyone with any ideas? help!

Thanks

---

### Post by nrune on 2009-01-01
on reinstall I get this...

```
Unpacking watchdog (from .../watchdog_5.4-7_amd64.deb) ...
Processing triggers for man-db ...
Setting up watchdog (5.4-7) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `logibm-': Read-only file system
mknod: `logibm-': Read-only file system
makedev logibm c 10 0 root root 0660: failed
rm: cannot remove `logibm-': Read-only file system
rm: cannot remove `psaux-': Read-only file system
mknod: `psaux-': Read-only file system
makedev psaux c 10 1 root root 0660: failed
rm: cannot remove `psaux-': Read-only file system
rm: cannot remove `inportbm-': Read-only file system
mknod: `inportbm-': Read-only file system
makedev inportbm c 10 2 root root 0660: failed
rm: cannot remove `inportbm-': Read-only file system
rm: cannot remove `atibm-': Read-only file system
mknod: `atibm-': Read-only file system
makedev atibm c 10 3 root root 0660: failed
rm: cannot remove `atibm-': Read-only file system
rm: cannot remove `jbm-': Read-only file system
mknod: `jbm-': Read-only file system

```

My guess it that this is where the problem is.

---

