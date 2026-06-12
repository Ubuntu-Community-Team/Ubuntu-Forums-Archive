---
title: "[SOLVED] Removing a disk from &amp;quot;Removable Media&amp;quot;"
date: 2008-07-16
forum: Desktop Environments
---

### Post by haegl on 2008-07-16
Hello,

Is there a way to tell gnome not to show some disks in Places->Removable Media & desktop? The reason is that /dev/sdc1 and /dev/sdd1 are part of a NTFS stripped volume (/dev/mapped/chaos) that is already mounted.

thnx in advance

---

### Post by haegl on 2008-07-16
Solved by adding a dummy entries in fstab

```
# /dev/sdc1
UUID=FA94FE6A94FE28B1   none                    ignore
# /dev/sdd1
UUID=7E1C6E9C1C6E4EE9   none                    ignore
```

---

