---
title: "Please explain to me"
date: 2006-02-18
forum: Desktop Environments
---

### Post by alinutzu15 on 2006-02-18
hi.
today i've installed for the first time ubuntu on my pc. And now i want to know how do i make permissions to users so that they can read&write&execute files from a partition.


Regards.


PS: i'm a Linux newbie so explain me step by step

---

### Post by rfruth on 2006-02-18
If ya want to use the GUI Nautilus 2.12.1 will change permissions ;)

---

### Post by nalmeth on 2006-02-18
sorry, can you explain your situation with some more details? Do you want to write to other partitions than ubuntu's? If your windows partition is ntfs you will not be able to write to it, period.

---

### Post by alinutzu15 on 2006-02-18
nop. i just want to change permisions to my ext3 partition.
btw, how can i acces windows partitions?? i mean where are them ?? I'm unable to find them  :confused:

---

### Post by cilynx on 2006-02-18
I'm making some assumptions here:

You have a machine with a new ext3 partition with Ubuntu on it.
You have an old windows (fat, vfat, or ntfs) partition as well.

-------------------------------

I'm not really sure what you mean by "change to users to read, write, execute from a partition".  If you're talking about (one of) the main partition(s), then you really shouldn't mess with the way that permissions are set up.  You probably want to research 'chmod'.  If you're talking about mounting an auxillary ext3 partition (for backups or data storage or whatever) then generally the user that mounted it has the most access to it and pretty much everyone else is blocked.  Again, look into 'chmod' for altering file permissions.

As for accessing Windows partitions, mine are automatically mounted in the /media/ directory.  Look into 'mount', 'umount' (that's not a typo), and 'fstab'.

Good Luck

---

