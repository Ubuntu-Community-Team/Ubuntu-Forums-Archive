---
title: "Disk space for updates"
date: 2009-06-08
forum: General Help
---

### Post by arstart on 2009-06-08
How do I add space for my Ubuntu disk?  The update manager needs 70.1 m free on disk.  G-parted shows /dev/hda1 as fat 32 HP recovery, /dev/hda2 ntfs hp pavilion, /dev/hda3 extended 2/49 gib, /dev/hda5 ext 3 2.33 gib, /dev/hda6 linux-swap 44.27 mib, /dev/hda7 ext2 73.80 mib, /dev/hda8 ext 2 51.65 mib.  Is there some way to move some space from someplace else to where it needs to be and where does it need to be :confused:Thanks in advance.

---

### Post by zvacet on 2009-06-08
Applications>accessories>terminal and type

```
sudo fdisk -l
```

Post output here.

---

