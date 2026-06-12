---
title: "I can't mount my ntfs files system and My Windows Vista gone from grub"
date: 2010-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ALF102 on 2010-08-24
when I want to mount my ntfs filesystem I get this message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


When I want to enter my windows vista, its gone from my Grub menu.

---

### Post by ALF102 on 2010-08-24
Ok, I've tried sudo update-grub2 and it seems all kernels is there but windows is gone. I can assume that windows has gone from the grub.cfg

---

