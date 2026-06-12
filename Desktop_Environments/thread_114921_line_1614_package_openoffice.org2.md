---
title: "line 1614 package openoffice.org2"
date: 2006-01-09
forum: Desktop Environments
---

### Post by jhellen on 2006-01-09
What's wrong with my system :confused:  I can't install anything right now. 

$ sudo apt-get install gnome-bluetooth
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libbtctl2 libgnomebt0 python2.4-libbtctl
The following NEW packages will be installed:
  gnome-bluetooth libbtctl2 libgnomebt0 python2.4-libbtctl
0 upgraded, 4 newly installed, 0 to remove and 193 not upgraded.
Need to get 0B/317kB of archives.
After unpacking 1192kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1614 package `openoffice.org2':
 `Suggests' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

**My sources.list looks like this:**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Running both Gnome and KDE 3.4 :cool:

**This is what my /var/lib/dpkg/available says at line 1614:**
Suggests: myspell-dictionary, openoffice.org2-help, menu, ooqstart-gnome | oooqs-kde, unixodbc, cupsys-bsd, libsane, ttf-bitstream-vera, prelink, openoffice.org-hyphenation, openoffice.org2-thesaurus, libxrender1, msttcorefonts, openoffice.org2-gnome | openoffice.org2-kde, libgl1-mesa | libgl1, mozilla-firefox | firefox |  | mozilla-thunderbird, openoffice.org2-officebean, java-gcj-compat | j2re1.4 | java2-runtime, openoffice.org2-filter-so52

---

