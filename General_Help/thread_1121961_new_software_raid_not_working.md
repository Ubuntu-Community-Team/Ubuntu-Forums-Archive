---
title: "new software raid not working"
date: 2009-04-10
forum: General Help
---

### Post by nex9 on 2009-04-10
Greetings - I need some help with getting a software raid10 working with ubuntu 8.10. I can get it working manually, but when I reboot I cannot mount the partition. I get the following error:

mount /dev/md0 /data -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail shows:

EXT3-fs: unable to read superblock

At this point, my  /proc/mdstat contains this (not sure how it got in this state?!? what is md127?)
Personalities : [raid10] 
md127 : inactive sdc1[1](S) sde1[3](S) sdd1[2](S)
      1465151808 blocks
       
unused devices: <none>

At this point I'm stuck. I'm trying to re-initialize the raid, and getting this:
mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: layout defaults to n1
mdadm: chunk size defaults to 64K
mdadm: /dev/sda1 is too small: 0K
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: create aborted

---

### Post by nex9 on 2009-04-10
After I rebooted, I was able to re-create the raid with:

mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1

Then, I was able to  mkfs.ext3 /dev/md0 and 
mount /dev/md0 /data -t ext3

However, when I reboot, I cannot mount and /proc/mdstat shows:

Personalities : [raid10] 
unused devices: <none>

---

