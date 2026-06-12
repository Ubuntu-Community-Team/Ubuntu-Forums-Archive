---
title: "New to Linux, needing some help"
date: 2008-12-07
forum: General Help
---

### Post by paintedbull on 2008-12-07
i just made the switch to linux, but might have been unsuccessful. my old hard drive was windows and got corrupted, so i wanted linux on a new harddrive so i could pull files off the old one.

i had a 500 gigabyte harddrive, and installed windows first so i could dual boot. I thought i gave it only 15 gigabytes. i then installed Ubuntu fine and have been running it for about a day.
i hooked up my old hard drive to transfer data. i started pulling off songs and putting them in my music folder on ubuntu.
apparently i only have about 15 gigs of storage on linux...
i ran partition program and i see that i have 450 gbs of NTFS space, 436MB of it is free space.

i dont know what drive ubuntu is on.

how do i access all this other space? is NTFS the wrong format?

what do i do? i really don't want to reinstall all of this again

also, i'm not sure if it was a problem that i installed ubuntu using WuBi instead of a boot disk, because WuBi is based in windows...please let me know

any help would be greatly appreciated! i thought i was somewhat computer savvy until I started with linux hahaha

thanks guys

---

### Post by Nathan Sweeney on 2008-12-07
So, you installed Windows on a 15 GB partition and then used Wubi to install Ubuntu on that partition as well?

How much space do you want Ubuntu to have?  If I understand the way Wubi works, it is using the same partition as the Windows install, so since the Windows partition is 15 GB that means that Ubuntu would also be 15 GB.

I'd install Ubuntu on it's own dedicated partition from the Live CD, say use 15 GB, then with Windows on 15 GB and Linux on 15 GB, you can have the rest as a large storage partition to keep music, files, etc.

---

### Post by paintedbull on 2008-12-07
yeah i've got no idea where i even installed linux too, i had just assumed it installed onto the other unallocated partition...

what format does a drive need to be for a ubuntu?

---

### Post by bp1509 on 2008-12-07
d

---

### Post by paintedbull on 2008-12-07
how do i "unpartition" my 450-some gbs of ntfs?

---

### Post by paintedbull on 2008-12-07
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d349d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959       60800   472648365    f  W95 Ext'd (LBA)
/dev/sda5            1959       60800   472648333+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17752   134205088+   7  HPFS/NTFS

```

---

### Post by acalafra on 2008-12-07
You need to boot back up with the live cd and us the "partition manager" i think thats what intrepid calls gparted. This should allow you to resize the current partition to 15GB and then restart and install ubuntu in the space thats left over. i.e guided but not guided use whole disk

The wubi is what caused your problem. You need to do a regular install to truly dual boot...follow one of the good guides [Heres one]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

also unplug the old windows drive to avoid mistakes until you are ready to get your data off of it

---

