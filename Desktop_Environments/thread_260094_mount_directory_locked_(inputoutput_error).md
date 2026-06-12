---
title: "mount directory locked (input/output error)"
date: 2006-09-18
forum: Desktop Environments
---

### Post by pataphysician on 2006-09-18
i had a windows share mounted in /mnt/windows. the windows machine crashed but is back online. i've verified that the share is accessable and i can browse it using smbclient and other linux machines on the network.

when i do *ls* in /mnt, i get *ls: windows: Input/output error*. if i do *mount*, i still see the windows share as being mounted. if i try to unmount, i get *umount: /mnt/windows: device is busy*. if i try to remount the share, i get *Could not resolve mount point /mnt/windows*. i googled *umount device is busy*. everything there says to use *fuser* to find out what's using the share. *fuser /mnt/windows* gives */mnt/windows: Input/output error*.

what can i do to get my share re-mounted in /mnt/windows? i'm running from a terminal and have no access to a gui.

---

### Post by kidders on 2006-09-18
Ugh... awkward!

Well, assuming **lsof | grep /mnt/windows** doesn't say anything, you could try remounting read-only  and then unmounting, or using the **-f** (force) switch, or the **-l** (lazy) switch ... perhaps in that order. One of them will most likely work for you, and then you can remount the share as normal.

---

### Post by nikhilk on 2006-09-18
If the solution mentioned by kidders does not work you may try the following.

Is the /mnt/windows partition auto-mounted? If yes comment out that line from /etc/fstab and then boot into recovery mode and see if you can manually mount the partition.

---

### Post by pataphysician on 2006-09-18
thanks guys! using -f to force the unmount worked.

---

