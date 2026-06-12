---
title: "Win XP after ubuntu"
date: 2006-06-21
forum: Desktop Environments
---

### Post by k_smolka on 2006-06-21
hi all 

I am currently running ubuntu and i need to install windows as a duel boot for visual studio. If i simply stick the windows disk in and install it on a new partition will grub automatically be adjusted.

Ie will it muck up my existing setup.

Thanks in advance.

Karl

---

### Post by stychman on 2006-06-21
Grub will not be updated because Windows doesn't recognize any boot loader other than a windows boot loader.  From my experience the best way to do things is to partition the drive using Fdisk or some other drive partitioner like QTParted from a live CD.  Install Windows on one partition then install Ubuntu.  Grub will then install a boot loader to recognize Windows and Ubuntu.  I've never had to adjust my grub menu after doing this but I know some people have.  I'm not sure if you can install windows and then go in and edit your grub menu after this.

---

### Post by comppsyco on 2006-06-21
See above for best way to do it, however, you may be able to install Windows, then boot from a LiveCD to edit grub configuration files. It is true, however, that once you install Windows, until you edit your grup config, you won't be able to boot to linux.

---

### Post by lamego on 2006-06-21
Here are some [instructions ](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) for restoring grub after installing Windows.

---

