---
title: "Thunar disconnects USB when filesystem mounted"
date: 2017-08-22
forum: Desktop Environments
---

### Post by stlu on 2017-08-22
Hi,

Normally you have a USB flash drive or external hard drive with one big partition.  But I have a USB enclosure that I put a drive in with 2 partitions.  Both the partitions mounted when I connected the drive.  

When I use the 'eject' button in Thunar on one of those partitions, it does unmount it, but it then does something to disconnect the USB device, which leaves the other partition to be unmounted forcibly.  This could cause loss of data.  Should I file a bug report?  If so, against which package?  Thunar? Or perhaps a daemon that manages mounts?

Thanks.

---

### Post by &amp;KyT$0P# on 2017-08-22
Just right-click it and select "Unmount" instead of ejecting it.

---

