---
title: "Newbie problem: Ubuntu live CD error(s)"
date: 2005-12-23
forum: Desktop Environments
---

### Post by i.herteleer on 2005-12-23
Hello,
I recently downloaded the CD version for live ubuntu, which failed to work, after which i opted for the DVD version. I did a checksum on the DVD version and it's as it should be. 
I get the following error when trying to run it:
   Failed to copy file from CD-ROM. Retry? <Yes> <No>.
Hitting yes doesn't help at all. CD integrity says the file is fine.
Hitting alt-F4 gives me the following errors:
   anna[10351] or something like that and
   I/O error: process 10349,
   error code 7

I'm running a P4 3.0GHz, 1GB ram system with some cheap motherboard and a BENQ DW1640 DVD-writer. 

Any solutions?
Also, how can I easily install a multi-boot so I can chose to either start up in windows or ubuntu (till i can work ubuntu well ;) ).
Thanks for the help!
Inti

---

### Post by i.herteleer on 2005-12-23
Woops. Forgot to say: Ubuntu 5.10 for both DVD and CD-ROM
:)

---

### Post by drotter on 2005-12-23
If you want to actually install ubuntu and have windows already installed.  Ubuntu will automatically install grub (the boot loader) when you install it.  All you have to do is make the partitions for ubuntu (follow the directions) and for the swap (if you want it) and it will do the rest...

When you boot up the computer it will load grub and you'll have the option to select what operating system you want to run.

Doing things the other way (install ubuntu first and then windows) never seems to work as smoothly.  I think that windows just doesnt want to see linux and just formats over everything...

If the DVD is giving you problems just dl and burn the cd version and you can get everything else from the respositories (apt-get or synaptic).

---

### Post by cotcot on 2005-12-23
I made a dual boot 5.10 and XP with grub on a floppy. Ubuntu gives during install the possibility to define the destination of grub. When you have installed ubuntu you need to make your partition with windows active again (with fdisk or ranish for instance) because ubuntu makes the new ubuntu partition active during install. When you the put in the floppy before boot you will come on the grub menu (if the floppy is the first on boot : see BIOS). If you remove the floppy before boot you get what you had before ubuntu install. This might maybe reduce your hesitation to install ubuntu instead of using the live CD.

---

### Post by Sef on 2005-12-27
I just have set up a dual boot with XP and Ubuntu.  Make sure that the windows is installed first, if it isn't installed.   When partitioning, keep the windows partition as the bootable partition (bootable is set to yes,) and make sure the root partition's bootable is set to no.

Also follow these directions that Herman wrote.   I followed them when installing Ubuntu.

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by izm81 on 2005-12-27
i.herteleer, I know how to solve your problem!  (Because I struggled for a long time with it.)

Ubuntu disables DMA by default, but on my drive, which also happens to be a **BENQ DVD DD DW1640**, this seems to cause it to stop functioning properly!

On the LiveCD, when setting up, do the following:

[LIST=1]
[*] Enter shell from LiveCD Setup Menu
[*] ```
# hdparm -d1 /dev/cdrom/cdrom0
```
[*] ```
# umount /cdrom
```
[*] ```
# mount /dev/cdrom/cdrom0
```
[*] ```
# exit
```
[/LIST]

It should function after that.

***What Ubuntu and Ubuntu-live need are boot options to enable DMA.***  Hope that helps.

*If you decide to install Ubuntu, you will want to enable DMA by default.  You could do the above process every time you log in, or you could follow the steps here: [https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")*

---

### Post by i.herteleer on 2006-02-02
I think the problem does lie in DMA not working, but following the steps you gave, I was unable to turn it on (number = step in your instructions):
     1. Worked fine
     2. Attempting this gave the following error: "No such file or directory". I attempted looking for this file myself, and found a folder dev/cdrom**s**. I tried the command again using this folder, but this resolved nothing.
     3. "Invalid argument"
     4. "Can't find /dev/cdrom(s)/cdrom0" in /etc/fstab
     5. Only thing besides getting into the shell that worked :P

Also, I tried following the instructions on the Wiki link to turn on DMA, but this failed as well... The 'sudo' command is not recognized...

On top of that I did something stupid now. A friend told me he installed a dual boot for WinXP/Ubuntu without any trouble using Partition Magic 8.0, so I 
downloaded it and followed instructions for making a new partition that would allow me to install Linux on it. Stupid thing. I can't install Ubuntu due to the DVD drive problem (should I try getting another CD drive in my computer and trying with that?), and in the meanwhile, I can't get into WinXP either ("Error loading operating system" during startup...).

Anyone have ANY suggestions for me that would allow me to install Ubuntu and/or have WinXP work again without having to reinstall?
Thanks,
Inti

---

### Post by i.herteleer on 2006-02-03
I was able to get around the DMA problem through installing in 'expert' mode and thus succeeded in installing Ubuntu :D (finally!). Still, i remain with the WinXP problem... cant start up in safe mode either :S. Any suggestions or will I have to format the partition which has windows on it? And will this cause any other problems? (I recall reading somewhere for proper functioning WinXP HAS to be installed before Ubuntu... or does it just have to be on a partition before that of Ubuntu (cause that's the case :) )).
Thanks,
Inti

---

### Post by infoseeker on 2006-02-04
I had very strange problems booting a Knoppix live CD with the same drive (Benq DVD writer DW1640), mostly regarding hardware detection, and doing a firmware update (BSOB release), believe it or not, sorted out these problems completely (had to do it under WinXP :( ).

The only problem I have now is that KDE and linux hangs when trying to import previously saved sessions on a CD from within k3b, requiring a HARDWARE RESET.  Enabling DMA makes no difference. Tried firmware BSNB and the same happens.  Maybe I should try all the firmware releases one at a time and see what happens, starting from oldest.

The only way I get around this problem is to physically swap my drive with an older Sony CDR which works flawlessly.

The same problem occurs under Debian Sarge :(

---

### Post by infoseeker on 2006-02-05
Just completed oldish SuSe 9.1 install on a spare 6GB drive and k3b hangs at the same point.  This problem is therefore not unique to Kubuntu/Ubuntu/Debian.

---

### Post by infoseeker on 2006-02-20
To reopen this topic, has anyone managed to get a Benq DW1640 DVD-RW drive to work normally under k3b, or is it my system only ?

> 0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82865G Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)

> Linux ubuntu 2.6.12-10-686 #1 Mon Feb 13 12:18:37 UTC 2006 i686 GNU/Linux

Thanks

EDIT - Dumped the Benq drive and bought a Sony DVD RW DRU-810A.........works like a charm.

---

