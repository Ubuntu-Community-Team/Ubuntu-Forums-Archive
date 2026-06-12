---
title: "Question about creating a partition table on internal HD"
date: 2009-02-11
forum: General Help
---

### Post by utherpendragonfly on 2009-02-11
I have a second internal hd that now has Linux Mint installed (Other hd has Intrepid).
I really don't use Mint on this machine and would like to use sdb as media storage and for backup. I'd like to make two partitions for this.
When I open Gparted and go to Create Partition Table, the default choice is MSDOS.
Is this what I should select? or one of other options. I'm not too familiar with the choices. And I just want to make sure it will mount properly.
Thanks.

---

### Post by caljohnsmith on 2009-02-11
> **utherpendragonfly said:**
> 
When I open Gparted and go to Create Partition Table, the default choice is MSDOS.
Is this what I should select? 
Yes. :)

---

### Post by NT4usB on 2009-02-11
I've wondered about this every time I do a fresh drive. Much googling didn't provide any insight.
Resigned to use msdos and after a dozen or so disks, seems to work fine.
I did find using a disk label or name works way cool for external drives.
They automount using the name instead of the generic /media/disk...

---

### Post by utherpendragonfly on 2009-02-12
Thank you.

---

### Post by dcstar on 2009-02-12
> **utherpendragonfly said:**
> I have a second internal hd that now has Linux Mint installed (Other hd has Intrepid).
I really don't use Mint on this machine and would like to use sdb as media storage and for backup. I'd like to make two partitions for this.
When I open Gparted and go to Create Partition Table, the default choice is MSDOS.
Is this what I should select? or one of other options. I'm not too familiar with the choices. And I just want to make sure it will mount properly.
Thanks.

Creating MSDOS partitions will limit you to 2GB maximum file sizes as well as other issues as not being able to preserve various attributes and possible filesystem corruption - it is basically the **worst** choice you can make.

If it is a drive that is in a Linux system, then format it with a Linux filesystem like EXT3 so you get all the benefits of a Linux filesystem.

---

### Post by caljohnsmith on 2009-02-12
> **dcstar said:**
> Creating MSDOS partitions will limit you to 2GB maximum file sizes as well as other issues as not being able to preserve various attributes and possible filesystem corruption - it is basically the **worst** choice you can make.

If it is a drive that is in a Linux system, then format it with a Linux filesystem like EXT3 so you get all the benefits of a Linux filesystem.
I think you misread his post; he asked about creating an MS-DOS **partition table**, not file system (FAT/FAT32) for a single partition.

---

### Post by jerome1232 on 2009-02-12
---edited--- caljohnsmith already posted

---

### Post by dcstar on 2009-02-12
> **caljohnsmith said:**
> I think you misread his post; he asked about creating an MS-DOS **partition table**, not file system (FAT/FAT32) for a single partition.

I thought of that, but I couldn't find in my Gparted where there are actually any partition table options (and have never seen anything like this in in Gparted) so I assume it is may be a confused description.

---

### Post by caljohnsmith on 2009-02-12
> **dcstar said:**
> I thought of that, but I couldn't find in my Gparted where there are actually any partition table options (and have never seen anything like this in in Gparted) so I assume it is may be a confused description.
I'm using gparted 0.3.8, and it's found under the "Device" menu > "Create Partition Table." Is yours different?

---

### Post by dcstar on 2009-02-12
> **caljohnsmith said:**
> I'm using gparted 0.3.8, and it's found under the "Device" menu > "Create Partition Table." Is yours different?

0.3.5 does not have that (just "Set Disklabel").

I apologise to the OP for wasting his time (though I can't understand why you would want to create a partition table on an already working drive with existing partitions.......)

---

