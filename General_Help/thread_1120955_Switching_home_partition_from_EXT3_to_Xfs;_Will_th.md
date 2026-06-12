---
title: "Switching home partition from EXT3 to Xfs; Will this work?"
date: 2009-04-09
forum: General Help
---

### Post by SoCalChris on 2009-04-09
A while ago I reinstalled my OS, and formatted my home partition as EXT3. I'm fairly unhappy with the performance that I'm seeing with this file system (Compared to the way XFS was working for me), and want to switch back. Will this upgrade plan work?

This is being done on a remote computer, that I'm connected to via SSH. 

1. Back up the home partition to an external drive using rsync
2. Unmount the home partition
3. Reformat the home partition as XFS
4. Mount the home partition
5. Copy everything back from the external drive

Can I do this while I'm logged in? Will not having a home directory mounted cause any problems while I'm formatting the partition? I shouldn't need to change anything in my fstab file, correct?

Thanks

---

### Post by SoCalChris on 2009-04-09
I see that I can't unmount the home partition while I'm logged in. I'll have to convert it while booted from a Live CD I guess.

---

