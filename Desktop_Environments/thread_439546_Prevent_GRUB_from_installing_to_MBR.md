---
title: "Prevent GRUB from installing to MBR"
date: 2007-05-10
forum: Desktop Environments
---

### Post by DemonOne on 2007-05-10
Hello,

Since I had my share of GRUB + WinXP catastrophes with Debian, I would like to install Ubuntu with GRUB installed to the root partition, and boot into GRUB from the XP bootloader.
Now, I already know how to do the later, but I couldn't bring myself to finish the installation without knowing if GRUB would be magically installed into my MBR without me knowing.

If it matters, WinXP is installed on my primary ATA HDD, and Ubuntu will be installed on my primary SATA HDD.

Finally, the question is: Does the Ubuntu 7.04 (LiveCD) installer ask where/if to install GRUB?

Thanks,

Demon.

---

### Post by phidia on 2007-05-10
I believe the livecd just defaults to installing to the mbr. This was a "user friendly" idea adopted a release or two ago.
If you want choice in where to install grub you want the alternate cd.

---

### Post by DemonOne on 2007-05-11
Well, now I won't get to have the joyful GUI based installation process.
Serves me right for wanting my MBR untouched.

Thanks for the reply phidia.

---

### Post by NilsE on 2007-05-11
There is a choice for where to put the boot record but it is pretty well hidden in one of the options around when the partitions are being done so look for it on each option screen before you click go.

It bit me once so what I did was take my internal drive out, booted with the live CD, and installed to my Ubuntu drive and of course the MBR defaults to the root partition. I then use the BIOS boot option to boot Ubuntu or that other thing called an operating system.

---

### Post by NJC on 2007-05-11
DemonOne;

On my first LiveCD install the screen resolution was stuck on 640 x 480 ... so when I arrived at the partition part of the install I didn't even SEE what was happening with respect to MBR. Grub did install onto my Win98 MBR so I had to run the fixmbr (or win98 equivalent). 

The advice I received for Install #2 was to unplug my Win drives, which I did, and of course no problems. I then added the magical code in the menu.lst to fool Win about it's Primary Master position and POOF, I had a working dual boot.

---

