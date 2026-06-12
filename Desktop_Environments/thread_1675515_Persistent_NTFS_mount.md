---
title: "Persistent NTFS mount?"
date: 2011-01-25
forum: Desktop Environments
---

### Post by avatarmonkeykirby on 2011-01-25
Is there a way to persistently mount my NTFS drive?

---

### Post by ajgreeny on 2011-01-25
Yes.  Edit the /etc/fstab file by adding the line:-
```
UUID=1a3edc2d-4fe7-49e6-8bcc-179e5d5df49f /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```make sure you get the UUID correct from command ```
sudo blkid
```and use the mount point you currently use in place of /media/windows, if that is not correct for your system, as there is no point making another one.

Or do it the easy way with the package **ntfs-config** with ```
sudo apt-get install ntfs-config
```

The first method may stand you in good stead, and give you a better understanding of the way linux works, but it's your choice.

---

