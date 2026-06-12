---
title: "Move Linux Boot Partition"
date: 2006-09-18
forum: Desktop Environments
---

### Post by rpalkovic on 2006-09-18
First off, I'm still reasonably new to Linux and Ubuntu.  I've been able to google everything else I needed, but I couldn't find anything remotely close to what I'm looking for on google, and attempting to figure it out on my own left me face down in the mud.  On the bright side, I havn't lost any data yet.

Anyhow, the hard drive I now have Ubuntu installed on WAS a dual boot drive to Windows XP.  As such, Ubuntu was installed on /dev/hda6 and the swap partition on /dev/hda7, because windows was taking up /dev/hda1-5.

Now, I've completly given WinXP ye 'ol heave ho, but I'm stuck in this strange predicament where my Ubunto boot partition is only 10 gigs and can't be extended because the other partitions can't be deleted because /dev/hda6 and /dev/hda7 are mounted.

I tried making the changes while booted from a Live CD, but I didn't seem to have any control over the partitions of the hard drives.

Here's what GParted says about /dev/hda:
unallocated     unallocated     15.93 GB         ---        ---     
/dev/hda2       extended        58.59 GB         ---        ---   lba
   /dev/hda5    ext3            48.83 GB   913.47 MB   47.94 GB
   /dev/hda6    ext3             8.79 GB     3.60 GB    5.19 GB
   /dev/hda7    linux-swap       1004.04         ---        ---

/dev/hda6 is my boot partition.

What I want to do is get /dev/hda6 to the front of the partition table, delete everything else, and extend it to the full size of the disk.

I'm stumped.  Help :)

---

### Post by BoneKracker on 2006-09-19
in LiveCD console...

```
sudo parted /dev/hda
help move
```

---

