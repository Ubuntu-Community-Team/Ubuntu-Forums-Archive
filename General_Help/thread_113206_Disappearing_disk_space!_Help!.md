---
title: "Disappearing disk space! Help!"
date: 2006-01-05
forum: General Help
---

### Post by quonsar on 2006-01-05
ok, i had a lot of unused space on an NTFS partition. i shrank the partition and formatted the unallocated space ext3. this left me with:

hda1 ext3 12967mb, 0 used, 12967 free
hda2 ntfs   6111mb, 5350 used, 761 free
hda3 linux-swap 478 mb
hda4 ext3 18575mb, 13512 used, 5063 free

hda4 is my root filesystem for ubuntu.

i had about 10 gigs of data (mostly mp3's) under /home/quonsar/documents which i then copied to the new partition, which i had mounted as /media/hda1.

once it was all safely copied over, i deleted the entire /home/quonsar/documents directory and emptied the trash. then i edited /etc/fstab so it would mount the new partition at /home/quonsar/documents and then i rebooted.

all seems well, i can access the new partition and all my data at /home/quonsar/documents, and the documents directory is on its own partition. the problem is, i do not seem to have gained my 10 gigs back from the root filesystem!

the partition table now looks like this:

hda1 ext3 12967mb, 10165 used, 2802 free
hda2 ntfs   6111mb, 5350 used, 761 free
hda3 linux-swap 478 mb
hda4 ext3 18575mb, 13512 used, 5063 free

where did my 10 gigs go? i did a du -h -x on the root filesystem and it shows only 3.1Gb used out of 18+ gigs, but the partition table indicates 13+ gigs in use and nautilus reports only 4.9 gigs free space!

how did i screw this up? how can i regain the space? anyone?

---

