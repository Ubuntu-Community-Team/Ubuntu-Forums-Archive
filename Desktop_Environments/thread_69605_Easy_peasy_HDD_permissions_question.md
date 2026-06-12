---
title: "Easy peasy HDD permissions question"
date: 2005-09-27
forum: Desktop Environments
---

### Post by Raeth on 2005-09-27
> Greets,

I installed Ubuntu 5.10 (I know, it's unsupported and all that), and all went well, detecting my USB hard drive's partitions as sda1 and sda2.

GNOME goes ahead and puts them up in the Computer section.

I realised that the HD was set to read-only, and root, which was crappy, so I opened up fstab and changed the entry to "defaults,user".
```

/dev/sda1       /media/sda1     vfat    defaults,user   0       0
/dev/sda2       /media/sda2     vfat    defaults,user   0       0

```

This made the HD writeable when mounted manually (via root), but not when Ubuntu boots up.

Can anyone help?

Thanks,
Raeth
**Edit**
Solved, I removed the two lines from /etc/fstab, allowing GNOME's HAL interface to take control of the drive.

---

### Post by mlomker on 2005-09-27
> Solved, I removed the two lines from /etc/fstab, allowing GNOME's HAL interface to take control of the drive.

[This]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8") will also work.

---

