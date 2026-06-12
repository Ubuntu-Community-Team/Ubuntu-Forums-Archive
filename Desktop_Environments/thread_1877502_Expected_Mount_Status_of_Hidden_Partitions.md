---
title: "Expected Mount Status of Hidden Partitions"
date: 2011-11-08
forum: Desktop Environments
---

### Post by RMOP on 2011-11-08
I used the following fstab entries to hide my W7 System partitions from Ubuntu:

/dev/sda2 /Windows/sda2 ntfs defaults,umask=777 0 0
/dev/sda3 /Windows/sda3 ntfs defaults,umask=777 0 0
/dev/sda1 /Windows/sda1 ntfs defaults,umask=777 0 0

These partitions no longer show up in the "Places" menu or in Nautilus. However, when I open "Disk Utility," ALL partitions are viewable and editable. That doesn't particularly surprise me, as I suppose one should not be expected to hide partitions from a utility which is designed to SEE partitions.

However what IS perplexing is that ALL THREE partitions show to be MOUNTED when viewed within Disk Utility. I even tried UNMOUNTING one, but got an error. Since the whole point of hiding these partitions is to isolate them from Ubuntu, I'm disinclined to try any more operations on these partitions.

But, I'd sure like to know WHY they show to be mounted in Disk Utility. Are all partitions mounted when Disk Utility runs? NO, that's NOT the case. After unmounting my automounted NTFS Data Drive, and then running Disk Utility, the HIDDEN partitions show to be MOUNTED, while the just unmounted one shows to be unmounted.

This strikes me as unexpected behavior, or at least undesired. Apparently I'm managing to MOUNT the very drives I'm HIDING, which is NOT what I intended. On reflection, it seems likely that the fstab entries (copied from a post in the forum about hiding partitions) explicitly MOUNTS these partitions while hiding them from the Desktop.

Any pointers on this, please? I'd like the partitions UNMOUNTED, HIDDEN, and ABSENT from my "Places" menu and from Nautilus.

---

### Post by Morbius1 on 2011-11-08
Add the "noauto" option to your fstab entries so that it won't mount at boot. For example:
```
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
```The way you had it it will mount automatically at boot but it will be unaccessible to everyone - well, everyone but root.

---

### Post by mcduck on 2011-11-08
+1 to above.

The method you are using is not hiding the partitions in any way, or preventing them from being mounted. It's simply mounting the drives in another location that doesn't cause them to appear in the Devices-section of the file manager (/Windows instead of /media). The drives are still mounted and accessible, if you just browse to the correct location (and use sudo since the umask you use removes all permissions).

Add the "noauto" to mount options if you don't want the drives to actually get mounted.

---

### Post by RMOP on 2011-11-08
McDuck & Morbius1 - thanks to you both. It's obvious in retrospect, but all I guessed was that I was unintentionally auto-mounting the partitions. The noauto didn't cross my mind.

---

