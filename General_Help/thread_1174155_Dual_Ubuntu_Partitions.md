---
title: "Dual Ubuntu Partitions"
date: 2009-05-30
forum: General Help
---

### Post by Tanner2007 on 2009-05-30
I made the stupid mistake of installing a second ubuntu partition so I can copy files from one to the next since I have display problems. Now the new one boots up, but old one with my files on it, freezes during half of the boot up, the bar freezes and everything, even my keyboards lights flash. When I see the boot loader (grub) during boot says there's two ubuntu partitions but my old one is something like  /dev5 or something, In new partition i can access old one but does not say anything expect 18.8 gb partition instead of a name. So anything I can do.

---

### Post by ajgreeny on 2009-05-30
What do you actually want to do?  It will be very easy to copy all your files from the old, non-booting install to the new one which does boot, using nautilus in this new good install.  Then you can get rid if the old version if you want, simply by deleting the partition(s) and adding the free space to your good new version, or just keep it separate with a reformat to ext3, and mount it at boot with a line in /etc/fstab so you can use it for storage.

---

