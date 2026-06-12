---
title: "Rkward cluster package issue"
date: 2013-05-31
forum: Education &amp; Science
---

### Post by ADani on 2013-05-31
I'm on Ubuntu 12.04.2, KDE 4.8.5 and Rkward Version 0.5.7
I have installed a package called "cluster" but I cannot use it in the software, the option doesn't appear in the Analysis tab in the program.

[COLOR=#333333][FONT=monospace]I'm new to the software and Installed it becase I need to do clustering analysis. I installed a package called "cluster" as root and It appears to be installed, actually I have somehow two of them (v 1.14.1 and 1.14.4):
[/FONT][/COLOR]
[[IMG]http://s7.postimg.org/nhtl8wgnv/rkward1.jpg[/IMG]]("http://postimage.org/")

Those locations exist and have "cluster" folders on them.
I've tryied loading the cluster package but I cannot get the cluster analysis options to appear anywhere in the analysis options for my data. Also, when I restar RKWard, "cluster" is not in "loaded packages"


[[IMG]http://s14.postimg.org/6b2ou0en5/rkward2.jpg[/IMG]]("http://postimage.org/")


sudo rkward in command terminal starts the program but shows:
```

Error: "/var/tmp/kdecache-dani" is owned by uid 1000 instead of uid 0.Error: "/tmp/kde-dani" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-dani" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-dani" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dani" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-dani" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-dani" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-dani" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dani" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dani" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-dani" is owned by uid 1000 instead of uid 0.

```


Please help me!
Thanks

---

### Post by rewyllys on 2013-05-31
Although I need to acknowledge that I haven't had occasion to use the "cluster" package, I can definitely say that I found the Rkward package generally unsatisfactory to use.

I strongly recommend that you try installing RStudio and using the cluster package in it.  I've been very pleased with the ease of use of RStudio for many types of analysis with R.

---

