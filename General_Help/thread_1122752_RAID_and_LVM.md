---
title: "RAID and LVM"
date: 2009-04-11
forum: General Help
---

### Post by equick on 2009-04-11
Hi,

I've been through a fair amount of sites about RAID and LVM but couldn't find a definitive answer for my particular requirements.

I am installing a ubuntu server and trying to configure it to use RAID and LVM. (I am new to this). I have two SATA disks, one 250GB and one 500GB. I want to use RAID 1 for my home directory which is going to be 100GB, and from what I read I need to have another two RAID 1 devices for my /boot (500MB) and swap (1GB) filesystems. I have created these all as primary partitions (not logical, is that right?)

Once those 3 devices have been created, it seems that I'm only able to create one more RAID device which has to be the root directory. 

Ideally I'd like to combine the remaining space into two RAID devices specified as physical volumes on LVM and create my filesystems in there but not sure this can be done.

Could someone clarify for me how to set this up please?

Thanks,

Ed.

---

### Post by equick on 2009-04-12
OK well in the end I set up the following:

primary 500 MB /boot - RAID1
primary 100 GB /home - RAID1
primary 40 GB / - RAID1
logical 420 GB lvm - RAID0
primary 9 GB swap - RAID1

After installing ubuntu 8.10 server 64 bit I have:

# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md2              38448212   2425268  34069848   7% /
tmpfs                  3059360         0   3059360   0% /lib/init/rw
varrun                 3059360       152   3059208   1% /var/run
varlock                3059360         0   3059360   0% /var/lock
udev                   3059360      2828   3056532   1% /dev
tmpfs                  3059360         0   3059360   0% /dev/shm
/dev/md0                474348     37513    412343   9% /boot
/dev/md1              96124812    237524  91004340   1% /home

root@ubuntu:~# pvscan
  PV /dev/md3                      lvm2 [420.03 GB]
  Total: 1 [420.03 GB] / in use: 0 [0   ] / in no VG: 1 [420.03 GB]

Does this look okay?? 

Ed.

---

