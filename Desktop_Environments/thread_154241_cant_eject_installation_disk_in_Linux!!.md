---
title: "cant eject installation disk in Linux!!??"
date: 2006-04-02
forum: Desktop Environments
---

### Post by UNIVSOUTHFLA on 2006-04-02
ok, now I just realized that I totally screwed up on my parition and need to reinstall OSX. Ok, when I try to eject the Linux install CD, I right click on the desktop icon for the CD, press Eject, and this error message comes up...
Unable to eject media
Show more details-
Umont:/dev/hbd mount disagrees with the fstab eject: unmount of `/tmp/disks-conf-hdb 'failed

---

### Post by aysiu on 2006-04-02
Have you tried this? ```
sudo eject /dev/cdrom
```

---

