---
title: "cryptsetup password asked twice at boot"
date: 2015-12-21
forum: Desktop Environments
---

### Post by Homer on 2015-12-21
Hello,

I just installed a new ubuntu 15.10 desktop system.  For the first time, I configured cryptsetup in order to have my hard drive completely encrypted.  I have 3 luks partitions (/, /home and swap).  Everything work fine.

Problem is when I boot my computer, I have to enter the password twice (one time for the root partition, then another one for the swap partition).  I'm not asked for the passphrase for the home partition.  All partitions use the same passphrase. Why do I have to unlock the encrypted swap after unlocking the root partition?

---

### Post by TheFu on 2015-12-24
Did you use LVM?
Please post the output of **lsblk** and please, please, please, use code tags so things line up and are easy to read.  Doh!

See how the sda5 partition below is fully encrypted and LVM is used to have /, swap and /Stuff?  1 encrypted volume = 1 request for the password.
```
$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /Stuff
```

Anyway, hope this helps.  LVM is slightly more complicated, but immensely more flexible.

---

