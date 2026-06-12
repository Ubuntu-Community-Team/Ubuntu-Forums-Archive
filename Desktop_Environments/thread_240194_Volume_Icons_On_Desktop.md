---
title: "Volume Icons On Desktop"
date: 2006-08-20
forum: Desktop Environments
---

### Post by PRGUY85 on 2006-08-20
Hey:  

Ubuntu makes the partitions on my hard drive appear on the desktop. I know how to turn them off on completely but I would like to have my CD and USB volumes still appear on desktop.  I just dont want the partitions to appear on the desktop, everything else is fine.

---

### Post by PRGUY85 on 2006-08-20
If not, how can you unmount a USB device without going to the desktop icon and hitting eject?  Is there a way to do it through Nautilus once I open the USB drive?

---

### Post by steve.horsley on 2006-08-20
I believe that hard drive partitions only show up on the desktop if they're mounted on /media. Try mounting them under /mnt instead of /media. You'll need to make the directories under /mnt and then edit /etc/fstab.

---

