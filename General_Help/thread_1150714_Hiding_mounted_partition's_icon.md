---
title: "Hiding mounted partition's icon"
date: 2009-05-06
forum: General Help
---

### Post by 343GuiltySpark on 2009-05-06
Hello,

2day I made a dual boot with 7 and ubuntu. Since 7 is so f***ing dumb, there is no way to read ext4 drives, and I need my files, so I made 4 ntfs partitions separated from the OSs ones (documents, pictures, music, video) and told ubuntu to mount them in my home folder.

This works great (ok, ntfs doesn't work great, but the trick works) except for one little problem. Since the partitions are automatically mounted, I see them on my Desktop as external drives.

Now, I definitely can live with that. But if anyone knew some tricks to avoid them showing up I'd love it, I'm just bothered from those 4 little disks! ^^

---

### Post by mcduck on 2009-05-06
> **343GuiltySpark said:**
> Hello,

2day I made a dual boot with 7 and ubuntu. Since 7 is so f***ing dumb, there is no way to read ext4 drives, and I need my files, so I made 4 ntfs partitions separated from the OSs ones (documents, pictures, music, video) and told ubuntu to mount them in my home folder.

This works great (ok, ntfs doesn't work great, but the trick works) except for one little problem. Since the partitions are automatically mounted, I see them on my Desktop as external drives.

Now, I definitely can live with that. But if anyone knew some tricks to avoid them showing up I'd love it, I'm just bothered from those 4 little disks! ^^

Configure those partitions to mount into any other location than in /media (Any drives mounted in /media will automatically appear on desktop). I recommend using /mnt for any internal partitions you want to mount but not to appear on desktop.

---

