---
title: "Backed up with tar"
date: 2008-12-18
forum: General Help
---

### Post by philetus on 2008-12-18
I added a HDD with a ext3 file system. It is /dev/sdb5 and it is a /media/disk.

To copy my backup to the media disk, would it be:

sudo mv /backup.tgz /dev/sdb5/backup.tgz

---

### Post by aheckler on 2008-12-18
```
sudo mv ./backup.tgz /media/disk/
```

---

### Post by kanikilu on 2008-12-18
Yes, but note that mv will move it, not copy (cp), and you can use either the device name (/dev/sdb5) or the path to where it's mounted /media/disk.

---

### Post by philetus on 2008-12-18
> **aheckler said:**
> ```
sudo mv ./backup.tgz /media/disk/
```

It wouldn't work until I removed the period

Thanks

---

### Post by aheckler on 2008-12-18
Was your backup.tgz in the root directory then?

---

### Post by philetus on 2008-12-18
It was in the "file system" which I thought was root.
When I removed the period it moved to the media disk.

---

### Post by aheckler on 2008-12-18
Yeah that was root. I was just a bit confused because the "./backup.tgz" should've indicated that the backup file was in the current directory, but I guess the working directory in your terminal was not root when you tried it.

---

