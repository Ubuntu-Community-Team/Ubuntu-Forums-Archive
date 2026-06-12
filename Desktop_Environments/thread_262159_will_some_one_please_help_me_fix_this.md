---
title: "will some one please help me fix this?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-21
dougie@DougiesToyBox:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core
The following NEW packages will be installed:
  openoffice.org-core
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
13 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 83.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 91944 files and directories currently installed.)
Unpacking openoffice.org-core (from .../openoffice.org-core_2.0.3-4ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/program/ooqstart', which is also in package openoffice.org-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$

---

### Post by n_hendrick on 2006-09-21
try to go to the var/cache/apt/archive directory and manually install the specific openoffice package with dpkg -i --force-overwrite nameofpackage . 
then just run apt-get -f install again and it should work.

---

### Post by abiezerm on 2006-09-21
well i think : sudo apt-get clean (or clear)

---

### Post by DougieFresh4U on 2006-09-21
Neither one worked. Some please help? It might be time to throw in the Puppy disc!(just kidding)

---

