---
title: "Upgrading libs for kirocker?"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by Beanalby on 2007-09-15
I've recently switched to Kubuntu, and I'm trying to get Kirocker to show Amarok's status on my side panel. ([http://www.kde-apps.org/content/show.php?content=52869](http://www.kde-apps.org/content/show.php?content=52869))

```
ninji@megaman:~/Desktop$ sudo dpkg -i kirocker_3.4.1-1_i386.deb
Password:
Selecting previously deselected package kirocker.
(Reading database ... 171282 files and directories currently installed.)
Unpacking kirocker (from kirocker_3.4.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of kirocker:
 kirocker depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Version of kdelibs4c2a on system is 4:3.5.6-0ubuntu14.1.
 kirocker depends on libart-2.0-2 (>= 2.3.18); however:
  Version of libart-2.0-2 on system is 2.3.17-1.
 kirocker depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 kirocker depends on libfreetype6 (>= 2.3.5); however:
  Version of libfreetype6 on system is 2.2.1-5ubuntu1.1.
 kirocker depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 kirocker depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
 kirocker depends on zlib1g (>= 1:1.2.3.3.dfsg-1); however:
  Version of zlib1g on system is 1:1.2.3-13ubuntu4.
dpkg: error processing kirocker (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kirocker
ninji@megaman:~/Desktop$
```

All of these libs are upgraded to their latest with aptitude, and I'm not familiar with trying to upgrade things beyond what's in the repository.

Is this something I could do (moderately) easily?  Or should I just wait for the repository to catch up?

Alternatively, anyone know where I could get an older Kirocker version, or another program that accomplishes the same thing?

---

