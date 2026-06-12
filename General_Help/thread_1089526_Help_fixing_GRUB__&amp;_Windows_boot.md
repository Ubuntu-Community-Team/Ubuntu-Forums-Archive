---
title: "Help fixing GRUB  &amp; Windows boot"
date: 2009-03-07
forum: General Help
---

### Post by Rubicon421 on 2009-03-07
I installed Ubuntu 8.10 from a live CD onto an external HD on a Machine w/ WinXP. The install completed successfully but when I rebooted the computer wouldn't finish booting.
It showed the BIOS/shipset screen, then showed the blank screen with the cursor for about 30 seconds. Then it just said "GRUB _" in the upper right corner and wouldn't get any further.
I turned off the external USB drive that I installed to and now it gets to the screen with the cursor then starts beeping constantly and really fast. 
During the install at the very end of the options before it starts copying files, I when to the advanced options and chose the Windows XP installation for where to put the bootloader. 

So... Does anyone know how to repair whatever it is about the XP install on the C: drive that is keeping it from booting with the external HD off? I'll worry about installing Ubuntu again later. I just want to fix the Windows boot first. I can still access & edit files on the C: drive using a live CD or any kind of rescue CD but it won't boot so I can't do it from windows unless I pull the HD and do it on a different machine.

---

### Post by GSF1200S on 2009-03-07
> **Kill Vista said:**
> I installed Ubuntu 8.10 from a live CD onto an external HD on a Machine w/ WinXP. The install completed successfully but when I rebooted the computer wouldn't finish booting.
It showed the BIOS/shipset screen, then showed the blank screen with the cursor for about 30 seconds. Then it just said "GRUB _" in the upper right corner and wouldn't get any further.
I turned off the external USB drive that I installed to and now it gets to the screen with the cursor then starts beeping constantly and really fast. 
During the install at the very end of the options before it starts copying files, I when to the advanced options and chose the Windows XP installation for where to put the bootloader. 

So... Does anyone know how to repair whatever it is about the XP install on the C: drive that is keeping it from booting with the external HD off? I'll worry about installing Ubuntu again later. I just want to fix the Windows boot first. I can still access & edit files on the C: drive using a live CD or any kind of rescue CD but it won't boot so I can't do it from windows unless I pull the HD and do it on a different machine.

Well, ive dual booted before quite a bit, and I have experience with Grub, so ill try to help. I have never installed to an external though.. Could you post a copy of your menu.lst, and the results of sudo fdisk -l WITH the external hooked up? Obviously this would require a boot from a livecd which sucks, but Im not entirely sure of your configuration.

---

