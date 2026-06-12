---
title: "system crash caused loss of vfat partition"
date: 2009-05-29
forum: General Help
---

### Post by maestrobwh1 on 2009-05-29
K9copy went nuts recently, made /home/user~/.xsession-errors into a 2.3 GB file and crashed my system.  A mounted vfat partition now shows under gparted as unknown as any kind of file type.  I am not particularly fond of vfat really, so I am not surprised, but I need it for a few things.  

I tried partition recovery, but it seems not to help because the partition was not removed, and I am thinking there is a huge chance the data is there if I could find a utility (free as the data there isn't of vital nature) that could relabel the partition as vfat without overwriting it.  I am using DiskDigger in windows, but it works for only some file types (and it works VERY well), but I would like to try to recover the whole thing.  I looked at parted and fdisk, but those seemed to want to create a new file system.  

Windows XP lists it but as an unformatted disk partition.

Ideas anyone?

---

### Post by quixote on 2009-05-30
Have you tried testdisk?  I think you need the universe repository enabled, then you can install through synaptic.  There's a step-by-step here: [http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk) .  Search for "testdisk tutorial" (without quotes) for lots of other how-tos.  Also, eg: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

