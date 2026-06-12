---
title: "Mounting an Ext3 drive"
date: 2005-05-26
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-26
Hi all.
I have had my windows NFTS partitions mounted sweet as.
But now I have a partition 10gigs in size thats ext3.
How do I mount it? I remember with Mandrake I just clicked on it and clicked mount.
I'm unsure of the commands to add to the fstab file.
How can i find which Hd is my 10 ext3 one?

---

### Post by MrTom on 2005-05-26
Follow this guide

[http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions](http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions) 

to discover which partition you want to mount, but when you get to step 4 the fstab line should be

Then add the line to your fstab
/dev/hdaN   /mountpoint    ext3    defaults  0   0

where N is the number of the partition, and /mountpoint is the directory where you want the volume mounted, eg /mnt/storage

The partition should now be 'mountable'

--MrTom

---

