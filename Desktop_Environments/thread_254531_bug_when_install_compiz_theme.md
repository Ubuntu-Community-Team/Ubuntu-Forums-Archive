---
title: "bug when install compiz theme"
date: 2006-09-10
forum: Desktop Environments
---

### Post by blacksea on 2006-09-10
have any body help me to fix this bugs

l csm
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  compiz-core compiz-plugins libglitz-glx1 libglitz1
Recommended packages:
  compiz-kde
The following NEW packages will be installed:
  cgwd cgwd-themes compiz compiz-core compiz-gnome compiz-plugins csm
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 6569kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y]
WARNING: The following packages cannot be authenticated!
  compiz-core csm compiz-plugins cgwd cgwd-themes compiz compiz-gnome
  libglitz1 libglitz-glx1 xserver-xgl
Install these packages without verification [y/N]? y
Get:1 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main compiz-core 0.0.13.48-0ubuntu1 [211kB ]
Get:2 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main csm 0.8-0ubuntu1 [27.2kB]
Get:3 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main compiz-plugins 0.20-0ubuntu1 [1393kB]
Get:4 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main cgwd 0.68-0ubuntu1 [200kB]
Get:5 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main cgwd-themes 0.16-0ubuntu1 [2979kB]
Get:6 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main compiz 0.0.13.48-0ubuntu1 [26.9kB]
Get:7 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main compiz-gnome 0.0.13.48-0ubuntu1 [58.7 kB]
Get:8 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main libglitz1 0.5.6-0ubuntu1 [77.3kB]
Get:9 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main libglitz-glx1 0.5.6-0ubuntu1 [30.0kB]
Get:10 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main xserver-xgl 7.0.0+cvs20060625 [1565k B]
Fetched 6358kB in 2m58s (35.7kB/s)
Failed to fetch [http://ubuntu.compiz.net/pool/main/c/compiz/compiz-core_0.0.13.4](http://ubuntu.compiz.net/pool/main/c/compiz/compiz-core_0.0.13.4) 8-0ubuntu1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?
hai@HHLV:~$ sudo apt-get update -fix-missing E: Command line option 'i' [from -fix-missing] is not known.
hai@HLV:~$ sudo apt-get update --fix-missing
Get:1 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release

Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:4 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release.gpg
Get:5 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release

Get:6 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release [5405B]
Get:7 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Get:8 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release [34.8kB]
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Ign [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Fetched 71.6kB in 24s (2974B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown error executing gpgv
W: GPG error: [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release: Unknown error executing gpgv
W: GPG error: [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
hai@HLV:~$ sudo apt-get update --fix-missing
Get:1 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Get:2 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release.gpg
Get:3 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release
Get:4 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release [34.8kB]
Ign [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release

Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Get:7 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release

Get:8 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release [5405B]
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Fetched 71.6kB in 23s (3107B/s)
Reading package lists... Done
W: GPG error: [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown error executing gpgv
W: GPG error: [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
hai@HLV:~$ sudo apt-get update --fix-missing
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper/universe Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) dapper-updates/universe Packages
Get:4 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg [189B]
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Hit [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/aiglx Packages
Fetched 568B in 12s (44B/s)
Reading package lists... Done
hai@HLV:~$ sudo apt-get install compiz compiz-gnome cgwd cgwd-themes xserver-xgl csm
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  compiz-core compiz-plugins libglitz-glx1 libglitz1
Recommended packages:
  compiz-kde
The following NEW packages will be installed:
  cgwd cgwd-themes compiz compiz-core compiz-gnome compiz-plugins csm libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 211kB/6569kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main compiz-core 0.0.13.48-0ubuntu1 [211kB]
Fetched 211kB in 15s (13.4kB/s)
[B]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/B]
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 10 during global destruction.
Selecting previously deselected package compiz-core.
(Reading database ... 110316 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.48-0ubuntu1_i386.deb) ...
Selecting previously deselected package csm.
Unpacking csm (from .../csm_0.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_0.20-0ubuntu1_i386.deb) ...
Selecting previously deselected package cgwd.
Unpacking cgwd (from .../cgwd_0.68-0ubuntu1_i386.deb) ...
Selecting previously deselected package cgwd-themes.
Unpacking cgwd-themes (from .../cgwd-themes_0.16-0ubuntu1_all.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_0.0.13.48-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_0.0.13.48-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglitz1.
Unpacking libglitz1 (from .../libglitz1_0.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0+cvs20060625_i386.deb) ...
Setting up compiz-core (0.0.13.48-0ubuntu1) ...
Setting up compiz-gnome (0.0.13.48-0ubuntu1) ...
Setting up libglitz1 (0.5.6-0ubuntu1) ...

Setting up libglitz-glx1 (0.5.6-0ubuntu1) ...

Setting up xserver-xgl (7.0.0+cvs20060625) ...

Setting up compiz-plugins (0.20-0ubuntu1) ...
Setting up csm (0.8-0ubuntu1) ...
Setting up cgwd (0.68-0ubuntu1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 477 strings at 20 - 27a0
Wrote aliases at 27a0 - 294c
Wrote parents at 294c - 32fc
Wrote literal globs at 32fc - 3358
Wrote suffix globs at 3358 - 6710
Wrote full globs at 6710 - 6734
Wrote magic at 6734 - bd80
Wrote namespace list at bd80 - bd90
***

Setting up cgwd-themes (0.16-0ubuntu1) ...
Setting up compiz (0.0.13.48-0ubuntu1) ...

---

