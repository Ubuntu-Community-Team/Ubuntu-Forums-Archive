---
title: "Change location where Gnome automatically mounts cdrom?"
date: 2010-02-12
forum: Desktop Environments
---

### Post by Harry Muscle on 2010-02-12
Is it possible to change the location where Gnome automatically mounts the CDROM drive to?  The reason I ask is because I have two drives and I would like to rearrange them.  Currently Gnome mounts the 1st drive to /media/cdrom1 and the 2nd drive to /media/cdrom0, I'd like to swap that around (without having to swap them physically).  Anyone know where this is configured?

Thanks,
Harry

P.S.  I'm running Ubuntu 9.10 64bit.

---

### Post by freeball1 on 2010-02-12
You can change the mountpoints in /etc/fstab
In your case just swap /media/cdrom0 and /media/cdrom1

---

### Post by Harry Muscle on 2010-02-12
> **freeball1 said:**
> You can change the mountpoints in /etc/fstab
In your case just swap /media/cdrom0 and /media/cdrom1

That's what I though at first, but only the first CDROM is listed in fstab, also if my understanding is correct, the automounting done by Gnome does not rely on fstab.  So it doesn't seem like fstab is what I'm looking for.

Harry

---

