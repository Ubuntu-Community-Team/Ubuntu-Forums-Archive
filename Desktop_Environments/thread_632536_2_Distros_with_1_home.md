---
title: "2 Distros with 1 /home ?"
date: 2007-12-05
forum: Desktop Environments
---

### Post by rollerdiscoman on 2007-12-05
hello, I want to install Linux Mint or Suse or Fedora on my HDD with Ubuntu. I want my Ubuntu and (other distro) to share the same /home folder, though... is this possible?

which distro should I choose, I'm interested in hearing..

---

### Post by werfu on 2007-12-05
From a technical point of view Linux Mint is at the first sight, the less trouble-some to install. It is ubuntu based and you can even install software from ubuntu repository in it. Just install ubuntu, using three partitions, one for ubuntu, another for linux mint and another for your home. Install ubuntu first, then linux mint. After this you'll have to setup grub correctly which can be a little touchy. But hey, RTM of Grub ;)

---

### Post by pyro_xp2k on 2007-12-05
> **rollerdiscoman said:**
> hello, I want to install Linux Mint or Suse or Fedora on my HDD with Ubuntu. I want my Ubuntu and (other distro) to share the same /home folder, though... is this possible?

which distro should I choose, I'm interested in hearing..

If your /home folder is in its own partition, then sure.
All you'd have to do when in the partitioning program or in /etc/fstab is just set the mount point of your the partition to /home in the other system.

---

### Post by trippinnik on 2007-12-06
Installing Linux Mint to a seperate partition would be a wast of space though.  It's basically a respin of Ubuntu with a few different packages installed instead and proprietary stuff isntalled already.
Using the same /home partition with different installs will mess with the permissions, espceially Fedora - Ubuntu combo as they use a different UID scheme.  You'd probably need to make it world writable, which isn't the safest way to leave your data.

---

### Post by ixlam on 2007-12-07
2 Distros or more is possible but User Groups and permissions becomes an issue between Fedora & ubuntu for example. It is possible tho..  typical Ubuntu user ID=1000 Fedora=500 just keep that in mind when creating users.

---

