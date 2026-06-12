---
title: "startx error"
date: 2009-06-09
forum: Desktop Environments
---

### Post by NewLearner001 on 2009-06-09
Hello,
Here is my server configurations....
 
**uname -r --> 2.6.24-23-generic**
**lsb_release -r --> Release: 8.04**
 
I am connecting to this server using putty.exe and since it is test box, loged in as "root".
 
When I type startx at the putty.exe terminal I am getting the following error.
 
 
hostname: Unknown host
X: warning; process set to priority -1 instead of requested priority 0
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux
mytestbox-test 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686
Build Date: 13 June 2008 01:08:21AM
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 9 10:51:41 2009
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(WW) VESA(0): Failed to set up write-combining range (0xfc000000,0x800000)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
[config/hal] couldn't initialise context: (null) ((null))
waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
 
xinit: unexpected signal 2.
 
What I should do to get my graphical display working.
My ultimate goal is to install Oracle on tihs box.
Thank you for your advice.
Smith

---

