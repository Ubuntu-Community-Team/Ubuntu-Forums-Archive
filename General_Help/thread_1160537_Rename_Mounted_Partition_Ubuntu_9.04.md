---
title: "Rename Mounted Partition Ubuntu 9.04"
date: 2009-05-15
forum: General Help
---

### Post by nephron222 on 2009-05-15
Hello!

I have my windows vista partition labeled as '162.1 GB Media' and i want to rename it to Windows Vista. How do i do that???

Thanks,
Nephron222

---

### Post by drs305 on 2009-05-15
You can label it with ntfslabel. It's part of the ntfs-config package. Install ntfs-config, then run:
```

sudo fdisk -l  # Lowercase L. To find your windows partition, it will be listed NTFS or HPFS/NTFS
sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sdXX labelname

```

Example: sudo ntfslabel /dev/sda1 windows

---

### Post by coffeecat on 2009-05-15
If you're not averse to booting into Vista, why not do it in Vista? If memory serves me correct, you simply go to My Computer, right-click on the C: partition, select 'rename' and rename the partition, which changes the partition label. I would guess there's no partition label at the moment which is why Ubuntu is showing it as 162.1 GB Media.

**Edit:** Rebooted into Vista and posting from there now, and it seems my memory is doing quite well. :) Only one mistake - in Vista it's 'Computer', not 'My Computer'.

---

### Post by nephron222 on 2009-05-15
ok ill try the windows method first! Thanks a lot guys!

---

