---
title: "Copy Paste using Nautilus causes system to crash"
date: 2007-05-24
forum: Desktop Environments
---

### Post by pbala on 2007-05-24
I'm trying to copy large files from and RAID 5 to JBOD that uses 3ware's SATA RAID card and drivers that come along with Ubuntu 6.06 Linux 2.6.15.

Copies using 'cp' command line work fine. However, copying (copy and paste) the files using the file browser always crash at different points of transfer. 

Copying files (using both command line and the GNOME file manager) from RAID to root file system, root file system to JBOD dont pose a problem. It's always with copying files from RAID to JBOD and that too using Nautilus that causes the system to crash. 

I've tried a few things so far - upgrading motherboard BIOS, upgrading the 3-ware drivers / firmware/ management utilities, disabling/enabling hyperthreading in the BIOS --> nothing that seems to help. 

command line 'cp' appears to be a single threaded implementation. I'm not sure if Nautilus implements a multithreaded file copy that, perhaps causes the crash. 

Please let me know if you have experienced similar problems or know of ways around this.

---

