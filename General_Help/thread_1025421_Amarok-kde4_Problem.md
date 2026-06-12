---
title: "Amarok-kde4 Problem"
date: 2008-12-30
forum: General Help
---

### Post by tarun86 on 2008-12-30
> tarun@mysterious-desktop:/usr/lib/kde4/share/kde4/apps/cmake/modules$ sudo apt-get install amarok-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amarok-kde4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs5-dev: Depends: kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3) but 4:4.1.2-0ubuntu1~hardy1~ppa1 is to be installed
  kdepimlibs5-dev: Depends: kdelibs5-dev (>= 4:4.1.0) but 4:4.0.5-0ubuntu1~hardy3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



> tarun@mysterious-desktop:/usr/lib/kde4/share/kde4/apps/cmake/modules$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libio-string-perl akiradnews libaudio-wav-perl libmp4-info-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdelibs5-dev
Suggested packages:
  kdelibs5-doc
The following packages will be upgraded:
  kdelibs5-dev
1 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
36 not fully installed or removed.
Need to get 0B/1463kB of archives.
After this operation, 397kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdelibs5-dev
Install these packages without verification [y/N]? y
(Reading database ... 347251 files and directories currently installed.)
Preparing to replace kdelibs5-dev 4:4.0.5-0ubuntu1~hardy3 (using .../kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb) ...
Unpacking replacement kdelibs5-dev ...
dpkg: error processing /var/cache/apt/archives/kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/apps/cmake/modules/FindXine.cmake', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant remove anything now. Cant install anything. 

Tried:
> sudo apt-get remove --purge amarok-kde4
gives the same error of dpkg: error processing try apt-get -f install.

Any solution ??

---

### Post by fooman on 2008-12-30
give these a try:

```
sudo dpkg --configure -a && sudo apt-get update
```

if those work...then try:

```
sudo apt-get -f install
```

hope that helps.

---

### Post by tarun86 on 2008-12-30
same error:

> Preparing to replace kdelibs5-dev 4:4.0.5-0ubuntu1~hardy3 (using .../kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb) ...
Unpacking replacement kdelibs5-dev ...
dpkg: error processing /var/cache/apt/archives/kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/apps/cmake/modules/FindXine.cmake', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-dev_4%3a4.1.2-0ubuntu1~hardy1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1


The problem is this: kdelibs5-dev depends on kdelibs5 which is ver 4.0.5. kdepimlibs5-dev requires kdelibs5-dev to be >= 4.1.0 & kdelibs5 version >= 4.1.0 isnt there in repo for Hardy.

> The following packages have unmet dependencies:
  kdelibs5-dev: Depends: kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3) but 4:4.1.2-0ubuntu1~hardy1~ppa1 is installed
  kdepimlibs5-dev: Depends: kdelibs5-dev (>= 4:4.1.0) but 4:4.0.5-0ubuntu1~hardy3 is installed

What do I do ? compile this crap or something ?

---

