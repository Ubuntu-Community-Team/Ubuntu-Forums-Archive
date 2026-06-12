---
title: "Boot Livecd Without hard disk at all"
date: 2009-03-19
forum: General Help
---

### Post by eumetaxas on 2009-03-19
Hi,
The HDD of my compaq laptop just "died" after 6 years and cannot boot either Ubunutu or xp (dual boot). Grub starts, it gives me the menu and then nothing. Livecd stucks during boot. 

I have **ordered a new hard disk and removed the old one**.** I tried to boot again using the livecd without hard disk installed but it fails** (bios cfg to boot from cd). i can access bios, the pre-boot Execution Enviroment (PXE) and it ends saying "no operating system found".

Can't i boot from livecd without any hard disk until my new HDD comes?

thanx!

---

### Post by john183 on 2009-03-19
Most computers nowadays will not boot, even from a cd, with out a harddrive. I had the same issue when i was trying to install Ubuntu to an external harddrive, the tutorial said to remove the internal hard disk to make sure that it didn't get mistakenly used in the process. When i took the HD out the computer refused to boot from the liveCD. you may just have to put the old drive back in and then boot from the liveCD.

---

### Post by eumetaxas on 2009-03-19
Thanx for the reply.
I have tried that several times. It stucks during the booting process - it shows up a never-ending list of the **hard disk errors and does not boot**.

[B]Is there a way during boot to tell it to ignore/bypass the hard disk?
[/B]
I am writing now from my other 8 years old compaq. Thanks to Linux and LXDE/Ffce there is no reason to throw away your computers anymore:)  

Thank you!

---

### Post by fieroboom on 2009-03-19
According to the original post, his first attempt was with the original HD in, and being that his computer is at least 6 years old, I doubt taking the drive out of it would affect it.

eumetaxas, since you get the grub menu on the old hard drive, have you tried booting into recovery mode? It should spell out the boot sequence, and you'll be able to see exactly where it's failing. Not that it would help with the live cd, but it should show you like some I/O errors if it is the hard drive.
:D
-Paul

EDIT:
Looks like I took too long to reply... :)

---

### Post by fieroboom on 2009-03-19
> **eumetaxas said:**
> Thanx for the reply.
I have tried that several times. It stucks during the booting process - it shows up a never-ending list of the **hard disk errors and does not boot**.

[B]Is there a way during boot to tell it to ignore/bypass the hard disk?
[/B]
I am writing now from my other 8 years old compaq. Thanks to Linux and LXDE/Ffce there is no reason to throw away your computers anymore:)  

Thank you!

It's probably trying to allocate swap space, and since the hard drive is bad, it can't. I know Damn Small Linux has a -toram option that loads everything into memory (you need 128MB).
[This page](https://wiki.ubuntu.com/BootToRAM) walks you through creating an Ubuntu live cd that loads to ram, but it recommends 256MB+, and it says that it does momentarily access the drive in RO mode.

[Here](http://ubuntuforums.org/showthread.php?t=707230) is another site about it.
You also might be able to to use a thumb drive for swap space...
Either way, it doesn't look like it's going to be a vanilla live cd.
:D
-Paul

---

### Post by eumetaxas on 2009-03-19
> **fieroboom said:**
> I/O errors if it is the hard drive.


It is all i get, both from livecd and recovery mode.

[QUOTE=fieroboom]it recommends 256MB+ [/QUOTE]

The RAM is 720mb (on the newer one).

It looks like i am going to stay with LXDE/kazehakase/Abiword/Leafpad (which are great and fast by the way) until i get my new HHD.

Thank you all!

---

