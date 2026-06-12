---
title: "Possible to undo mkfs.hfsplus?"
date: 2009-04-11
forum: General Help
---

### Post by eddyjackson on 2009-04-11
I accidentally did a sudo mkfs.hfsplus on the wrong device (should have triple checked, I know). The action only lasted a second and resulted in a 
"Initialized /dev/sdk as a 1397 GB HFS Plus volume"
so I'm hoping its just flagged the partition and its still possible to recover the files somehow. If not, it's not the end of the world but it would save me more than a few headaches. The drive was previously an ext3 drive. 

Anyone have any ideas of what possible steps I should take?
Thanks for any help.

---

### Post by tgalati4 on 2009-04-11
Check the partition table with cfdisk.  Make a new table with partitions as you remember them.  Reboot, or  simply try to mount the drive.  Use testdisk to recover the partitions.  Use photorec to recover files.

---

