---
title: "Problems with Kxdocker"
date: 2007-03-28
forum: Desktop Environments
---

### Post by BraggPxnk on 2007-03-28
I just installed Kxdocker using the package manager and when I tried to run it, this is what I got:

```
justin@justin-laptop:~$ kxdocker
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-24732' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.
justin@justin-laptop:~$ 

```

Any suggestions?

---

### Post by Martin Du Plooy on 2007-03-29
I also struggled installing kxdocker on my kubuntu through Adept Manager Manage Packager. It did not work after installation. Here is a manual install that does work....

This is how I installed it on Kubuntu 6.10. Key Words - Mac OSX docker kxdocker 

Hope someone can use this :

sudo apt-get install xlibs-dev libqt3-mt-dev  kdelibs4-dev kdebase-dev

Download kxdocker-version.x.x.tar.bz2

from

[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)

tar jxfv kxdocker-version.x.x.tar.bz2

cd kxdocker-version

./configure --prefix=/usr

make

sudo make install

Also download these packages : 

The very useful files are:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2

The optional files are:

kxdocker-arpmanager-version.x.x.tar.bz2
kxdocker-bluetooth-version.x.x.tar.bz2
kxdocker-gaclock-version.x.x.tar.bz2
kxdocker-gamarok-version.x.x.tar.bz2
kxdocker-gapager-version.x.x.tar.bz2
kxdocker-gbattery-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2
kxdocker-gipcontrack-version.x.x.tar.bz2
kxdocker-gmail-version.x.x.tar.bz2
kxdocker-gmount-version.x.x.tar.bz2
kxdocker-gnetio-version.x.x.tar.bz2
kxdocker-gpipe-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-gthrottle-version.x.x.tar.bz2
kxdocker-mountmanager-version.x.x.tar.bz2
kxdocker-networker-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz2

These optional files depend on your needed, for me I just download:

kxdocker-gaclock-version.x.x.tar.bz2
kxdocker-gapager-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2
kxdocker-gmail-version.x.x.tar.bz2
kxdocker-gmount-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-mountmanager-version.x.x.tar.bz2
kxdocker-networker-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz2

Note : Do not install package kxdocker-gthrottle-1.0.0. It crashes.

Compile and Install

tar jxfv kxdocker-package-version.x.x.tar.bz2

cd kxdocker-package-version.x.x/ && ./configure --prefix=/usr --with-extra-libs=/usr/lib/ --with-extra-includes=/usr/include && make && sudo make install && cd .. && ls

Do this for all your packages you want to install

Uninstall KXDocker

Go to each directory you installed it and type:
make clean && sudo make uninstall
Start with KXDocker

After install KXDocker just type

kxdocker

---

### Post by Martin Du Plooy on 2007-03-29
I also struggled installing kxdocker on my kubuntu through Adept Manager Manage Packager. It did not work after installation. Here is a manual install that does work....

This is how I installed it on Kubuntu 6.10. Key Words - Mac OSX docker kxdocker 

Hope someone can use this :

sudo apt-get install xlibs-dev libqt3-mt-dev  kdelibs4-dev kdebase-dev

Download kxdocker-version.x.x.tar.bz2

from

[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)

tar jxfv kxdocker-version.x.x.tar.bz2

cd kxdocker-version

./configure --prefix=/usr

make

sudo make install

Also download these packages : 

The very useful files are:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2

The optional files are:

kxdocker-arpmanager-version.x.x.tar.bz2
kxdocker-bluetooth-version.x.x.tar.bz2
kxdocker-gaclock-version.x.x.tar.bz2
kxdocker-gamarok-version.x.x.tar.bz2
kxdocker-gapager-version.x.x.tar.bz2
kxdocker-gbattery-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2
kxdocker-gipcontrack-version.x.x.tar.bz2
kxdocker-gmail-version.x.x.tar.bz2
kxdocker-gmount-version.x.x.tar.bz2
kxdocker-gnetio-version.x.x.tar.bz2
kxdocker-gpipe-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-gthrottle-version.x.x.tar.bz2
kxdocker-mountmanager-version.x.x.tar.bz2
kxdocker-networker-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz2

These optional files depend on your needed, for me I just download:

kxdocker-gaclock-version.x.x.tar.bz2
kxdocker-gapager-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2
kxdocker-gmail-version.x.x.tar.bz2
kxdocker-gmount-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-mountmanager-version.x.x.tar.bz2
kxdocker-networker-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz2

Note : Do not install package kxdocker-gthrottle-1.0.0. It crashes.

Compile and Install

tar jxfv kxdocker-package-version.x.x.tar.bz2

cd kxdocker-package-version.x.x/ && ./configure --prefix=/usr --with-extra-libs=/usr/lib/ --with-extra-includes=/usr/include && make && sudo make install && cd .. && ls

Do this for all your packages you want to install

Uninstall Kxdocker

Go to each directory you installed it and type:
make clean && sudo make uninstall
Start with Kxdocker

After install Kxdocker just type

kxdocker &

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

