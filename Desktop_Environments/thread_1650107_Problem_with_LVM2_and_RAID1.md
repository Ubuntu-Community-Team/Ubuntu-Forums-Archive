---
title: "Problem with LVM2 and RAID1"
date: 2010-12-21
forum: Desktop Environments
---

### Post by thermopyl on 2010-12-21
HI Guys

Hope someone can help me. 

I have a RAID1 setup (my OS is on a separate non-RAID disk) and have been using LVM to manage my volume on this array.

All been working fine for months, however yesterday I was copying some files to the volume and then all my data just disappeared! :(

If i now try to mount the volume, it appears to be empty. I have tested my array and the disks are ok.

If i run sudo pvscan, i get
PV /dev/md0  VG filesystem lvm2 [465.76 GiB / 776 MiB free]

..so that suggests that the volume still has the data on it.

Can anyone please suggest some actions on how i recover either the volume or the data on it????

---

