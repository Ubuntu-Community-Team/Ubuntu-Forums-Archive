---
title: "I've lost boot options menu"
date: 2006-08-26
forum: Desktop Environments
---

### Post by PaulFXH on 2006-08-26
I use a multi-boot system with WinXP and several Linux distros (including Ubuntu Dapper). Grub is the bootloader and resides in the mbr.

However, yesterday, I temporarily set the floppy drive as the first boot option. When I resumed my normal boot sequence, I found that my boot option menu no longer appeared on boot up. Rather, I get a non-GUI window offering F1 or F2 as the only options. F2 boots to WinXP and F1 runs the Dell Diagnostic routine for hardware. So, essentially the Linux OSs are no longer available directly from the HDD.

(Note that I can still multi-boot but only when I use my bootcd).

I have restored the Grub files to the mbr using this link: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/) but all to no avail.

Anybody know what's wrong?

---

### Post by v1ct0r on 2006-08-26
Give us some info about your partition scheme/OSes. 
I guess you could try and edit the grub.conf using a live cd of your choice [ [SLAX](http://www.slax.org/download.php) helped me a lot in the past...]

---

### Post by PaulFXH on 2006-08-26
Thanks for your reply, v1ct0r
OK, here's the partition table:

			
hda1	        FAT16	       Primary  Dell Diagnostics
hda2	        ntfs	       Primary	WinXP
hda3		               Extended	
hda5		               Logical	Linux Swap
hda6	        ext3	       Logical	Ubuntu root
hda7	        ext3	       Logical	Ubuntu home
hda8	        ext3	       Logical	Debian root
hda9	        ext3	       Logical	Zenwalk root


When you say grub.conf, presumably you mean menu.lst?
One thing I'm puzzled about is that the menu.lst is actually there but has been somewhat altered since I first created it. Now, the Zenwalk entries are missing but both Ubuntu and Debian are still there. Nevertheless, neither shows up as a boot option.

I think Zenwalk got missed out when I "restored" grub to the mbr and Zenwalk is actually bootloaded by Lilo.

Would welcome any comments
Paul

---

### Post by arbind on 2007-07-09
I had ubuntu as os initially. Then i installed windows xp and lost the boot option for linux...It continued for some two days and then windows stopped working and now unable to access ubuntu also...
Can someone help??
Thnx

---

