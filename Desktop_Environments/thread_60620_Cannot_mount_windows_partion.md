---
title: "Cannot mount windows partion"
date: 2005-08-28
forum: Desktop Environments
---

### Post by t0m4s3 on 2005-08-28
finally i made my kubuntu work with nvidia, so here's my new problem

i had 2 PATA disc, each of them has 2 partition
first has windows ntfs partition an kubuntu ext 3 partition, second both ntfs partitions
Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13545   102400168+   7  HPFS/NTFS
/dev/hda2           13546       15505    14817600   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1274    10233373+   7  HPFS/NTFS
/dev/hdb2            1275        9729    67914787+   f  W95 Ext'd (LBA)
/dev/hdb5            1275        9729    67914756    7  HPFS/NTFS


i can mount hdb1/5 by typing "sudo mount /dev/hdb1 /media/disk_c" and also hdb5

but for windows partition it's looking like this

tomase@amd64:~$ sudo mount /dev/hda1 /media/disk_c/
mount: /dev/hda1 already mounted or /media/disk_c/ busy
mount: according to mtab, /dev/hda1 is mounted on /
tomase@amd64:~$



any ideas? THX

---

### Post by incinerator on 2005-08-28
could you please post the contents of your /etc/fstab and /etc/mtab?

---

### Post by snpz on 2005-08-29
Edit your /etc/fstab 
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by t0m4s3 on 2005-08-29
after editing /etc/fstab just like in guide and restart of computer, everything is working fine... thx

---

