---
title: "Inotify"
date: 2005-12-06
forum: General Help
---

### Post by organgtool on 2005-12-06
I have found conflicting information about whether or not Breezy comes with inotify support by default in the kernel.  I heard from some people that it does NOT come with support and that I need to compile my own kernel to get support.  I have heard from other sources that inotify IS in the Breezy kernel, but that there are bugs in the version that it comes with.

According to many sites, if inotify is supported by the kernel, /dev/inotify should exist and that device is not present on my system.  However, support could be there and the device just does not exist since most users would never need it.

Please shed any light on this situation so that I can start developing a small intrusion detection system using inotify!

---

### Post by flopsy on 2005-12-06
Appears to be compiled in:
```

gee@daisy:~$ grep INOTIFY /usr/src/linux-headers-2.6.12-10-686-smp/.config
CONFIG_INOTIFY=y

```

You shouldn't have a /dev/inotify:
[http://lists.debian.org/debian-user/2005/10/msg02280.html](http://lists.debian.org/debian-user/2005/10/msg02280.html)

But I don't have a /proc/sys/fs/inotify:
[http://lists.debian.org/debian-user/2005/10/msg00142.html](http://lists.debian.org/debian-user/2005/10/msg00142.html)

---

