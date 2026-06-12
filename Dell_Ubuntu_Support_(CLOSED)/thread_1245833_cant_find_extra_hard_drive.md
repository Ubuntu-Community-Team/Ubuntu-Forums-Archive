---
title: "cant find extra hard drive"
date: 2009-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hello2007 on 2009-08-21
i just installed a harddrive onto my computer and cant locate it anywhere it doesnt display. I formatted it to ntf or something like that from a cd called bootit. But it still doesnt appear anywhere

---

### Post by doas777 on 2009-08-21
> **hello2007 said:**
> i just installed a harddrive onto my computer and cant locate it anywhere it doesnt display. I formatted it to ntf or something like that from a cd called bootit. But it still doesnt appear anywhere

open a terminal (applications -> accessories) and paste in:
```
sudo fdisk -l
``` and post what it prints out.

---

### Post by hello2007 on 2009-08-21
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by howefield on 2009-08-21
Copy/Paste the command into terminal from doas777s` post, you may have mistyped it.

---

### Post by hello2007 on 2009-08-21
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1965    15728640    7  HPFS/NTFS
/dev/sda3   *        1965       60476   469989400    7  HPFS/NTFS
/dev/sda4           60477       60801     2610562+   5  Extended
/dev/sda5           60477       60779     2433816   83  Linux
/dev/sda6           60780       60801      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS




the hard drive i installed is 1tb seagate if that matters

---

### Post by howefield on 2009-08-21
Try installing ntfs-3g and ntfs-config, both with synaptic package manager.

ntfsprogs is also useful.

---

### Post by hello2007 on 2009-08-21
how do i do that?

---

### Post by doas777 on 2009-08-21
**go to System -> Administration, and open up "Synaptic Package Manager"** or "synaptic". it is a gui program that allows you to add or remove software on your machine.

once synaptic is up, **search for the packages**
ntfs-3g
ntfs-config
ntfsprogs

**Right click on each of them and select "Mark for Installation"**. once they are all highlighted, **click the "Apply" button at the top**. 

after all that, you will have the tools needed to mount ntfs volumes.
[B]
Reboot.[/B] 

your fdisk output shows that ubuntu sees the drive.
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
```

shows a 1TB NTFS volume, so your good there. 
now you just need to mount it. 

open up Places -> Computer
do you see your drive there now?

if not, we can try to mount it manually.
you need to decide on an internal name for the disk. I'm using "disk1" in this example.
```

sudo mkdir /media/disk1
sudo mount /dev/sdb1 /media/disk1 ntfs3g defaults

```

thats all there should be to it. if the drive will always be available to the system, you can add it to the /etc/fstab file so it mounts at boot: 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
(this site has a great deal of good info. check it out)

have fun

---

