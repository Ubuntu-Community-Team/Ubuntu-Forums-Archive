---
title: "Broken package screwing up apt-get"
date: 2006-03-04
forum: Desktop Environments
---

### Post by napoleon on 2006-03-04
I'm having a problem using apt-get.  I tried to remove amarok completely to install the beta and apt-get gave me a broken package error about amarok-gstreamer.  I tried to fix with an update/upgrade first, then apt-get -f install, apt-get -f upgrade to no avail.  I decided it wasn't a big deal, but in the process of trying to install a library to compile c++, apt-get wouldn't install anything because of the broken amarok package.  Here's the outputs...

sudo apt-get remove amarok
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amarok
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 17.3MB disk space will be freed.
Do you want to continue [Y/n]?
dpkg: parse error, in file `/var/lib/dpkg/status' near line 397 package `amarok-gstreamer':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  amarok-gstreamer
Suggested packages:
  gstreamer0.8-plugins gstreamer0.8-mad
The following NEW packages will be installed:
  amarok-gstreamer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/59.5kB of archives.
After unpacking 217kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 397 package `amarok-gstreamer':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

Like I said, apt-get is completely useless right now, so any help would be appreciated. Thanks!

---

### Post by teaker1s on 2006-03-04
try this

 apt-get install -f

---

### Post by napoleon on 2006-03-04
apt-get install -f gives me the same result as apt-get -f install.

---

### Post by Xian on 2006-03-04
[QUOTE=napoleon]dpkg: parse error, in file `/var/lib/dpkg/status' near line 397 package `amarok-gstreamer':
 missing version[/QUOTE]

Your status file is corrupt. Open /var/lib/dpkg/status-old (or even /var/backups/dpkg.status.*) and compare to the current file. Check for differences and attempt to fix the version error noted by line number, or just move the entire backup file into place. Keep copies of each until your system is back in working order.

---

### Post by az on 2006-03-04
Try:

sudo dpkg --clear-avail
sudo apt-get update
and then try removing the package.

---

