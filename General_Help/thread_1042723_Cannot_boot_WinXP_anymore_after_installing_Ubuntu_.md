---
title: "Cannot boot WinXP anymore after installing Ubuntu on second HD"
date: 2009-01-17
forum: General Help
---

### Post by Cornova on 2009-01-17
I have two hard drives (both SATA), one has WinXP and the other had an older version of Ubuntu on it that gave me trouble with the new motherboard I had to put in. I decided to unplug my WinXP hard drive because I was afraid I'd accidently use that one to install the latest Ubuntu instead of doing so over the existing old one.

Everything installed just fine, hardware works and everything, but when I shut it down to place my WinXP HD back into SATA1 and the Ubuntu HD to SATA2 I get a GRUB “error 2.” I tried going into the BIOS and it sees my WinXP HD but it doesn't show up under the “boot order” options, the Ubuntu HD does even when I unplug it. 

When I unplug the Ubuntu HD and try to boot with my WinXP HD I still get the same GRUB “error 2.”

The motherboard is an ASUS P5GC-MX/1333. When I boot into Ubuntu I can mount the WinXP HD and browse it but for some reason I can't boot into it (it doesn't show up on the GRUB list either). Do I need to add it to GRUB somehow? Or perhaps missing something in the BIOS?

---

### Post by ac7ss on 2009-01-17
Most bios will only have the choice for HDD, FDD and CDROM for boot order. It will automatically boot from the first HDD boot partition.

If the computer will boot from the boot sector of the linux disk, you will need to configure GRUB to see the boot sector of the windows disk. If you can get to the grub screen, you can force the system to boot from any disk attached to the machine.

---

### Post by Dieseler on 2009-01-17
I think you just need to add this to the bottom of your grub menu.lst under the Commented out #lines.
Its at the very bottom. The quoted text works for me on my grub and my Win Xp is on sdb1.
So the entry could be different in the two map entries depending on where your win xp is.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


> title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I'm assuming that Ubuntu is installed on the master cable (sda1) and Win XP (sdb1) is on the secondary as that is the way mine is set up and that way you will get the option to boot to XP.
You may just have a black screen and see a countdown at boot up, if so hit escape real quick and you should see the window to choose. I don't see how it could hurt to try this other than you have to be able to get root privelege to save the menu.lst... If it doesn't work you can just delete the entry.

I would rather you wait till someone else helps though because I'm a newB really.
I have edited the crap out of this, but one more suggestion with the above, put the Ubuntu drive as master and you should be ok.

---

### Post by lakersforce on 2009-01-17
Perhaps you have attached your harddrives in the wrong order?

---

### Post by Dieseler on 2009-01-17
Looks like he did the same thing I did.
He unplugged his XP drive cause he was scared of the installer. I was to.
The ubuntu install would have found and edited grub for him if the drive had been in I think.
So now just boot off the Ubuntu drive (master) edit grub and you should be fine. It only takes a second at the grub menu to choose XP.

---

### Post by Cornova on 2009-01-17
The HD's are SATA so they shouldn't need master and slave. I am trying to figure out how to add WinXP to the GRUB list, I got it to show but the syntax might be wrong.

---

### Post by Dieseler on 2009-01-17
KK, read up on this a little and you will be up again in no time.

[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

If you have both drives in you can > sudo fdisk -lu from terminal to find out how they are listed.
sda, sdb and so on.
Grub starts its numbering at 0 like hd0,0  ...  hd1,0 and so on.
So sda1 would be hd0,0 in grub.

---

### Post by Cornova on 2009-01-17
I just tried the format you posted Diesler and I was able to both see WinXP on the list and boot into it. I will check out that link to familiarize myself with the variables involved--I may want to put Ubuntu back on SATA2 but it does work. 

Thank you very much for the help.

---

### Post by Dieseler on 2009-01-17
Glad to help.

:guitar:

---

