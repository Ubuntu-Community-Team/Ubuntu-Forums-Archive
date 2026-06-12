---
title: "usb disk disconnected and reconnected while writing"
date: 2010-11-24
forum: Desktop Environments
---

### Post by clatclat on 2010-11-24
Hi,
since some weeks I have a problem with an external disk (ntfs formatted). I'm using that drive since more that a year without problems for my backups, and the disk seems to still work properly. Now however, while one of my backup scripts is writing on the disk, the disk is disconnected and then reconnected. The script doesn't mount/unmount the disk, just rsyncs two files. This happens almost every time the script writes to the disk (it's a 8 Gbyte file, so the rsync lasts for some minutes), usually leaving the disk with errors that I must recover on a Windows system. I didn't find anything interesting in the system logs, only a:
Nov 24 19:11:36 kernsrc@claudio [ 8086.815714] usb 1-3: USB disconnect, address 10

followed by a lot of I/O errors.
I have vmware running on the system. I noticed that while a disk is connected to vmware, it happens sometimes that the disk is disconnected from vmware and reconnected to the host, with obvious I/O errors from the Windows application, so today I tried removing the usb_storage module; while a windows guest was working on the disk, the usb_storage module was reloaded and the disk reconnected to the linux host.
So, it seems that something every now and then "works" on the usb disks, disconnecting and then reconnecting the disks, no matter if they are in use. Ant hint?

thanks,

- Claudio

---

