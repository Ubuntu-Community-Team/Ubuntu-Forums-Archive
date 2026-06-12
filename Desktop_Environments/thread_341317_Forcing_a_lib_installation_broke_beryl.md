---
title: "Forcing a lib installation broke beryl"
date: 2007-01-18
forum: Desktop Environments
---

### Post by rama on 2007-01-18
I tried to compile an application that required qt libraries. Due to a version conflict on a dependent package I forced it to another version and it seems that this action broke beryl : Since this happened when I run beryl-manager kde shuts down and I am thrown back to gdm (I installed kde on an ubuntu installation). How can I update the package to the current version? I tried apt-get update, apt-get upgrade and apt-get dist-upgrade but the package never showed up.

PS: I'll edit the post later with the name of the application that I tried to compile and the package I forced as well as my sources.list so that you 'll know what repos I'm using. Sorry about that but I'm currently at work.

EDIT : The app I tried to install was KAnyRemote

and from the synaptic history here is the part I downgraded the package:
Commit Log for Sat Jan 13 00:05:48 2007


Downgraded the following packages:
libglu1-mesa

Installed the following packages:
libaudio-dev (1.8-2)
libcupsys2-dev (1.2.4-2ubuntu3)
libexpat1-dev (1.95.8-3.2)
libfontconfig1-dev (2.3.2-7ubuntu2)
libfreetype6-dev (2.2.1-5)
libgcrypt11-dev (1.2.2-2)
libglu1-mesa-dev (6.5.1~20060817-0ubuntu3)
libgnutls-dev (1.4.0-3ubuntu1)
libgpg-error-dev (1.2-1)
liblcms1-dev (1.15-1)
liblzo-dev (1.08-3)
libmng-dev (1.0.9-1)
libopencdk8-dev (0.5.8-1)
libpng12-dev (1.2.8rel-5.1ubuntu0.1)
libpopt-dev (1.10-2)
libqt3-mt-dev (3:3.3.6-3ubuntu3)
libtasn1-3-dev (0.3.5-1)
libxcursor-dev (1.1.7-0ubuntu1)
libxft-dev (2.1.10-1ubuntu1)
libxi-dev (2:1.0.1-0ubuntu1)
libxinerama-dev (2:1.0.1-4build1)
libxmu-dev (2:1.0.2-1ubuntu1)
libxmu-headers (2:1.0.2-1ubuntu1)
libxrandr-dev (2:1.1.1-0ubuntu1)
libxrender-dev (1:0.9.1-0ubuntu1)
qt3-dev-tools (3:3.3.6-3ubuntu3)
x11proto-randr-dev (1.1.2-3ubuntu1)
x11proto-render-dev (2:0.9.2-3ubuntu1)
x11proto-xinerama-dev (1.1.2-3ubuntu1)


The package I neaded was libqt3-mt-dev. I know I can fix this with a single command but right now since I don't know what this command is my only option is to reinstall ubuntu...
Somebody?

---

### Post by rama on 2007-01-20
bump?](*,)

---

