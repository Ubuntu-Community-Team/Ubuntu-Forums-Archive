---
title: "My other post was wrong"
date: 2009-03-02
forum: General Help
---

### Post by MountainX on 2009-03-02
This error magically persists across repartitioning and all other disk changes. 
[CENTER]**"Incorrect metadata area header checksum"**
[/CENTER]
 How do I make it disappear?

I am willing to wipe out all data on the disk. In fact, I have deleted all partitions and started fresh several times, but I still get the error "Incorrect metadata area header checksum" when I run vgscan as soon as any new partition is put on the disk -- even non-LVM partitions.

I suspect using dd to zero out the whole disk might work, but I want a short cut... something faster than waiting a looooooonnnng time for dd to zero a 1.5 TB disk.

Where is this LVM metadata persisted on the disk that enables it to reappear even after deleting all partitions?

(Why I made a new post -- previously, I thought this error had something to do with needing to filter my USB flash drive out of /etc/lvm/lvm.conf but that wasn't it. This error is happening on a Seagate 1.5 TB SATA drive.)

---

### Post by MountainX on 2009-03-04
SOLVED [HERE]("http://www.linuxquestions.org/questions/linux-hardware-18/this-error-magically-persists-across-repartitioning-and-all-other-disk-changes.-708713/"): http://www.linuxquestions.org/questions/linux-hardware-18/this-error-magically-persists-across-repartitioning-and-all-other-disk-changes.-708713/

---

### Post by MountainX on 2009-03-04
For people searching for solutions, I'll reference this thread too:

[B][LVM problem on fresh install withOUT LVM]("http://ubuntuforums.org/showthread.php?t=89503")
[/B]http://ubuntuforums.org/showthread.php?t=89503

and an [old (2006) thread on same topic]("http://www.linuxquestions.org/questions/linux-general-1/lvm-error-incorrect-metadata-area-header-checksum-419978/") with no solution:
http://www.linuxquestions.org/questions/linux-general-1/lvm-error-incorrect-metadata-area-header-checksum-419978/

---

