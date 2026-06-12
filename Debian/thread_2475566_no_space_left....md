---
title: "no space left..."
date: 2022-06-01
forum: Debian
---

### Post by jotauve on 2022-06-01
Hi people. I ve a debian with 2 entries in the fstab, mounted in /media. One is an internal disk and another is a remote NAS (in the same lan, mounted in /media/backups). Sometimes, for unknown reasons, the NAS fails and the nightly backups are made in the /media/backups directory of the computer  instead in the "/media/backups" of the NAS. The main disk is little and a no space left in device is shown everywhere... the apache stop working and I ve many problems when this occurs, some idea how to solve that? thanks!

---

### Post by Impavidus on 2022-06-01
Make sure that the backup script first checks to see if the backup location is mounted. A simple trick is to put a file with a specific name in the directory used as a mountpoint. If the file appears there, the backup drive isn't mounted.

---

### Post by ActionParsnip on 2022-06-01
Clear space where you can

---

### Post by howefield on 2022-06-01
Thread moved to the "*Debian*" sub forum for a better fit.

---

### Post by Tadaen_Sylvermane on 2022-06-01
You can also use the mountpoint command

```
mountpoint -q /media/backups || exit 1
```

---

