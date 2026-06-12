---
title: "xorg crashing from glxinfo"
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by mega on 2007-04-05
I've been running beryl on nvidia beta drivers sense they came out

today I rebooted and now X crashes


I always start up in safe mode and run beryl-manager to go into pretty mode


but now even running glxinfo crashes X to a black screen


this is the end of the xorg.0.log.old file

Backtrace:
0: /usr/bin/X.schedreal(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting


ideas?

---

### Post by handaxe on 2007-04-05
Although about wine, the end of the referred thread might help, as it mentions your problem.

[http://ubuntuforums.org/showthread.php?p=2406692](http://ubuntuforums.org/showthread.php?p=2406692)

HA

---

### Post by mega on 2007-04-05
rerunning nvidia installer fixed it

it's like the 15th time I've had to reinstall it

---

