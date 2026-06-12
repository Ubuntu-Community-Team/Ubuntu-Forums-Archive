---
title: "Permission Troubles"
date: 2009-04-19
forum: General Help
---

### Post by johnmarkbuchanan on 2009-04-19
I accidentally installed ubuntu on my 16 gig flash drive and now I am having trouble formatting the drive in unbuntu because it says that I do not have permission.
" mkfs -T vfat /dev/sdc5 
mke2fs 1.41.3 (12-Oct-2008)
mkfs.ext2: Permission denied while trying to determine filesystem size
john@john-desktop:~$ "

Any thoughts on how to get around this?

---

### Post by justin_guerin on 2009-04-19
You need to be root to work directly with the device node.  So run the command in sudo mode.

---

