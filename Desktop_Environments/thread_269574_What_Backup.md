---
title: "What Backup?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Branta on 2006-10-01
**What _backup_** should I use for Ubunto 6.06?


--- Bob ---

---

### Post by aysiu on 2006-10-01
I like *rsync*.

```
rsync -av /home/username /backup/media
``` When you repeat the command, it'll copy over only files that have been added or changed since the last backup.

---

### Post by orb9220 on 2006-10-02
Hey aysiu since U R here does rsync support backing to fat32?
I think there was something to say no to use tar instead.

---

### Post by aysiu on 2006-10-02
As a matter of fact, it doesn't. Glad you asked.

---

### Post by Branta on 2006-10-02
I _succeeded_ in BU to **_XP ]NTFS**_ with:

  ```
sudo rsync -av /home/bob /media/Back\ Up
```

This is what I wanted!

Thanks, Bob

~~~

FYI, here is my system:

  sudo fdisk -l

Linux:

  /dev/hda2
  /dev/hda5

XP NTFS:

  /dev/hdb1   
  /dev/hdb2
  /dev/hdb3
  /dev/hdb5
  /dev/hdb6
  /dev/hdb7   This is 'Back Up'

---

