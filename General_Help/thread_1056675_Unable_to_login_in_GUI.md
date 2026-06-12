---
title: "Unable to login in GUI"
date: 2009-02-01
forum: General Help
---

### Post by anjanesh on 2009-02-01
Hi

Im having Kubuntu 8.10 64-bit on a PC.
Now all of a sudden I cant seem to login.
After entering the username & password, it shows the loading KDE 4.1 splash page - after it shows the first icon, it sort of restarts X and goes back to the login screen back again !

I did try updating to KDE 4.2 yesterday but that doesnt seem to have happened fully I guess.

I can login using console but what am I supposed to edit to get back login using GUI ?
Tried startx - a blank screen shows up with te mouse cursor and then back to console.
```

anjanesh@be3:~$ startx


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux be3 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008 09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (build@crested.buildd)
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the full version.
Module Loader Present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 1 11:32:02 2009
(==) Using config file: "/etc/X11/xorg.config"

waiting for X server to shut down

anjanesh@be3:^$

```

.xsession-errors
```
Xsession: X session started for root at Sun Feb  1 12:06:36 IST 2009
Setting IM through im-switch for locale=en_IN.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
Error: "/tmp/ksocket-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-anjanesh" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-anjanesh" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/bin/kcminit_startup
Error: "/var/tmp/kdecache-anjanesh" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/ksmserver
<unknown program name>(5848)/ KStartupInfo::createNewStartupId: creating:  "be3;1233470197;631085;5848_TIME0" : "unnamed app"
ksmserver: error while loading shared libraries: libplasma.so.3: cannot open shared object file: No such file or directory
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.

```
This may have something to do with libplasma.so.3 ?
Thanks

---

### Post by cmnorton on 2009-02-02
If you can log into the console, at least you have access to your logs (/var/log) and that's a good place to start to look for information as to why this happened.

---

### Post by anjanesh on 2009-02-09
I got it working by running OS in rescue mode and "dpkg Repair broken packages"

---

