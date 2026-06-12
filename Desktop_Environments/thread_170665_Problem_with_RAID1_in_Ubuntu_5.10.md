---
title: "Problem with RAID1 in Ubuntu 5.10"
date: 2006-05-05
forum: Desktop Environments
---

### Post by zezami on 2006-05-05
I've just installed Ubuntu with RAID1 and everything went fine. Got the system booting on the 2 disks with GRUB. Then i began testing and disconnected drive 2 from the array. It boots up, but it wont automatically rebuild the array. This is what i get from /proc/mdstat:

Personalities : [raid1]
md2 : active raid1 sda3[0] sdb3[1]
      979840 blocks [2/2] [UU]

md1 : active raid1 sda2[0]
      78123968 blocks [2/1] [U_]

md0 : active raid1 sda1[0]
      64128 blocks [2/1] [U_]

unused devices: <none>

md0 is /boot, md1 / and md2 is swap

the swap rebuilds just fine when i reinserted the disk but not /boot or /. 

Here's the md output from the kernellog:

[4294678.679000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294678.682000] md: raid1 personality registered as nr 3
[4294678.921000] devfs_mk_dev: could not append to parent for md/0
[4294678.925000] md: md0 stopped.
[4294678.925000] md: bind<sdb1>
[4294678.925000] md: bind<sda1>
[4294678.925000] md: kicking non-fresh sdb1 from array!
[4294678.925000] md: unbind<sdb1>
[4294678.925000] md: export_rdev(sdb1)
[4294678.926000] raid1: raid set md0 active with 1 out of 2 mirrors
[4294678.938000] devfs_mk_dev: could not append to parent for md/1
[4294678.941000] md: md1 stopped.
[4294678.942000] md: bind<sdb2>
[4294678.942000] md: bind<sda2>
[4294678.942000] md: kicking non-fresh sdb2 from array!
[4294678.942000] md: unbind<sdb2>
[4294678.942000] md: export_rdev(sdb2)
[4294678.942000] raid1: raid set md1 active with 1 out of 2 mirrors
[4294678.960000] devfs_mk_dev: could not append to parent for md/2
[4294678.963000] md: md2 stopped.
[4294678.964000] md: bind<sdb3>
[4294678.964000] md: bind<sda3>
[4294678.964000] raid1: raid set md2 active with 2 out of 2 mirrors
[4294678.985000] Attempting manual resume
[4294678.988000] swsusp: Suspend partition has wrong signature?

Any ideas on how to fix this is appreciated!

Thanks

/Johan

---

### Post by zezami on 2006-05-05
Wey

Found out how to fix it! 
mdadm /dev/md1 -a /dev/sdb2
and
mdadm /dev/md0 -a /dev/sdb1 

did the trick..

anyone know if its possible for this to be done automatically and not having to type it  every time? (not that you're supposed to have to type it all the time but still)

---

