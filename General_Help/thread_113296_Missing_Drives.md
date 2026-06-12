---
title: "Missing Drives"
date: 2006-01-06
forum: General Help
---

### Post by fine_young_misanthrope on 2006-01-06
I have several partitions in my computer (9 including the swap on two drive), but i only see 6 drives including the swap.  Ive tried to alter the /etc/fstab file, but have not seen any changes.  Any advice on how to see the other drives on my desk top?  I really don't need to see the swap on the desktop.

---

### Post by hw-tph on 2006-01-06
If you see a swap partition on your desktop you're not using it as a swap partition and trying to mount a swap partition is...well...not very fruitful, unless you're doing advanced crash recovery.

First off, browse through the dmesg output (try **dmesg | less**) and see if the partitions are detected. If they are, mount them manually and when you got the mount options working correctly, add new lines for your added partitions in /etc/fstab.


H&#229;kan

---

### Post by fine_young_misanthrope on 2006-01-06
Thank you I was able to get find what was wrong and fix it.  Thanks for the heads up on finding all my drives.

---

