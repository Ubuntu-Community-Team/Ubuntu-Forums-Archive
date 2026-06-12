---
title: "what's keeping me from enjoying ubuntu"
date: 2006-03-20
forum: Desktop Environments
---

### Post by oneiropolos on 2006-03-20
Hello guys! Ok here is the story:
some days ago i installed ubuntu on my pc (P4 3Ghz, 1 Gb ram, 2 hard drives 80 Gb's each). Installation completed. The only problem i faced was with the DHCP network configuration so i opted for "Do not configure the network at this time" or sth like that, but as far as i know i can configure it later anyway, isn't that right?

anyway after the installation i logged in and everything was fine. The following day, when i was starting the pc, the following message kept flashing on my screen:
"Buffer I/O error on device sda1, logical block 1773568 ata1:command 0x35 timeout, stat 0xd0 host_stat 0x61 ata1: translated ATA stat/err 0x35/00 to SCSI SK/ASC/ASCQ" So I restarted but: "Error 17" and ubuntu wouldn't start :(

I reinstalled ubuntu with no problems again (except for the DHCP issue) and came across the same problem when restarting my pc. From the message i may suppose that there is a problem with me first hard drive? should i try to install ubuntu on sdb1? what should i do?

Help plz!
Thanx in advance
A linux newbie

---

### Post by mority on 2006-03-20
I would say that your assumption is pretty right. Probably the harddisk, or at least the master boot record of it, is somewhat broken.
If you reinstalled Ubuntu and the very same error appears again, I would say that the problem is really a hardware fault. I think your idea to try and install Ubuntu on the other harddisk is the best way to make sure. I would do the same.
And if the error does not appear with the second harddisk, you should try to RMA the broken one. If the error does appear with the second harddisk as well it may still be a hardware problem but with the SATA controller.
Good luck...

---

### Post by xmastree on 2006-03-20
What disks do you have in there? sda1 sounds like a sata drive, is that right?

---

