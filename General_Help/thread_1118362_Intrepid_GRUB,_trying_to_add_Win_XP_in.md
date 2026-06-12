---
title: "Intrepid GRUB, trying to add Win XP in"
date: 2009-04-06
forum: General Help
---

### Post by sicksix on 2009-04-06
I am trying to add Win XP into my GRUB dual boot program but I cannot figure this out as far as what the (HD) is and such..  I am really a noob at this!  I am trying to make Windows XP default on the list also..  Can you guys help me?  Here are my drives that I have /dev/sda is the windows drive and of course the /dev/sdc is the ubuntu drive.. How do I add my Windows XP to my GRUB Editor program?

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x13d09d06

Device Boot Start End Blocks Id System
/dev/sda1 * 1 41344 312560608+ 7 HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1c70416

Device Boot Start End Blocks Id System
/dev/sdb1 1 121601 976760001 7 HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Device Boot Start End Blocks Id System
/dev/sdc1 1 29638 238067203+ 83 Linux
/dev/sdc2 29639 30394 6072570 5 Extended
/dev/sdc5 29639 30394 6072538+ 82 Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16f4e251

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 30401 244196001 7 HPFS/NTFS

Disk /dev/sde: 127 MB, 127926272 bytes
16 heads, 32 sectors/track, 488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sde1 * 1 488 124911+ 6 FAT16
Partition 1 has different physical/logical endings:
phys=(486, 15, 32) logical=(487, 15, 31)

---

### Post by sicksix on 2009-04-06
please help... i cannot boot into windows xp..

---

### Post by callie510 on 2009-04-07
Wow, that is a lot of hard drives.......... my Intrepid was always smart enough to add Windows XP to my list automatically, but you can do it by hand too!

From within Ubuntu, here is how you edit your grub menu:
> 
gksu gedit /boot/grub/menu.lst

Post what this says right now? I will help you add the Windows entry to the list and make it the default entry.

---

### Post by callie510 on 2009-04-07
I just tested this on my own dual-boot XP/Ubuntu system so I know it works :) 

1) Open your menu.list for editing using:
> gksu gedit /root/grub/menu.lst

2) Look through the bottom part for any mention of Windows XP. 
If it is there, stop and post your menu.lst and I will look to see what's wrong.

If there's no mention of Windows XP, add this to the very bottom of the file (below all the Ubuntu entries).... This should work provided that your windows really is on /dev/sda1, as you said, and your Windows is a working installation.

> 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry added for Windows XP on /dev/sda1
title		Windows XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 

3) The very top of menu.lst should contain some stuff that looks like this:
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default		0

To make Windows XP your default, change the "0" to "saved":
> default		saved

This works because the Windows XP entry contained that line that said "savedefault" - now Grub will default to Windows after 10 seconds instead of Ubuntu.

Now you should have the option to boot Windows in Grub! :)

---

