---
title: "Where is SWAP?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by fresco on 2005-08-08
My system just had a strange freeze for approx. 20 secs and after I opened System Monitor I've noticed that there was'n any swap space available, only RAM. System somehow turned it off. Now big programs run much slower. I hadn't applied any changes to /etc/fstab before that.

Here's my fstab line:
/dev/hda7       none            swap    sw              0       0

when I try to *mount /dev/hda7* , it gives me the following: "mount: mount point none does not exist".

How to fix this thing?

Thanks!


Edit:

$ sudo swapon -a
swapon: cannot stat /dev/hda7: No such file or directory
Ok, there's no /dev/hda7, but it should be...

Edit2:

Fixed it!

$ dmesg | tail
Out of Memory: Killed process 9905 (nautilus).
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda5.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda5.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda5.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda5.

Something was wrong with my FAT partition so it had dissappeared. Man, what a mess! :)))

I chanded hda7 to hda5 in fstab and ran

$mount -a
$swapon


Thanks for advice!

---

### Post by MrCheese on 2005-08-08
[QUOTE=fresco]My system just had a strange freeze for approx. 20 secs and after I opened System Monitor I've noticed that there was'n any swap space available, only RAM. System somehow turned it off. Now big programs run much slower. I hadn't applied any changes to /etc/fstab before that.

Here's my fstab line:
/dev/hda7       none            swap    sw              0       0

when I try to *mount /dev/hda7* , it gives me the following: "mount: mount point none does not exist".

How to fix this thing?

Thanks![/QUOTE]

Swap is not meant to be mountable - it's a special-format partition where virtual memory chunks are stored temporarily when swapped out of physical ram. Therefore mount point "none" is correct. Try reactivating swap with command "swapon" if you really thinkit's been accidentally turned off.

---

