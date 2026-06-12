---
title: "SoftRAID 1 Ubuntu server 8.10"
date: 2009-02-27
forum: General Help
---

### Post by stek_87 on 2009-02-27
Hi!

I need to set up a RAID1 volume in Ubuntu server 8.10.

I've got 3 disks.

IDE  80gb - single disk - /
SATA 1024gb - RAID1 - /var/vm <-- not yet set up
SATA 1024gb - RAID1 - /var/vm <-- not yet set up

So.. I have installed my system on my 80gb disk drive, and I have run apt-get update, apt-get upgrade.

Can some one please direct me to a good guide?

I believe I will use mdadm to set up the volume and smartd for monitoring it. Is it a better way to go?

What will happen if one disk goes down? The system will be able to run normally?
What happens after reboot? Will the disk complain? Will I have to do any action to make it work with only one disk running?

/S

---

### Post by justleen on 2009-02-27
mdadm is the way to go. Its easiest to maintain. I dont have a good guide though, but im sure there are plenty to be found.

If one disk dies (in the raid, not the 80gb system disk :)), your system will keep on running fine. Depening on the monitor you'll get a trigger that you need to replace on of the disks..

---

### Post by fjgaude on 2009-02-27
Here's a good link to start with:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Let us know how you are doing.

---

### Post by stek_87 on 2009-03-04
Hi! Thanks for the help..

This is how i did it.
```

sudo su -
apt-get update
apt-get upgrade

init 6

sudo su -

apt-get -&#8211;no-install-recommends install mdadm


fdisk /dev/sdb
create partition
primary
whole disk size
write changes to disk

fdisk /dev/sdc
create partition
primary
whole disk size
write changes to disk

mdadm --create /dev/md0 --chunk=8 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

mkfs.ext3 /dev/md0
tune2fs -m 1 /dev/md0
mkdir /var/vm

nano /etc/fstab

/dev/md0 /var/vm ext3 default 0 0

init 6

login....

sudo cat /proc/mdstat 
```


If some one is curious, this is a server I set up for running vmware server 2.0. 64 bit

It is now up running with 5 servers on it.



rgds
/S

---

