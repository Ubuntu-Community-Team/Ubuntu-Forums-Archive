---
title: "GParted &amp; USB Drive"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jimmymac on 2006-08-14
Alright guys,

I thought I'd use GParted to resize my external USB NTFS partition and create an ext3 partition, copy the data over and extend the ext3.

GParted sees the drive no problem, I unmounted the drive and thought let's get another stage of the anti-windows program done!

However GParted won't resize the partition.  There is an exclamation mark next to the partition.  When I open up the information panel it says:

Unable to read the contents of the filesystem!
Because of this some of the operations may be unavailable.
Did you install the correct plugin for this system?

Any ideas?

TIA

Jimmy

---

### Post by reacocard on 2006-08-14
do you have ntfs-progs installed? gparted needs it to handle ntfs.

---

### Post by jimmymac on 2006-08-14
No I didn't!

I installed it, which enable GParted to actually see the partition correctly.  So I deleted the FAT32 partition and tried to resize the NTFS one.
However when I resize the NTFS partition it appears to work then just goes back to it's old size unaffected.

Any ideas on that one?

TIA

Jimmy

---

### Post by reacocard on 2006-08-14
i've noticed problems with resizing ntfs before. what i'd do is just delete that ntfs partition and make a new one of the size you want. that's probably the easiest thing to do.

---

### Post by jimmymac on 2006-08-14
Would love to do that!  Problem being is there's 120Gb data on there that I haven't got anywhere else to put!
But yes agreed it is the easiest and probably the best option!

Any other ideas please?

TIA

Jimmy

---

### Post by reacocard on 2006-08-14
find someone with space to put the data?

you could try defragmenting the disk. you'll have to use windows to do that though, since linux can't. also, use scandisk to check the disk for errors, both before and after defragging.

---

### Post by asplode on 2006-08-14
Scandisk doesn't come with XP, you need to run this in the command prompt.

```
chkdsk /f
```
And it will say it cannot do it because its mounted (active handles or whatever the hell msft calls it), do you want to check after restart, say yes, and then reboot.

---

### Post by reacocard on 2006-08-14
I didn't mean scandisk specifically. just the disk checking utility XP has. right-click the drive, choose properties, tools, disk check. defrag is in the same spot.

---

