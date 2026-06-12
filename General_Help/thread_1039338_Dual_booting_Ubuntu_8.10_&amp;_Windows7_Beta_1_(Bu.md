---
title: "Dual booting Ubuntu 8.10 &amp; Windows7 Beta 1 (Build 7000)"
date: 2009-01-14
forum: General Help
---

### Post by paragkalra on 2009-01-14
Hey Chums,

At present I have a dual boot system - Ubuntu 8.10 & Debian 4 Release 5. Here is the output of "#fdisk -l /dev/sda"

/dev/sda1   *           1        3187    25599546   83  Linux
/dev/sda2            3188        5580    19215360   83  Linux
/dev/sda3            5581        6077     3992152+  82  Linux swap / Solaris
/dev/sda4            6078       19457   107474850   83  Linux

"/dev/sda1" belongs to Debian and /dev/sda2 belongs to Ubuntu 8.10. I am planning to wipe off Debian from /dev/sda1 and install Windows7 Beta1 on it. 

No no no please don't jump to any conclusion. I am still very much a committed Linux user. Just wanna try Windows7 since it's free till August. :D

Ok coming to the point - Since installing Windows7 will overwrite the MBR I am planning to recover it using the Live CD. So basically I want a dual boot system having Ubuntu 8.10 and Windows7

Here are the URLs I am looking forward to:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Before I try them I had few queies:

1. Has anyone tried dual booting Ubuntu 8.10 & Windows7 (build 7000)?
2. Any better & straight forward pointers to proceed ahead that will make me accomplish my task in one go?

---

### Post by Titan8990 on 2009-01-14
You will be the first that I have heard of doing it. From what I have read Windows 7 is mainly a UI upgrade for Vista so I doubt grub will have problems booting it.

---

