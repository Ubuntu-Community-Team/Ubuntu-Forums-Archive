---
title: "Attempted a speed tweak, confused that one step didn't work."
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by CheshireMac on 2007-12-03
Hey folks. I've been fiddling with Gutsy and Firefox a bit lately, and I discovered a nice tutorial on how to speed things up a bit, machine-wise. [link]http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed[/link]
I followed through to the last step of the first tut, and I can't figure for the life of me what I'm supposed to enter for "your drive" after /dev/. 
Any help would be appreciated, and if you've got any other laptop tweak ideas I'd love to hear it. :) Thanks.

---

### Post by yabbadabbadont on 2007-12-03
Edit: Your link is broken.  You need to remove the space.

---

### Post by yabbadabbadont on 2007-12-03
Please post the output of the following commands when run in a terminal window:
```
mount
sudo fdisk -l
```

---

### Post by CheshireMac on 2007-12-03
mac@mac1:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=mac)
mac@mac1:~$ sudo fdisk -l
[sudo] password for mac:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95e695e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Sola

---

### Post by yabbadabbadont on 2007-12-03
/dev/sda1 is your "drive".  (Your root partition)

---

