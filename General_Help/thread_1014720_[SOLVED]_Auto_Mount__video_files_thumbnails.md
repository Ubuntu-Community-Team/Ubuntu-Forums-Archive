---
title: "[SOLVED] Auto Mount / video files thumbnails"
date: 2008-12-18
forum: General Help
---

### Post by Oliv' on 2008-12-18
Hello,

I've got Ubuntu 8.10. I've got a dual boot with windows XP.
The first time I want to access my NTFS partitions from Linux I have to manually mount the HDs. Is it possible to have them mounted automatically at the start of ubuntu ?

Something a bit annoying : when I open a directory with hundreds of video files it takes minutes to have the complete list of the files because, I guess, it opens each files to do a "thumbnail". how can I desactivate it ?

Regards,

Olivier

---

### Post by Elfy on 2008-12-18
First - automount, the easy way to get ntfs to do so is to install ntfs-config

```
sudo apt-get install ntfs-config
```

Once installed there will be a tool in system tools which will allow you to set up your ntfs mounts. Reboot and they should be there for you.

Second - file previews can be altered in Nautilus, Edit Preferences, Preview tab - Other Previewable FIles

---

### Post by Oliv' on 2008-12-18
Thanks for your quick reply !

---

