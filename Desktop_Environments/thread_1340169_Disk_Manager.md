---
title: "Disk Manager"
date: 2009-11-28
forum: Desktop Environments
---

### Post by danteuk on 2009-11-28
Why isn't there one ?
searching for a disk manager, I have multiple disks and kubuntu 9.10 didn't create any mount point or fstab entries for my Windows partitions.
So now I have to try and do this manually and it's a pain in the ****.
I'd have thought there would be a reasonable gui tool for disk management in KDE by now!

NOTE:
qtparted is not available for install via apt-get.

---

### Post by Zorael on 2009-11-28
You mean, partitioning manager? There's **partitionmanager** in the repos which is Qt-based, but it doesn't beat gparted. QtParted is supposedly dead upstream.

I guess they'll help you get an overview over partitions but as far as I know they won't suggest fstab entries for you. I think those features are built into the installer (Ubiquity), and if it doesn't do the trick you'll have to resort to manual methods.

(The installer code is largely shared except for the frontend, so the same issue should happen if you install Ubuntu instead of Kubuntu.)

---

