---
title: "Manage hard drive partitions in KDE4.1"
date: 2008-08-26
forum: Desktop Environments
---

### Post by jonathanku on 2008-08-26
I've just installed KDE4.1 (on an UbuntuStudio 8.04 installation).

I'm liking it so far. However - I am struggling to find out how to manage hard-drives. In KDE3 I would just go to system settings and hit the advanced tab I think... but I can't find this in KDE4.

I have a bunch of files backed up on the other partition, which I can't seem to access.

Any thoughts?

---

### Post by cmittle on 2008-08-26
In a terminal type sudo fdisk -l.  This will output all of the drives and partitions on them that are active in your setup.  Locate the particular disk and partition your want to mount, it should look something like /dev/sda2.  

If the empty directory for where you want to mount these is already created great, if not create them.  Then it's as simple as sudo mount /dev/sda3(this is the disk you want to mount) /path/to/mnt/location.

If you add these to /etc/fstab this will be even easier next time.

---

