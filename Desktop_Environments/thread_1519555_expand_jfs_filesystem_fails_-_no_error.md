---
title: "expand jfs filesystem fails - no error"
date: 2010-06-28
forum: Desktop Environments
---

### Post by defunkt on 2010-06-28
i have a file server and have added another 2TB drive into my array (hardware raid card).  ubuntu detects that the total volume has changed and now i need to expand the JFS volume to consume the remaining volume.  the remaining volume should be around 10TB with a JFS file system using a GPT file table.

in all of my readings I've found that for JFS that all that should be done is: sudo mount -vvv -o remount,resize /RAID
output:

sudo mount -vvv -o remount,resize /RAID 
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "/dev/sdb1"
mount: node:  "/RAID"
mount: types: "jfs"
mount: opts:  "defaults,remount,resize"
mount: mount(2) syscall: source: "/dev/sdb1", target: "/RAID", filesystemtype: "jfs", mountflags: -1058209760, data: resize
/dev/sdb1 on /RAID type JFS (rw,resize)


not sure if a negative number for mountflags is normal?  but i dont see any errors...



Ive also used gparted, and it fails to expand the partition, but does not say why, it just says it failed to grow the jfs file system.  gparted shows that it supports all of the JFS functions such as expanding the partition (jfsutils is installed).  

i have double and triple checked the kernel config to verify that all of the JFS items have been turned on.  

i had a post last week on an error with JFS not loading after reboot, but a simple forced fsck.jfs cleaned that issue up:
[http://ubuntuforums.org/showthread.php?t=1514838](http://ubuntuforums.org/showthread.php?t=1514838)

ubuntu 32 bit lucid that's up-to-date with a Areca hardware controller

any help or pointers would be appreciated, i did read somewhere that the 2.6.0 kernel was glitchy or problematic with JFS...  im thinking there has to be something simple im overlooking.

thanks in advance.

---

### Post by defunkt on 2010-06-28
i figured it out...  

after expanding my array, my backup GPT table (which resides at the end of the disk), was nol onger at the end of the disk (due ot the added space to teh RAID).  i needed to fix this through parted before coninueing to expand the partition.

gparted would not do this, you must go into parted and select the drive.  it should then as you if you want to repair this problem.  select yes and then you can expand your array without any problems.

---

