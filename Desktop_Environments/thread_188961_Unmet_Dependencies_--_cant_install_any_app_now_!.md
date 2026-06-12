---
title: "Unmet Dependencies -- cant install any app now ! ?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by chetanthaker on 2006-06-04
Hey guys...

I just upgraded from Breezy to Dapper and I just cant seem to install any application with apt-get install xxxxx

I get this error


> ceetee@ceeteebox:~/Desktop/superkaramba-0.39/superkaramba-0.39$ sudo apt-get install karamba
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kubuntu-default-settings: Depends: kwin-style-crystal but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ceetee@ceeteebox:~/Desktop/superkaramba-0.39/superkaramba-0.39$           


Can someone help ??

If I try ./configure, i get this error


> (some checks before this)
.....
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!




Can someone help me with these 2 errors ??


CeeTee

---

### Post by daller on 2006-06-04
Have you tried to run one of the following: (as suggested)

sudo apt-get -f install

sudo apt-get upgrade --fix-missing

---

### Post by chetanthaker on 2006-06-05
Still cant get it to install the missing files 

What do I do ??

I get the following errors


> ceetee@ceeteebox:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kwin-style-crystal
The following NEW packages will be installed:
  kwin-style-crystal
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
10 not fully installed or removed.
Need to get 0B/122kB of archives.
After unpacking 516kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter

(Reading database ... 100497 files and directories currently installed.)
Unpacking kwin-style-crystal (from .../kwin-style-crystal_0.9.9-0ubuntu4_i386.deb) ...
dpkg: error processing /cdrom//pool/main/k/kwin-style-crystal/kwin-style-crystal_0.9.9-0ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/kwin_crystal_config.so', which is also in package crystal
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /cdrom//pool/main/k/kwin-style-crystal/kwin-style-crystal_0.9.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

ceetee@ceeteebox:~$ sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kubuntu-default-settings: Depends: kwin-style-crystal but it is not installed
E: Unmet dependencies. Try using -f.
ceetee@ceeteebox:~$     

---

### Post by Chickenmonger on 2006-06-05
I've heard either Aptitude or Synaptic does a better job of resolving broken-ness than plain apt-get. I've personally used Synaptic to resolve broken packages before.

---

### Post by effoff on 2006-06-05
This is caused by errors in the **debhelper** that the maintainer/developer used to make the deb.

the place to examine is /var/lib/dpkg/info...........

Under the package in question here are a few files we see are the scripts associated with the package:

pkgname.postinst
pkgname.prerm
pkgname.postrm

These scripts will run at the appropriate time (post-install, or pre-removal and post-removal respectively).

To fix this you have two choices:

1- Edit the script to make the failure non-terminal.
2- Examine the script and determine why it fails.

In general most of the scripts associated with Debian packages will begin with:
**#!/bin/sh -e**
or
[B]#!/bin/sh

set -e[/B]

Either of these two scripts will abort with an error if something fails. A simple fix is to remove the "-e", or the "set -e" line from the script before repeating your upgrade/install/removal attempt.

---

### Post by chetanthaker on 2006-06-07
These are the 3 files -- can you guys pls help ??


CeeTee

---

