---
title: "Cannot install kde3"
date: 2010-08-20
forum: Desktop Environments
---

### Post by edabd on 2010-08-20
I tried to install kubuntu-desktop-kde3 but could not:

```
cannnot overwrite /etc/kde3/ksslcalist which is also in package kdelibs-data4
```There's also something about openoffice dependencies.  I don't use openoffice, but it seems to be interfering with the installation of kde3.

Other threads indicate that kde3 can be installed alongside kde4, but not here, evidently.  Any pointers, advice, hints appreciated.

---

### Post by edabd on 2010-08-20
Hate replying to my own post, but:

```
sudo apt-get install kubuntu-desktop-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs4c2a-kde3: Depends: kdelibs-data-kde3 (> 4:3.5.12) but it is not going to be installed
                    Depends: kdelibs-data-kde3 (< 4:3.5.13) but it is not going to be installed
``````
sudo apt-get install kdelibs-data-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  kdelibs-data-kde3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/7,612kB of archives.
After this operation, 30.1MB of additional disk space will be used.
(Reading database ... 160556 files and directories currently installed.)
Unpacking kdelibs-data-kde3 (from .../kdelibs-data-kde3_4%3a3.5.12-0ubuntu6+r1152788_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data-kde3_4%3a3.5.12-0ubuntu6+r1152788_all.deb (--unpack):
 trying to overwrite '/etc/kde3/ksslcalist', which is also in package kdelibs-data 4:3.5.10.dfsg.1-3ubuntu2
```

---

