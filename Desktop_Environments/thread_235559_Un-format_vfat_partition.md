---
title: "Un-format vfat partition"
date: 2006-08-13
forum: Desktop Environments
---

### Post by el3ktro on 2006-08-13
Damn, wat the hell. I wanted to change the volume label of a FAT32 partition and did mkfs.vat -n Name /dev/hda2, which did not only set the volume label, but also quick-formatted the harddisk. Is there any chance to und this? No data has been written on this harddrive so far, the only thing done was a quick-format. Is there some kind of backup copy of the FAT and can it be restored? Damn I really need your help guys!!

Tom

---

### Post by jordilin on 2006-08-13
> **el3ktro said:**
> Damn, wat the hell. I wanted to change the volume label of a FAT32 partition and did mkfs.vat -n Name /dev/hda2, which did not only set the volume label, but also quick-formatted the harddisk. Is there any chance to und this? No data has been written on this harddrive so far, the only thing done was a quick-format. Is there some kind of backup copy of the FAT and can it be restored? Damn I really need your help guys!!

Tom

I'm afraid you will not be able to undo this. When you format a disk you lose all data.

---

### Post by oghanchi on 2006-08-13
Try testdisk. It recently worked for me when I had lost my partitions because of a corrupt partition table. Testdisk will scan the drive and can restore previous partitions for you. But BE CAREFUL, read all documentation and how-to's before trying this or any other recovery utility because you may end up doing more harm than good. 

Good luck.

---

