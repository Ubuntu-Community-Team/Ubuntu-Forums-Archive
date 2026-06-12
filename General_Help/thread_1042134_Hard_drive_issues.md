---
title: "Hard drive issues"
date: 2009-01-17
forum: General Help
---

### Post by djbushido on 2009-01-17
Whenever I shutdown, my drive apparently gets partially corrupted. This leads to next time the drive gets mounted read-only, and then X, among other applications, can't start. This leads to fail. Then, I reboot, the drive gets checked, errors are found and fixed, then I reboot again, and then I can get back in.

Any ideas on how to avoid this? I am using a standard hard drive connected via USB.

---

### Post by taurus on 2009-01-17
Maybe your USB drive is about to go.

Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by djbushido on 2009-01-17
Pretty sure it's not the drive. Hope its not. That would be bad.
Anyway:

fdisk: ```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9af30f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4fee4fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8bbb8bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3544    28467148+  83  Linux
/dev/sdc2            7230        7297      546210   82  Linux swap / Solaris
/dev/sdc3            3545        7229    29599762+   5  Extended
/dev/sdc5            3545        7032    28017328+  83  Linux
/dev/sdc6            7033        7229     1582371   82  Linux swap / Solaris

Partition table entries are not in disk order

```

fstab: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=98e1986d-f6f0-4d07-ba04-ef264ecb68a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

df: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc5              27G   14G   12G  56% /
tmpfs                 347M     0  347M   0% /lib/init/rw
varrun                347M  216K  346M   1% /var/run
varlock               347M     0  347M   0% /var/lock
udev                  347M  2.8M  344M   1% /dev
tmpfs                 347M     0  347M   0% /dev/shm
lrm                   347M  2.0M  345M   1% /lib/modules/2.6.27-9-generic/volatile

```

And if it was a drive problem (which again I'm sure it's not, because I'm dual-booting fedora 10 fine), how would one find out?

ALSO: the /dev/sda and /dev/sdb are both windows partitions. Just so you know.

EDIT: Also so you know, the Xubuntu is /dev/sdc5, but Fedora (sdc1) has boot control.

---

### Post by djbushido on 2009-01-18
Question/bump

Would it be a HUGE problem to take out the errors=remount-ro part of fstab?
And is it at all possible to move a partition, as currently sdc5 is part of an extended partition, and I would prefer it as a primary partition. Preferably keeping UUID.

---

### Post by djbushido on 2009-01-20
Bump.

Anybody have any ideas?

---

