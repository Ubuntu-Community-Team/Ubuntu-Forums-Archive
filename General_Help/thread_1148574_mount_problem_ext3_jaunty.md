---
title: "mount problem ext3 jaunty"
date: 2009-05-04
forum: General Help
---

### Post by timroberts on 2009-05-04
I'm having a problem with my new jaunty install. I screwed up something trying to change where a partition mounts, i tried to use the menu under properties to change where a partition mounts (kept all of the same options as it had already) and now it tells me its unable to mount. Is there some way to clear the mounting options so i can get it to automount again? My fdisk is as follows, i'm trying to mount sda4:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19721971

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       21008    15149295    5  Extended
/dev/sda4           21009      121601   808013272+  83  Linux
/dev/sda5           19123       19185      506016   82  Linux swap / Solaris
/dev/sda6           19186       21008    14643216   83  Linux

On a side note, I think my hard drive (which is only a month old) may be dying on me. If i leave my computer on for a while and i try and run something, it gives me an "i/o error". If i let it do the file system check that it wants to run at startup, it crashes, tells me to run fsck. When i run fsck it then wipes a whole bunch of stuff forcing me to re-install. Any ideas? Is this a hard drive issue? or is it a hardware issue somewhere else?

---

### Post by Bindsa on 2009-05-04
Hard drive issue I think, looks like you have some bad sectors on your drive. Not sure though.

---

### Post by kpoole on 2009-05-05
A failing hard drive is not impossible but there are other things to check as well.  

The delay in onset of trouble may indicate overheating.  Make sure there's adequate airflow around the drive.

If you have the time, you can download the toolkit from the drive manufacturer (ie seatools from seagate) to do a recertification of the drive.

Just noticed, this is a terabyte drive.  Is it a Seagate?  They had some problems with their terabyte drive software.  Youmight check to see if this is in the range of drives (serial number) where they had problems.

---

### Post by timroberts on 2009-05-05
Its a western digital "green" 1 TB drive. Cooling shouldn't be an issue, its a gaming rig i built a few years ago. My old hard drive crashed on me and i replaced it with this one.

I got tired of problems yesterday, so i formatted and went with ext4 on both partitions, and haven't had any problems thus far.

---

### Post by Bindsa on 2009-05-07
I'm glad to hear your problems are gone now.

---

