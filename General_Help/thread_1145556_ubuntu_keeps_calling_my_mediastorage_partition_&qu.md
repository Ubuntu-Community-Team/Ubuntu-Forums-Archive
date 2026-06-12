---
title: "ubuntu keeps calling my /media/storage partition &quot;100.0gb media&quot;"
date: 2009-05-01
forum: General Help
---

### Post by anonymousT on 2009-05-01
not a big problem but does anyone know how to change it?

---

### Post by soro2005 on 2009-05-01
I think it'll stick if you install/open Gparted/Partition Editor select the partition, right click and assign a label. If not, you'd have to define a mount point in /etc/fstab.

---

### Post by taurus on 2009-05-01
Change the label of your drive to something else then.

---

### Post by mb_webguy on 2009-05-01
Is this removable media, like a USB drive?  If not, it shouldn't be mounted under /media.  Anything under /media is treated as removable media, which can cause problems if it's actually not.  A better place to mount general-purpose partitions would be /mnt.

---

