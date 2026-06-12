---
title: "fat problem"
date: 2006-08-31
forum: Desktop Environments
---

### Post by gnejusz on 2006-08-31
I've got al little problem. I've got a fat parttiton.
After some hours it becames Read-Only.
There is a pise of syslog:
```
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
Aug 31 16:41:30 localhost kernel: [17247092.960000] FAT: Filesystem panic (dev hda6)
Aug 31 16:41:30 localhost kernel: [17247092.960000]     fat_bmap_cluster: request beyond EOF (i_pos 177564155)
```

---

### Post by Dramist on 2006-08-31
well theres your problem.. your using fat...

---

### Post by gnejusz on 2006-08-31
I think that is a kernel-bug

---

