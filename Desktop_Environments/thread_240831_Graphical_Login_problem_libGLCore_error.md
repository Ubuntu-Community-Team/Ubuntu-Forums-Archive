---
title: "Graphical Login problem libGLCore error"
date: 2006-08-21
forum: Desktop Environments
---

### Post by tkirke on 2006-08-21
I'm suddenly having login problems
Using recovery I can login as root and startx
I notice though I get
dlopen: (cut) libGLcore.so: undefined symbol: __glXLastContext
Failed to load (cut)/libGLcore.so
I can also startx if I su to normal user.

---

### Post by jfdill_2 on 2006-08-21
Grrr same thing happening to me since updating xserver-xorg-core to 1:1.0.2-0ubuntu10.3.  I'm going to see if I can find an older .deb somewhere and downgrade.

Edit: GLcore was a red herring, I disabled the module in xorg.conf and X still wouldn't start.  People have started a buhzillion different threads now about this subject, the fix seems to be:

```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

I'm going to take it one farther and say you might want to do this until we know a fix is available--wajig is just here because it's a very easy way to get the correct "pin" for the package.

```
sudo apt-get install wajig
sudo wajig hold xserver-xorg-core
# when a working package comes out
sudo wajig unhold xserver-xorg-core
```

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux musashi 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 21 21:49:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

```

---

