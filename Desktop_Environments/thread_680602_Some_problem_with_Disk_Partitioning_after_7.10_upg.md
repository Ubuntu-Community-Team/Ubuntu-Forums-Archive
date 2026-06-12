---
title: "Some problem with Disk Partitioning after 7.10 upgrade"
date: 2008-01-28
forum: Desktop Environments
---

### Post by alexagosto62 on 2008-01-28
Hi folks.
Before installing the Ubuntu 7.10, kernel 2.6.22-14-generic, all was fine and i was able to use Gparted, fdisk, and regularly configuring my hda disk with many partitions. I was able mount W32 partitions both in ro and in rw modes.
Now i have some problems ... I've found that my 'hda' device does not esist more and i see a new sda (scsi) disk instead of the hda one. Now if i attempt to use Gparted, it thinks a lot before showing me a unique unpartitioned sda disk ...., If i attempt to use fdisk it says: 

alessandro@alessandro-laptop:~$ sudo fdisk -l
[sudo] password for alessandro:

Unable to seek on /dev/sda

In order to mount my previous W32 hdax partitions, i found that all have changed name and order (sda1, sda2, sda7 instead of hda1, hda2, hda5), and they don't allow me to mount them rw (even if the mount command gives no errors).

What has been happened?
I will appreciate any helps.

Alessandro

---

