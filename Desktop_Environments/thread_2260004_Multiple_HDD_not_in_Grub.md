---
title: "Multiple HDD not in Grub"
date: 2015-01-08
forum: Desktop Environments
---

### Post by danraskew on 2015-01-08
I have 2 hdd in my machine. One has 2 partitions, a Win 7 and Ubuntu 14.04. The other is my work HDD with Win 7. I have BIOS set to boot to the Ubuntu/Win7 hdd. I then get the Grub menu. The other HDD is not showing in the Grub menu.
  If I use the BIOS boot menu and choose the work Win hdd it will start to boot Win then switched over to the other hdd. I would like to set the BIOS to not be able to boot to the work Win7 hdd, but have it boot to Grub and from there I can choose. 
  How do I add the other hdd to Grub? The pc is an HP p7-1534.

---

### Post by oldfred on 2015-01-08
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Have you run this?
sudo update-grub

---

