---
title: "Windows/Ubuntu 9.10 dual boot problem Dell"
date: 2010-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madli on 2010-03-14
Hi,
I have Dell Vostro 1320 and have partitioned my 320 disk in two to have dual boot with windows and ubuntu (windows XP installed first, then installed ubuntu 9.10). I have grub 2 for dual booting, which works fine until i won't use windows. Every time i work in windows for a while, the computer won't go to Grub any more. I get the message "Grub loading.", then the screen goes black and the restart starts all over again, and goes in to a cycle with it.

When i just start windows and get out within a few minutes, i get Grub working alright, and get to do dual boot. But when i use windows more, grub won't start any more.

From what i have figured out, windows seems to overwrite the mbr somehow. Is there a way to tell it not to do so?

For now, i have resolved the problem by reinstalling every time ubuntu in a separate small partition just to get grub working with mbr again. In this way i can then choose to use my initial ubuntu with all its settings etc. 

Please help :)

---

### Post by perham on 2010-03-14
> **madli said:**
> Hi,
I have Dell Vostro 1320 and have partitioned my 320 disk in two to have dual boot with windows and ubuntu (windows XP installed first, then installed ubuntu 9.10). I have grub 2 for dual booting, which works fine until i won't use windows. Every time i work in windows for a while, the computer won't go to Grub any more. I get the message "Grub loading.", then the screen goes black and the restart starts all over again, and goes in to a cycle with it.

When i just start windows and get out within a few minutes, i get Grub working alright, and get to do dual boot. But when i use windows more, grub won't start any more.

From what i have figured out, windows seems to overwrite the mbr somehow. Is there a way to tell it not to do so?

For now, i have resolved the problem by reinstalling every time ubuntu in a separate small partition just to get grub working with mbr again. In this way i can then choose to use my initial ubuntu with all its settings etc. 

Please help :)

I had the same problem on my brother's laptop. you need to install grub legacy instead. I recommend installing it from system rescuecd, but you can use any other livecd which includes grub legacy (0.97)

first, boot up with your livecd. open a terminal, use sudo -i or anything else to get a root terminal. then mount your ubuntu partition and remove everything in /boot/grub. now copy grub legacy files from your livecd to /boot/grub and make a new menu.lst that suits your computer. then install grub on mbr. now you should be fine, since grub legacy never had any problems with XP. grub2 is just useless.

---

### Post by madli on 2010-03-14
Thanks for your advice. :)

I switched to Grub Legacy but am unable to set it to boot also in Windows. I think i'm getting some line wrong in the menu.lst

In Grub 2 the Windows lines are as follows:


insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 48a8f0a5af09324
drivemap -s (hd0) ${root}
chainloader +1

How do i get Grub Legacy show (and boot to) also Windows?

---

### Post by perham on 2010-03-14
> **madli said:**
> Thanks for your advice. :)

I switched to Grub Legacy but am unable to set it to boot also in Windows. I think i'm getting some line wrong in the menu.lst

In Grub 2 the Windows lines are as follows:


insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 48a8f0a5af09324
drivemap -s (hd0) ${root}
chainloader +1

How do i get Grub Legacy show (and boot to) also Windows?

title Windows
rootnoverify (hd0,2)
chainloader +1
boot

---

### Post by madli on 2010-03-15
Still not working...

Got the error message:
Error 12: Invalid device requested

This is how my menu.lst looks now for windows. Sda is second because Dell has its own partition, which is first:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,2)
makeactive
chainloader +1
boot

---

### Post by perham on 2010-03-15
> **madli said:**
> Still not working...

Got the error message:
Error 12: Invalid device requested

This is how my menu.lst looks now for windows. Sda is second because Dell has its own partition, which is first:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,2)
makeactive
chainloader +1
boot

please post the output of "sudo fdisk -l /dev/sda"

---

### Post by madli on 2010-03-15
There you go:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = silindrit of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

    Seade Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    6  FAT16
/dev/sda2               6       17064   137026416    7  HPFS/NTFS
/dev/sda3           17065       38913   175502092+   5  Extended
/dev/sda5           38022       38913     7164958+  82  Linux swap / Solaris
/dev/sda6           17065       37414   163461312   83  Linux
/dev/sda7           37415       38021     4875696   83  Linux

---

### Post by perham on 2010-03-15
> **madli said:**
> There you go:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = silindrit of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

    Seade Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    6  FAT16
/dev/sda2               6       17064   137026416    7  HPFS/NTFS
/dev/sda3           17065       38913   175502092+   5  Extended
/dev/sda5           38022       38913     7164958+  82  Linux swap / Solaris
/dev/sda6           17065       37414   163461312   83  Linux
/dev/sda7           37415       38021     4875696   83  Linux

based on this, you need to use (hd0,1) instead of (hd0,2). see if it works.

---

### Post by madli on 2010-03-15
It did work fine to get grub legacy boot to windows. But using grub legacy doesn't solve the initial problem. I can use windows but can't boot my computer after that. :(

---

### Post by perham on 2010-03-15
> **madli said:**
> It did work fine to get grub legacy boot to windows. But using grub legacy doesn't solve the initial problem. I can use windows but can't boot my computer after that. :(

then I guess you should use windows's bootloader as the default, install grub on your ubuntu partition, and then use windows's bootloader to chainload into your ubuntu partition.

also you can use grub4dos for that matter.

[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager)

---

### Post by madli on 2010-04-03
Hello again,
Could you explain, please, how do i use windows bootloader?

M.

---

### Post by perham on 2010-04-03
here's a guide:

[http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3](http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3)

here's a thread about this:

[http://ubuntuforums.org/showthread.php?t=615242](http://ubuntuforums.org/showthread.php?t=615242)

always search first. there are lots of stuff about this on the internet.

---

