---
title: "Strange partition issue..."
date: 2009-01-07
forum: General Help
---

### Post by mplex2000 on 2009-01-07
I was running solaris from a 40gb sata drive using three one terabyte drives in a zfs pool.  I thought I was going to change over to freenas when I decided to add a fourth tb disk, as zfs doesn't support expanding a zraid.  Well, I wasn't real happy with freenas as the raid kept breaking, disks dissappearing and such.

Now, I decided to go back to Ubuntu (8.10 desktop, x64) which I was running prior to solaris.  I fdisk'd all four of the tb disks.  Only ONE shows a partition.  This one happens to be one of the original three.  If memory serves, the other two originals say "this disk contains GPT bla bla bla please use parted".  I had no problems creating the partions, however only the first one (sda1) shows up.  The other disks (sdb sdc sdd and the system disk sde, with it's partitions) all show up, just no partitions.  No matter what I do.  I used gparted to create new partition tables on ALL FOUR disks, still, only showing sda sda1 sdb sdc sdd ... 

Any ideas??  The disks physically seem solid, have been running for a few months no issues, smart shows good.

---

### Post by bc90021 on 2009-01-07
I'm not an expert, so take this with a grain of salt, but it seems like the OS may be seeing some kind of RAID container and so is not allowing you access to the individual disks.

I'm not sure what you'd have to do to get around that, but it at least seems where I would start.

---

### Post by fjgaude on 2009-01-07
Well, the zfs is still hanging onto your disks. I don't think **GParted**, **parted**, handles zfs but I could be wrong. It certainly doesn't any other software raid like **md** and **mdadm**.

GPT is created using GParted but I've never used it, always DOS.

You could simply start over and install the filesystem again on each disk? Not knowing how this is done with zfs I'm no help.

---

