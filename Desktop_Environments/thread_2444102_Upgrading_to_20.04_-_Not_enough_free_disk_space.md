---
title: "Upgrading to 20.04 - Not enough free disk space"
date: 2020-05-24
forum: Desktop Environments
---

### Post by ubuntini2 on 2020-05-24
So spent the afternoon simply trying to upgrade from Ubuntu 18.04 to 20.04

using the following command
```
sudo update-manager -c -d
```

But repeatedly get the following error popup when the installation is half complete

> Not enough free disk space

The upgrade has aborted. The upgrade needs a total of 4,520 M free space on disk '/'. Please free at least an additional 3,510 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I've gone thru all the usual steps to free up space including removing ALL but necessary linux kernels et.

This is the result of a $df command

```
Filesystem     1K-blocks      Used Available Use% Mounted on
udev            32870524         0  32870524   0% /dev
tmpfs            6588324      2076   6586248   1% /run
/dev/sda2       41153856  38030268   1010052  98% /
tmpfs           32941612         0  32941612   0% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs           32941612         0  32941612   0% /sys/fs/cgroup
/dev/loop0         56320     56320         0 100% /snap/core18/1705
/dev/nvme1n1p1 491209736     71596 466116444   1% /mnt/xxxxxxxxxxxx
/dev/loop1        114432    114432         0 100% /snap/cmake/340
/dev/loop2        116992    116992         0 100% /snap/cmake/283
/dev/loop3         56320     56320         0 100% /snap/core18/1754
/dev/loop4         56064     56064         0 100% /snap/core18/1668
/dev/sda1         562084      7324    554760   2% /boot/efi
/dev/loop5        114432    114432         0 100% /snap/cmake/323
/dev/sda3      660427896 538425036  88432044  86% /home
tmpfs            6588320        52   6588268   1% /run/user/1000
```
Can any experienced linux users suggest what steps i should take next?
Thanks and regards

---

### Post by grahammechanical on 2020-05-24
Why are you using the -d switch? That will attempt to upgrade to Ubuntu 20.10 development version. Apart from that your root folder (sda2) is 98% full and your home folder (sda3) is 86% full. From Ubuntu 18.04 onwards a swap file is used instead of a swap partition. I have no idea how much swap space is used during an OS upgrade but you may be in a situation where the swap file cannot expand as large as it needs to. 

Regards

---

### Post by lazyteddy on 2020-05-29
> Why are you using the -d switch? That will attempt to upgrade to Ubuntu 20.10 development version.
No; if you want to update from LTS to LTS before the first point release, you have to use -d. LTS users won't get notified of a new version right away.

---

### Post by lazyteddy on 2020-05-29
One thing you can try to find out where the largest folders are is
```
cd /
sudo du -sh ./*
```
This might give you an idea what else you might have to remove or at least move out of the way for the upgrade.

---

### Post by anarchy-x on 2020-06-29
Look for cache, thumbnail, temp, and tmp directories. You'll *probably* be safe deleting the contents within.

---

### Post by ajgreeny on 2020-06-29
I would immediately suspect some runaway logs in /var/log but without more info it's impossible to know, but with a separate /home partition filling a 40G / partition is a bit unusual.

Run command ```
cd /var/log; du -h -d 1 | sort -h
```
to see all the first level folder content of /var/log or search other places by moving to a different folder at the start of the command.

---

### Post by rsteinmetz70112 on 2020-06-30
I'd check /var as well but you can also:

```
sudo apt autoremove
sudo apt autoclean
cd / 
sudo du -sh *
```
to see where that space has gone.
I agree it shouldn't be that full unless you've got something else on it.

---

