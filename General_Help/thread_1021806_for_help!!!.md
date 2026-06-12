---
title: "for help!!!"
date: 2008-12-25
forum: General Help
---

### Post by ilinux_bj on 2008-12-25
my system is ubuntu8.10 desktop-i386,here is a problem:

[COLOR="Red"]ilinux@ilinux-desktop:~$ sudo apt-get install libgtop2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtop2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  sharutils diffstat quilt xaw3dg-dev liblockfile-dev xaw3dg
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libgtop2-dev (2.24.0-0ubuntu2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libgtop2-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libgtop2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

and also:
[COLOR="Red"]ilinux@ilinux-desktop:~$ sudo apt-get remove libgtop2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sharutils diffstat quilt xaw3dg-dev liblockfile-dev xaw3dg
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libgtop2-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1139kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 181540 files and directories currently installed.)
Removing libgtop2-dev ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libgtop2-dev (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 libgtop2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Please help me!Thank you very much!

---

### Post by gettinoriginal on 2008-12-26
Not sure what you are asking, you installed it, then removed it, but didn't fix errors in between, what is it you are trying to do ??

---

### Post by ilinux_bj on 2008-12-26
> **gettinoriginal said:**
> Not sure what you are asking, you installed it, then removed it, but didn't fix errors in between, what is it you are trying to do ??

I want to install conky,then you can see:

[COLOR="Red"]ilinux@ilinux-desktop:~$ sudo apt-get install conky
[sudo] password for ilinux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  sharutils diffstat quilt xaw3dg-dev liblockfile-dev xaw3dg
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libgtop2-dev (2.24.0-0ubuntu2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libgtop2-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libgtop2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]

---

### Post by gettinoriginal on 2008-12-26
libgtop2-dev  is in Synaptic, install it from there rather than trying to compose it from source.  But before you do, run:

sudo apt-get autoremove 
to get rid of the "not needed" in conky install.

---

### Post by ilinux_bj on 2008-12-27
> **gettinoriginal said:**
> libgtop2-dev  is in Synaptic, install it from there rather than trying to compose it from source.  But before you do, run:

sudo apt-get autoremove 
to get rid of the "not needed" in conky install.

I did it as you said,but it still reported the errors:


[COLOR="Red"]ilinux@ilinux-desktop:~$ sudo apt-get autoremove
[sudo] password for ilinux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sharutils
The following packages will be REMOVED:
  sharutils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 991kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181612 files and directories currently installed.)
Removing sharutils ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing sharutils (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sharutils
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Please help me!Thank you very much!

---

### Post by gettinoriginal on 2008-12-27
Try these two sites as they are both about cleaning up your system:  :P

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

