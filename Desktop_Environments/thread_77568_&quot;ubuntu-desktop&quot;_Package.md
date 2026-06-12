---
title: "&quot;ubuntu-desktop&quot; Package"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Underhill on 2005-10-17
Hi,

Is it safe to remove "ubuntu-desktop"? What is it anyway? I'm trying to remove the HP Linux Printing and Imaging System (since I do not have any of that) but it depends on the "ubuntu-desktop" package. So, is it okay to remove?

---

### Post by Pablo_Escobar on 2005-10-17
ubuntu-desktop is a meta package for default installation, it's very safe to remove it, but before upgrading do Dapper Drake (6 month period :D) You'll need to install it.

---

### Post by angkor on 2005-10-17
```
apt-cache show ubuntu-desktop
Package: ubuntu-desktop
Priority: optional
Section: base
Installed-Size: 36
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Architecture: i386
Source: ubuntu-meta
Version: 0.80
Depends: [....]
Filename: pool/main/u/ubuntu-meta/ubuntu-desktop_0.80_i386.deb
Size: 10452
MD5sum: d3bc92d424da8b2f9318a2ae81bc6348
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system
 .
 It is safe to remove this package if some of the desktop system
 packages are not desired.  However, it is recommended that you keep
 it installed, because it is used to carry out certain upgrade
 transitions (such as adding new packages to the system).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-desktop
```

In other words, it's safe to remove but it is handy to have it installed when upgrading to the next release.

---

### Post by Underhill on 2005-10-17
Okay thanks Pablo_Escobar & angkor.

---

