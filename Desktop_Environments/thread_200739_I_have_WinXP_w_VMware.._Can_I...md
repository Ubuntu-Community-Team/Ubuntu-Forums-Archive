---
title: "I have WinXP /w VMware.. Can I.. ?"
date: 2006-06-20
forum: Desktop Environments
---

### Post by dBLiSS on 2006-06-20
I have WinXP /w VMware setup and working. I also have two harddrives in this computer that are NTFS. Can i access these NTFS harddrives from my VMware WinXP with full read/write?

---

### Post by G Morgan on 2006-06-20
I don't think so, you need the drivers in the kernel for full read write and their not fully stable yet. One posibility (if you don't plan on reinstalling Windows) is to backup your data then convert the partition/s to ext3 then install your VM there then move the data back in either using Samba (would be the most work) or some kind of media (CD/DVD-R, flash drive).

Do you have VMware workstation or player. If you only have the player it may take some work to get a VM running to begin with (lack of VMware tools, configuration only posible by editing a text file).

---

### Post by dBLiSS on 2006-06-20
Thanks for the reply. It looks like I would be able to access the NTFS partitions if i had RW access compiled. I do have Vmserver installed and it is working fine. I would like to convert my ntfs partitions to ext3 but, i have 600 gigs over 3 harddrives in NTFS and no where to back to all up to do the conversion.. anyway, thanks for the help.

---

