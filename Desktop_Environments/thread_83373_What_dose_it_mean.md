---
title: "What dose it mean?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by kapa_des on 2005-10-28
root@kapaciu:/home/kapaciu # apt-get install valknut
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs4: Depends: kdelibs-data (>= 4:3.3.0) but it is not going to be installed
  valknut: Depends: libdc0c2 (< 0.3.7-99) but it is not going to be installed
           Depends: libdc0c2 (>= 0.3.7-0) but it is not going to be installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not going to be installed
           Depends: libxml2 (>= 2.6.20) but 2.6.17-0ubuntu1 is to be installed
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/re$ Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_re%24_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@kapaciu:/home/kapaciu #

---

### Post by KingBahamut on 2005-10-28
run 

apt-get -f install 

and give us the output after.

---

### Post by Kyral on 2005-10-28
Or your sources.list

It looks like a malformed sources.list more than anything else

---

