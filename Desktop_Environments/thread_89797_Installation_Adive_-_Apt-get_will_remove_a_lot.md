---
title: "Installation Adive - Apt-get will remove a lot"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Ingla on 2005-11-13
Hello.

I want to make Flash movies, so I downloaded f4l (a .deb from Sourceforge).

When trying to install the deb, apt-get said the dependencies were unavailable, so I added the following Debian repositories:

deb [ftp://ftp.us.debian.org/debian](ftp://ftp.us.debian.org/debian) stable main contrib non-free
deb [ftp://non-us.debian.org/debian-non-US](ftp://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free


Then apt-get said it couldn't do it because of conflicts and I should try apt-get -f install.

That brought me this:
--------------------------------------------------------------------------
[COLOR="Red"]sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libqt3c102-mt
Suggested packages:
  libqt3c102-mt-psql libqt3c102-mt-mysql libqt3c102-mt-odbc
The following packages will be REMOVED:
  f4l k3blibs kdebase-bin kdelibs-bin kdelibs4-dev kdelibs4c2 libarts1-dev
  libarts1c2 libdbus-qt-1-1c2 libqt3-mt libqt3-mt-dev licq licq-plugin-qt
  qt3-dev-tools
The following NEW packages will be installed:
  libqt3c102-mt
0 upgraded, 1 newly installed, 14 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 3045kB of archives.
After unpacking 61.4MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.[/COLOR]
--------------------------------------------------------------------------
As you can see I aborted the operation pending advice because it looks like apt-get wants to remove half the system in order to install this one program.[B][I]
Aren't these things needed for other apps? Would I dare let apt-get do this?[/I][/B]

Also, it says it will remove f4l, but that's what I wanted to install (and haven't yet...unless something partial was done).

When I tried to install originally, I got this:

--------------------------------------------------------------------------
[COLOR="Red"]sudo dpkg -i Desktop/f4l_0-1.2-1_i386.deb
Selecting previously deselected package f4l.
(Reading database ... 97661 files and directories currently installed.)
Unpacking f4l (from Desktop/f4l_0-1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libxrender1 (>= 1:0.9.0-2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
[B][I]dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l[/I][/B][/COLOR]
--------------------------------------------------------------------------
Does that mean f4l was installed but not configured?

Any advice as to what I should do (safely) please?

---

### Post by Ingla on 2005-11-13
Title should have been "Installation Advice", etc.;)

---

