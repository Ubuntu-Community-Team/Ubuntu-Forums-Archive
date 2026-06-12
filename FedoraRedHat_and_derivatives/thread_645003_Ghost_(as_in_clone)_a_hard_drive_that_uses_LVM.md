---
title: "Ghost (as in clone) a hard drive that uses LVM???"
date: 2007-12-19
forum: Fedora/RedHat and derivatives
---

### Post by thatswhatshesaid on 2007-12-19
I have a server that has Redhat 4 installed with a /boot partition and an LVM partition.  Symantec/Norton Ghost seems to mess up the LVM partition when I put the image on a different machine.

I have tried using Ghost 4 Unix but it won't detect the drives (SAS drives).

I have tried Clonezilla but it won't detect the NICs, two Broadcom NetXtreme IIs.

I need to back up this server so I can use it for another project (with Windows) , but I also need to be able to restore the server after the Windows project is done.

The server is a Dell PowerEdge 1950 with dual quad-core 2.33 GHz processors and 4 GB RAM.  It has two 250GB SAS drives configured as raid 0.  The broadcom NICs are driving me crazy.

Any one have any ideas? or other tools?

---

### Post by jinx099 on 2007-12-20
I don't have much experience with dd, but it may be just what you're looking for.  Something to the effect of:
```
dd if=/dev/sda of=/dev/sdb
```
Where sda is the drive you want to back up and sdb is the drive you want to copy to.  FOR YOUR OWN SAKE, BE CAREFUL WITH THIS COMMAND!  Hopefully someone with more experience with dd will comment here.

---

