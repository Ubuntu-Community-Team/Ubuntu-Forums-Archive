---
title: "Just installed Steam but it won't run ..."
date: 2015-10-15
forum: Gaming &amp; Leisure
---

### Post by GameGuru on 2015-10-15
I am running Ubuntu 15.04 and installed Steam but it won't run when I launch it.  When I run it in Terminal I get the following:

Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast


Looks like it is having issues with my Radeon R7 265.  I am just using the drivers that game with Ubuntu, haven't installed anything else.  Do I need to?  If so, how do I do it?

---

### Post by MikeCyber on 2015-10-16
You need to install the proprietary AMD drivers.

---

### Post by howefield on 2015-10-16
Try searching the dash for Additional Drivers and install the proprietary option that is offered.

---

### Post by R33D3M33R on 2015-10-17
The proper solution is executing these commands: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

BTW: there are tons of exactly same threads every month. Why not make a sticky thread describing the solution?

---

### Post by vpiercy on 2015-12-02
UPDATE: I moved the libraries as described in this Askubuntu thread: [http://askubuntu.com/questions/689598/steam-wont-open-in-ubuntu-15-10/690300#690300](http://askubuntu.com/questions/689598/steam-wont-open-in-ubuntu-15-10/690300#690300)

That got Steam to run.
----


Will that gcc libraries thread linked in the previous post work for Ubuntu 15.10?

When I try to start Steam I get the following lines before it stalls:

> $Steam
Running Steam on ubuntu 15.10 64-bit
STEAM_RUNTIME is enabled automatically
[2015-12-02 20:53:49] Startup - updater built Nov  9 2015 18:23:22
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

:-/

Just installed Ubuntu 15.10 today onto a Z170 Skylake PC. Any ideas on what's holding up Steam from running on Ubuntu?

Thanks!

---

