---
title: "/mnt Mounts not showing on desktop/Places."
date: 2009-05-29
forum: General Help
---

### Post by GAZ082 on 2009-05-29
Hi guys. I edited fstab to mount fixed devices on /mnt and keep /media for removable. The thing is, the mounts on /mnt do not show in the desktop.

Any tip?

Thanks!

---

### Post by CatKiller on 2009-05-30
I'm pretty sure that's by design.

You can either mount them under /media to show them on the desktop, or bookmark the location (to have it show in the Places menu) and make a launcher on the desktop for ```
nautilus /mnt/whatever
```

---

### Post by mcduck on 2009-05-30
Catkiller is right, only drives mounted under /media are supposed to appear on desktop and the Places-menu.

---

### Post by GAZ082 on 2009-05-31
Thanks guys.

---

