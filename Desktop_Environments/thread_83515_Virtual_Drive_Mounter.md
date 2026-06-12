---
title: "Virtual Drive Mounter"
date: 2005-10-28
forum: Desktop Environments
---

### Post by rj686 on 2005-10-28
Is there anyway to mount iso's on a virtual drive, like alcohol 120 in windows. It would be nice to copy iso's for certain games to the computer(i have a laptop) rather than carry all of them with me.

---

### Post by matva on 2005-10-28
From starter guide (system->help->"Ubuntu 5.10 Starter Guide"):
How do I mount/unmount Image (ISO) files without burning?
1. To mount Image (ISO) file
sudo mkdir /media/iso
sudo modprobe loop 
sudo mount file.iso /media/iso/ -t iso9660 -o loop
2. To unmount Image (ISO) file
sudo umount /media/iso/

---

