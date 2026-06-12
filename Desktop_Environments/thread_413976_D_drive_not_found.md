---
title: "D: drive not found"
date: 2007-04-19
forum: Desktop Environments
---

### Post by mrsal on 2007-04-19
I created a Live CD of UBUNTU 7.04 and then booted my computer from the CD Drive.  UBUNTU loaded OK but the only hard drive that is shown under places-computer is my C; drive, identified as WinXP.  How can I mount the D: drive, on which most of my files reside?

I eventually will partition my C; drive to load UBUNTU on it, but would rather wait a while.  Thanks

---

### Post by taurus on 2007-04-19
You probably need to mount it by hand from a terminal.  What's the output of this command from a terminal then?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mrsal on 2007-04-20
I entered the command at the terminal and received this message:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

