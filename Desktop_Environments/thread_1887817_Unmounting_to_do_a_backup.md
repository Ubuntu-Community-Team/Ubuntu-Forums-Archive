---
title: "Unmounting to do a backup"
date: 2011-11-27
forum: Desktop Environments
---

### Post by mscdc on 2011-11-27
Partimage demands that i should unmount my Ubuntu drive to make a backup image. 
But how can this be done when I'm running Partimage from Ubuntu?










eee PC R051PX 
N570 dualcore, 2 GB RAM. dual boot-Ubuntu 11.10/Win 7 Ultimate

---

### Post by bluexrider on 2011-11-27
PartImage does not support Ext4 partitions, and Ubuntu defaults to the Ext4 filesystem format. I'm told [PartClone]("http://partclone.org/") (which does support Ext4) is a good alternative. You might also want to look into [CloneZilla]("http://clonezilla.org/").

---

### Post by vangop on 2011-11-28
Do you have a single partition for the system, or several separate ones (/home, /boot etc)
If it's a single one, you might need to go single user mode or boot from external liveCD to do a backup.
If it's separate ones, you have much more options.

---

### Post by Bobhuber on 2011-11-28
fsarchiver will backup a mounted partition with no problems at all.

---

