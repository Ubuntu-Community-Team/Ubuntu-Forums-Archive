---
title: "I srewed up the bootloader...please help!"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Blue1k on 2005-04-09
Ok I am a moron but I need help...BAD

This is my set up:

I have a 120GB SATA drive that I had WinXP installed (NTFS) then added Mandrake 10.1 to the same drive. I also have a 60GB IDE drive that is just a back up (it is FAT32). 


Well I got sick of Mandrake and decided to try the new Kubuntu. I deleted the Mandrake partition with Paritition magic and installed Kubuntu to the free space on the SATA drive. I then screwed up somehow. When I was asked to load the bootloader (grub) it asked to install to the MBR (which it decided should go on the IDE drive). When I did that Grub was not detected and the old LIlo loader booted up.

Ok, so I decided to install teh loader to the SATA drive. (in the win partition). I made sure to flag the / partition. Well I got this error and repeated itself when I also tried to load grub to ext3 (/)

root (hd1,2)
error 22: no such partition

when I tried to boot into WinXP I got this:

root (hd1,0)
error 22: no such partition


PLEASE HELP! I need this computer for school and I am having to use Knoppix Live to type this

Thanks in advance!

---

### Post by tiiim on 2005-04-09
[QUOTE=Blue1k]Ok I am a moron but I need help...BAD

This is my set up:

I have a 120GB SATA drive that I had WinXP installed (NTFS) then added Mandrake 10.1 to the same drive. I also have a 60GB IDE drive that is just a back up (it is FAT32). 


Well I got sick of Mandrake and decided to try the new Kubuntu. I deleted the Mandrake partition with Paritition magic and installed Kubuntu to the free space on the SATA drive. I then screwed up somehow. When I was asked to load the bootloader (grub) it asked to install to the MBR (which it decided should go on the IDE drive). When I did that Grub was not detected and the old LIlo loader booted up.

Ok, so I decided to install teh loader to the SATA drive. (in the win partition). I made sure to flag the / partition. Well I got this error and repeated itself when I also tried to load grub to ext3 (/)

root (hd1,2)
error 22: no such partition

when I tried to boot into WinXP I got this:

root (hd1,0)
error 22: no such partition


PLEASE HELP! I need this computer for school and I am having to use Knoppix Live to type this

Thanks in advance![/QUOTE]
 grub should sit nicely on the MBR! Kubuntu should detect the win partition and shub it on the MRB there should not be a prob.

So either reinstall Kubuntu on the same partition and shub grub or lilo on the MRB. 

There is out there a linux rescue cd you can download but if your typing on a live cd then reisntall kubuntu on the space it should have a parition prog already built in use the existiting space and use the MBR only!

also grub should go on the first drive. if your IDE drive is the second hard drive that may be the prob. put grub on the MBR on the first drive it wont screw up windows if that the drive its on, its sits on the MBR. So reinstall kubuntu. If worse comes to worse a OS is better than  none!

---

### Post by Blue1k on 2005-04-09
Victory is mine! 

All I did was unplug the IDE drive (just storage) and install Kubuntu. I loaded grub into the MBR and presto everything is working.

I am very impressed with how fast everything runs. I am glad I chose Kubuntu!

Cheers!

---

### Post by digby on 2005-04-09
I like the inventive solution.:grin:

I bet what happened is that the installed assumed that the IDE drive was the boot drive instead of the SATA.   Do you remember exactly how you set up the partitions on the first install?

---

