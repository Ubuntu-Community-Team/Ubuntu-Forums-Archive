---
title: "[SOLVED] Linux RAID"
date: 2007-07-14
forum: Desktop Environments
---

### Post by fjgaude on 2007-07-14
I've been testing software raid using mdadm, a fine program. Going through various configuratons of two to four 300 GB disks, then testing for throughput.

I've run into a situation where I can't create any more sets using the same array of disks. Question: Is there a way to remove the /sys/block entries that mdadm creates with the /mdx names?

I have reformatted the disks, etc., but mdadm ends up indicating devices are busy.

Thanks for any help.

frank

---

### Post by fjgaude on 2007-07-14
Okay, I found the answer:

sudo mdadm -S /dev/md32

Such command deactivates the raid set. Done deal! -S or --stop deactivates array, releasing all resources.

Maybe this helps others who are into software RAID until Ubuntu.

frank

---

