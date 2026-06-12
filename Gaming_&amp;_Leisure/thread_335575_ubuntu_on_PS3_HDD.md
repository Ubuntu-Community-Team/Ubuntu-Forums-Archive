---
title: "ubuntu on PS3 HDD"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by inee on 2007-01-10
[http://www.justlinux.com/forum/showthread.php?p=862262#post862262](http://www.justlinux.com/forum/showthread.php?p=862262#post862262)


finally got it in on the ps3's hdd.


1. install fedora minimum
2. mount /dev/cdrom /mnt/cdrom
3. yum install dhclient
4. yum install wget
5. copy debootstrap to /tmp
6. zcat debootstrap
7. mkdir /mnt/ubuntu and /mnt/ubuntu/boot
8. debootstrap edgy to /mnt/ubuntu
9. copy fedora's kernel and initrd stuff
10. edit fstab and kboot configurations
11. install xbuntu desktop (ubuntu had a lot of dependency resolving)
12. install ps3videomode
13. configure xorg


NOTE: ubuntu will not let you log in as root. so before restarting you may want to edit your passwd, grp, and/or use passwd root to enable it if you want.

---

### Post by inee on 2007-01-10
okay, im now trying to install kubuntu instead. everything seems to be okay so far.

---

### Post by Ciego on 2007-01-17
I would really like to do this without installing Fedora first.  I have been working on it using the Gentoo live CD but I still have a few kinks to work out.

---

