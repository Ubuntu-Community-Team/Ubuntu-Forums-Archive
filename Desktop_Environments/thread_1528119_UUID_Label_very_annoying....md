---
title: "UUID Label very annoying..."
date: 2010-07-10
forum: Desktop Environments
---

### Post by asbesto on 2010-07-10
Hi, 

since the last version of ubuntu, when inserting any USB disk into any computer, I had something like this:

```

/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=udisks)

```

Now, with Ubuntu 10.04, I have

```

/dev/sdb1 on /media/f2c2a735-8451-4e1f-b6c6-bd509892722e type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1 on /media/7ca71811-144b-4812-84df-dbd60d5202e6 type ext3 (rw,nosuid,nodev,uhelper=udisks)

```

:confused:

that is very, very annoying, because I'm a computer user, I just want to plug my disk and find it as I expect to be called: DISK. I don't care about any UUID, this is totally unuseful to me nor to any normal user. 

This way of associate the mountpoint to the UUID also causes a lot of confusion on newcomer users that expect their devices to be named with human readable names instead of hexadecimal UUID's: something like KINGSTON, USBPEN, DRIVE, DISK...

[-X

How to get rid FOREVER of those unuseful and unpratical UUID's used as mount points? 

](*,)

---

### Post by ronnielsen1 on 2010-07-10
[CENTER]You have to set labels for the partitions in question. I installed gparted and relabeled a windows partition as windows and a backup as backup. Then I rebooted and no more UUID:D
[/CENTER]

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/390304](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/390304)

> I can confirm this and reproduce it on many machines running Karmic. If a  partition is unlabeled, mounting it will mount it to /media/$UUID  instead of /media/disk-#

---

### Post by sisco311 on 2010-07-10
Labeled devices that automount will be mounted in the /media directory using their label as the mount point, /media/<label>.

To change the label go to System -> Administration -> Disk Utility

---

