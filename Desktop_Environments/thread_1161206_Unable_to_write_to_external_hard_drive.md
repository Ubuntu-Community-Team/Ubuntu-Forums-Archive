---
title: "Unable to write to external hard drive"
date: 2009-05-16
forum: Desktop Environments
---

### Post by smirnoff76 on 2009-05-16
Hey all, 

I have an external hard disk I am trying to write to but am unable to do so. The partition is FAT32 and is a 500Gb capacity with around 300Gb free space so deleting the partition and re-creating isn't an option here as you can imagine. 

I am pretty certain this is a permissions issue and am wondering if anyone can tell me how to reset the permissions on the disk. 

Thanks!

---

### Post by Villiam on 2009-05-16
The hard drive will presumably show up on
sudo fdisk-l

as /dev/hdb or something similar. What you need to do is simply chown the partition when it is mounted in /media/hdb or whatever it is. You do this with

sudo chown -R user:group /media/hdb

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by smirnoff76 on 2009-05-17
in gparted the hard drive shows up as sdf so from what I can see the command should be:

sudo chown -R smirnoff:group /media/sdf 

but when I run this command i get 
chown: invalid group: `smirnoff:group'

Presumably I should be specifiying a specific group in the chown command, is this right? if so what group? 

Thanks

---

