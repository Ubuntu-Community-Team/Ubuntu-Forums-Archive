---
title: "PiKdev install problems"
date: 2006-05-27
forum: Desktop Environments
---

### Post by f3tus on 2006-05-27
[http://pikdev.free.fr/](http://pikdev.free.fr/)
```
f3tus@w00t:~/Desktop/Incoming$ sudo dpkg -i pikdev_0.9.1-1_i386.deb
(Reading database ... 117543 files and directories currently installed.)
Preparing to replace pikdev 0.9.1-1 (using pikdev_0.9.1-1_i386.deb) ...
Unpacking replacement pikdev ...
dpkg: dependency problems prevent configuration of pikdev:
 pikdev depends on kdelibs4c2a (>= 4:3.5.2-1); however:
  Package kdelibs4c2a is not installed.
 pikdev depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 pikdev depends on libidn11 (>= 0.5.18); however:
  Version of libidn11 on system is 0.5.13-1.0.
 pikdev depends on libqt3-mt (>= 3:3.3.6); however:
  Version of libqt3-mt on system is 3:3.3.4-8ubuntu5.
 pikdev depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 pikdev depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
 pikdev depends on gputils; however:
  Package gputils is not installed.
 pikdev depends on kdelibs4c2a (>= 4:3.0.0); however:
  Package kdelibs4c2a is not installed.
dpkg: error processing pikdev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pikdev
f3tus@w00t:~/Desktop/Incoming$
```

What am I supposed to do now :/?
I'm running Kubuntu 5.10 with the latest KDE and other stuff from the repositories.

---

### Post by linuxvacuum on 2008-04-25
```
sudo apt-get -f install
```

---

