---
title: "missing desktop icon for mount"
date: 2005-10-24
forum: Desktop Environments
---

### Post by coldrick on 2005-10-24
Up until a day or so ago, my desktop contained an icon for each of the two disks I share with my windoze boot: one VFAT and the other NTFS. Now for some reason only the NTFS one appears, although both still are on the Places menu.

Both disks are mounted similarly in fstab:

/dev/sda2	/media/sda2	ntfs	ro,auto,umask=000 0 0
/dev/sda5       /media/sda5     vfat    rw,auto,umask=000 0 0

How do I make sda5 re-appear?

Thanks and regards,
David

---

### Post by codejunkie on 2005-10-24
[quote=coldrick]Up until a day or so ago, my desktop contained an icon for each of the two disks I share with my windoze boot: one VFAT and the other NTFS. Now for some reason only the NTFS one appears, although both still are on the Places menu.

Both disks are mounted similarly in fstab:

/dev/sda2    /media/sda2    ntfs    ro,auto,umask=000 0 0
/dev/sda5       /media/sda5     vfat    rw,auto,umask=000 0 0

How do I make sda5 re-appear?

Thanks and regards,
David[/quote]you could try adding the user option that worked in hoary but i have no idea about breezy. 
```
 /dev/sda5       /media/sda5     vfat    user,rw,auto,umask=000 0 0

```

---

### Post by coldrick on 2005-10-25
Realised I hadn't closed this off - turned out my icon was under some other icon :(

Dunno why Gnome would think that this was a sensible thing to do.

Regards,
David

---

