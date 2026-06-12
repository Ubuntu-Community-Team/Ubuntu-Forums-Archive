---
title: "XP cant read my FAT32 partition"
date: 2005-12-08
forum: General Help
---

### Post by Daminator on 2005-12-08
I'm dual booting and have these partitions ..

hda1 - NTFS, 10 Gig
hda2 - NTFS, 3.5 Gig
hda3 - ext3, 10 Gig
hda4 - extended
-hda5 - linux-swap, 2 Gig
-hda5 - fat32, 50 gig

Any ideas???

If I go to 'Computer management>Disk Management' in XP, then it knows that the drive is there in the extended partition, and it looks like it knows that it's fat32, but I can't give it a drive letter or access it in any way.

---

### Post by tomwell on 2005-12-08
Daminator,

I had that same problem... There are threads that i started and that were solved plus other threads started by other people that have been solved...

I think to solve your problem you need to boot into windows, and format your partition as fat32 through windows... Since you are dual booting that shouldn't be a problem...

Let us know how you get on...

Peace

Tom

---

### Post by Bachstelze on 2005-12-08
Something disturbs me here... How can you hae two /dev/hda5 partitions ?

---

### Post by aerials on 2005-12-08
I had such a problem with a FAT32 partition on a usb drive which I created under linux. Gparted did not set a LBA flag for the partition and so it was inaccessibe in windows.
I then set the LBA flag using parted instead of gparted an was now able to see my partition in windows.

---

### Post by Daminator on 2005-12-08
[QUOTE=HymnToLife]Something disturbs me here... How can you hae two /dev/hda5 partitions ?[/QUOTE]

**HymnToLife**,
D'oh!
My mistake, the last one's hda6


Thanks for the other responses .. I'll try them out.

**aerials**,
How can I use Parted to set LBA flag? (I'm new to Linux, but not to computers, so I'm not scared of a command line)

---

### Post by tomwell on 2005-12-08
Do try it out it should work on your machine too it did on other machines....

Peace

Tom

---

