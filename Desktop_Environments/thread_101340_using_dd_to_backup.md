---
title: "using dd to backup"
date: 2005-12-09
forum: Desktop Environments
---

### Post by vtec on 2005-12-09
I have one drive in my system and i want to back it up using a second drive in a removeable tray with dd. Is it possible to do this while the system is running, or do i need to boot off a different drive and use dd while the main drive is unmounted.

---

### Post by schilcha on 2005-12-09
I do not recommend to do so, although dd will allow it. You might run into problems, if files are changed/created/deleted while being backuped. This may result in a corrupted backup. You can try to mount the partition read-only. Depending on the contents of the partition, you have to change to runlevel 1 before, to stop all those processes writing to disk. 

Anyways, just give it a try -- maybe I'm just to cautious.

---

### Post by strawberry on 2005-12-09
[QUOTE=vtec]I have one drive in my system and i want to back it up using a second drive in a removeable tray with dd. Is it possible to do this while the system is running, or do i need to boot off a different drive and use dd while the main drive is unmounted.[/QUOTE]
I recommend 'partimage' to back up a single partition and 'parted' to copy it.

---

