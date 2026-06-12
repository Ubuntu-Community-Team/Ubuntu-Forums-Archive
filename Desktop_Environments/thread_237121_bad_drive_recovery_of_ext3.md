---
title: "bad drive? recovery of ext3?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by relux on 2006-08-15
I am having an issue with a drive of mine. It is confusing the heck out of me. It's a 120 gig seagate ide hard drive. It was my primary drive which had a root and a swap partition. I replaced it because when my computer would startup it would just power cycle over and over. The bios read it fine and all the hard drive diagnostic tests including those from manufacturer said the drive was fine.

I am trying to find a way to recover data from it. Any help would be appreciated. Here is what the situation is.

- It's a ext3 partition
- Bios sees it.
- Fdisk sees it and the partitions.
- testdisk sees it and the partitions. I can also go through and see the file names on it. Of course, you can't recover with testdisk as far as i know.
- fsck /dev/hdb1 comes back with "Warning... fsck.ext3 for device /dev/hdb1 exited with signal 8."
- tune2fs /dev/hdb1 -l comes back with nothing that I can tell is out of the ordinary.
- When trying to mount the partition mount just hangs.

Any ideas here how to recover data off this drive? I can't see any visible errors... Any help or things I can try is greatly appreciated!

Regards

---

### Post by matspekkie on 2006-08-15
you can boot from the ubuntu cd an "live" session and run an fsck on the drive although i think it might be an grub "bootmanager" related problem witch can be solved with an grub-install. if not sure how to do those things reading man pages might help.

---

### Post by relux on 2006-08-15
> **matspekkie said:**
> you can boot from the ubuntu cd an "live" session and run an fsck on the drive although i think it might be an grub "bootmanager" related problem witch can be solved with an grub-install. if not sure how to do those things reading man pages might help.
eek double posted

---

### Post by relux on 2006-08-15
> **matspekkie said:**
> you can boot from the ubuntu cd an "live" session and run an fsck on the drive although i think it might be an grub "bootmanager" related problem witch can be solved with an grub-install. if not sure how to do those things reading man pages might help.
Well, I have since put a new drive in. I am unable to run fsck on it. I posted the error above. I am also unable to mount it which is why I find it so strange. If not specifying -t ext3 mount seg faults. If I do specify it it just hangs.

---

