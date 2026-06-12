---
title: "Error ejecting disc"
date: 2009-01-14
forum: General Help
---

### Post by mustanggt359 on 2009-01-14
i get a message when i try to eject the disc and it tells me i do not have privlage to umount volume and i cant eject the disk

---

### Post by albinootje on 2009-01-15
> **mustanggt359 said:**
> i get a message when i try to eject the disc and it tells me i do not have privlage to umount volume and i cant eject the disk

Is it a cdrom ? If so, try :
```

sudo eject /dev/cdrom

```

---

