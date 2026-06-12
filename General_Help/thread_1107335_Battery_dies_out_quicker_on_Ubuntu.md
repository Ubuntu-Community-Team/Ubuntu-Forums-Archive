---
title: "Battery dies out quicker on Ubuntu?"
date: 2009-03-26
forum: General Help
---

### Post by aceplayer97 on 2009-03-26
I recently switched to Ubuntu from Windows XP. So far Ubuntu is absolutely perfect. There is one problem though. On Windows XP I would have a minimum of at least 2.5 hours of battery life but now when I switched to Ubuntu I only have 1 hour of battery life. Why is that? Does Ubuntu use up a lot more resources than Windows XP? Are there tips to save and increase battery life?

---

### Post by Wayne_V on 2009-03-26
see  "apt-cache show laptop-mode-tools ubuntu-laptop-mode"

---

### Post by aceplayer97 on 2009-03-26
Well I typed that in terminal and this is what I got:

Package: laptop-mode-tools
Priority: optional
Section: utils
Installed-Size: 468
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Samwel <bart@samwel.tk>
Architecture: all
Version: 1.45-1ubuntu4
Depends: lsb-base (>= 3.0-10), util-linux (>= 2.13)
Recommends: acpid | apmd | pbbuttonsd | pmud, hdparm, hal
Suggests: sdparm
Conflicts: noflushd
Filename: pool/main/l/laptop-mode-tools/laptop-mode-tools_1.45-1ubuntu4_all.deb
Size: 104362
MD5sum: a8e2146b737037a924ec6791d665ec60
SHA1: 389a1fa94f785b894714dda1e0b4e56834e43c88
SHA256: 8fd6461390e276a17f507aca2e168184ce8688eeac9aa680a92298024ab8ea7c
Description: Scripts to spin down hard drive and save power
 Laptop mode is a Linux kernel feature that allows your laptop to save
 considerable power, by allowing the hard drive to spin down for longer
 periods of time. This package contains the userland scripts that are
 needed to enable laptop mode. It includes support for automatically
 enabling laptop mode when the computer is working on batteries. It also
 supports various other power management features, such as starting and
 stopping daemons depending on power mode, automatically hibernating if
 battery levels are too low, and adjusting terminal blanking and X11
 screen blanking.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mobile-mid, mobile-mobile

Package: ubuntu-laptop-mode
Priority: optional
Section: universe/utils
Installed-Size: 56
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Matthew Garrett <mjg59@srcf.ucam.org>
Architecture: all
Version: 1.0-1
Recommends: hdparm
Conflicts: laptop-mode-tools
Filename: pool/universe/u/ubuntu-laptop-mode/ubuntu-laptop-mode_1.0-1_all.deb
Size: 3306
MD5sum: 9bb2b579633fdd9588b4bd70b5598cbd
SHA1: cfd5622bc816351400de8c28f891775840edcfea
SHA256: d9e568ca12f6914ada88ce5c500dc31c0147e9586194b5b2b9e0a2039a34572e
Description: Support for reducing hard drive power consumption
 Laptop mode is a Linux kernel feature that allows the system to reduce power
 consumption by allowing the hard drive to spin down for longer periods of
 time. This package contains a script to control these kernel parameters.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by philinux on 2009-03-26
laptop-mode-tools is installed by default but i think you have to install ubuntu-laptop-mode.

---

### Post by Wayne_V on 2009-03-26
Yes - that is showing the packages available for laptop support.  Install one (I prefer laptop-mode-tools) and then see /etc/init.d/laptop-mode, /etc/default/laptop-mode, config files in /etc/laptop-mode, etc

---

### Post by aceplayer97 on 2009-03-26
Well I installed laptop-mode-tools from Synaptic Package Manager but it seems to have made no difference. Is there something else I'm supposed to do after installing it?

---

### Post by aeiah on 2009-03-26
> **aceplayer97 said:**
> Well I installed laptop-mode-tools from Synaptic Package Manager but it seems to have made no difference. Is there something else I'm supposed to do after installing it?

yea. the 2nd part of wayne's sentence:
> and then see /etc/init.d/laptop-mode, /etc/default/laptop-mode, config files in /etc/laptop-mode, etc

---

