---
title: "Connecting an ISCSI volume crashes Debian 12"
date: 2023-11-30
forum: Debian
---

### Post by Drenriza on 2023-11-30
Hi All
I know that this is not quite the correct place for a Debian 12 question, but I have used this forum for many years and always found extremely
helpful people, so I hope you will bear with me since no one has any thoughts on the Debian forum for this issue.

My issue is as follows
I have a QNAP NAS where i have created an ISCSI target that i would like to connect to in Debian.

```
$ iscsiadm  --mode discovery --type sendtargets --portal [IP]
```

Shows me all available targets.

```
$ sudo iscsiadm  --mode node  --targetname "[TARGET]" --portal "[IP]" --login
```

Allows me to login to the target.

```
$ sudo dmesg
```

Shows my target getting recognised
> scsi host6: iSCSI Initiator over TCP/IP
scsi 6:0:0:0: Direct-Access     QNAP     iSCSI Storage    4.0  PQ: 0 ANSI: 5
sd 6:0:0:0: Attached scsi generic sg1 type 0
sd 6:0:0:0: [sdb] 2097152000 512-byte logical blocks: (1.07 TB/1000 GiB)
sd 6:0:0:0: [sdb] Write Protect is off
sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 08
sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 6:0:0:0: [sdb] Preferred minimum I/O size 1048576 bytes
sd 6:0:0:0: [sdb] Optimal transfer size 1048576 bytes
 sdb: sdb1
sd 6:0:0:0: [sdb] Attached SCSI disk

fdisk created a partition and mkfs.ext4 made an ext4 drive no issues.

Manually mounting the drive also works with
```
$ sudo mount /dev/sdb1 /mnt/mountPoint
```

node.startup is set to 'automatic' under
> /etc/iscsi/nodes/[IQN]/default

And my /etc/fstab looks as follows
> /dev/sdb1    /mnt/mountPoint    ext4    defaults    0    1

The issue is if i keep the disk mounted my system crash after 5 - 10 minutes, and if i restart the system after mounting the drive but before the crash, the whole system is unable to boot and Debian says that the root account is locked.

I cannot get a working bash shell by editing the kernel and adding > init=/bin/bash fsck fails, all system mounts fail, and the only thing that i have found that works is to live CD the system and remove the > /etc/fstab line for the ISCSI drive.

Are there anyone that can tell me if i have made an obvious mistake that explains what i am experiencing?

Are there anything i can try to figure out what is going on? I am NOT an iSCSI expert by any means.

Thank you in advance
Best regards

---

### Post by coffeecat on 2023-11-30
*Thread moved to the **Debian** sub-forum.*

---

