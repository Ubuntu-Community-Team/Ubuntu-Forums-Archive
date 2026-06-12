---
title: "Fix silly gnome places menu behavior..."
date: 2009-05-23
forum: General Help
---

### Post by MJBoa on 2009-05-23
I've been gradually becoming more and more annoyed with the GNOME places menu and compouter:// as time goes on. To explain, I have a lot of disks and a lot of partitions that I use day to day. So I mount them all through fstab to /mnt. Now there are two partitions I don't need so I leave those unmounted.

In the places menu and computer:///, it shows the unmounted partitions and ignores the ones I mounted through fstab. It completely ignores other mounted filesystems, those on /mnt. Completely ridiculous and useless behavior. Now this would be fine if I could customize the god damn thing.
Of course, as far as I can tell I have no way of adding everything on /mnt and ignoring unmounted partitions.

To be clear, what I want is for computer:// to show all my drives on /mnt so that I can just click Computer from Places and see all my partitions.
Someone, please tell me I can change this.

---

### Post by JC Cheloven on 2009-05-23
Perhaps you've already considered it, but anyway:
Is there a reason to prefer mounting under /mnt? Perhaps legacy habits, or other distros habits?

I'd say that mounting under /media (the usual way in ubuntu) would fix your problem without changing anything else.

---

### Post by MJBoa on 2009-05-23
Alright I guess that's what I'll have to do, I guess I can only have it listed as the disk label?

---

