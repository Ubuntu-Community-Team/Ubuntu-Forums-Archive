---
title: "Creating a Windows Boot Disk"
date: 2009-01-29
forum: General Help
---

### Post by Elemaoh on 2009-01-29
When I installed Ubuntu I formatted my Windows Vista off. Im going to now dual boot but need to get XP installed. When I put in my XP Boot CD, It shows I have no Hard Drives. This is because i need to load my SATA Drivers before It will pick them up. I have the drivers, and need to put them on a Windows Bootable CD, as I have no Floppy disk or Windows machine to use nLite with. Are there any other ideas to try?

---

### Post by prince_niceguy on 2009-01-29
check this out..... 

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by mozkill on 2009-01-29
1.  All you need to do is set your SATA drives in your bios to use "IDE" mode.  In that case Windows install will see the drives without any problem.   Once you get windows up, then "I think"  your SATA driver installation archive will allow you to pre-install the SATA drivers.  Then you reboot your machine and change the bios to SATA mode and then windows will probably detect it i think.

2. Once you get it running then you back it all up using Clonezilla.

3. Then, you attempt your Linux install over the XP install.

4. Finally, you backup the config again using Clonezilla.

---

