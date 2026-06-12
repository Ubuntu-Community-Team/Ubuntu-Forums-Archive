---
title: "Friend Needs help...assistance, perhaps?"
date: 2013-02-21
forum: Desktop Environments
---

### Post by ButterFreedom on 2013-02-21
Dear Gurus',

I just joined this forum because I am attending a University and am in the Bachelors of Computer Science Program.  The immediate issue that I am experiencing is this:

My friend just preformed an update using "windows update" on his Multi-partitioned drive for his windows 8 partition.  In doing so, he somehow corrupted the entire partition, deleted his HP recovery partition (the one that resets the PC to factory settings) and is now not able to boot the computer to windows.  There's more.  He is unable to force, through the BIOS, the computer to boot from the Installation CD as well as any other form of media.  I, myself, have formatted a flash drive into an NTFS format to be able to load windows 8 (using an .iso file) to do a repair for his computer.  The PC will read the media when in Ubuntu but it won't initially boot the selected device. So, here in turn, lies my question.
  Not being too terribly familiar with Linux based OS's I want to know if there is any way that I can run the ".iso" disk on a virtual platform?  In theory, I should be able to run the "setup.exe" inside the ".iso" file.  The problem is that his version of Ubuntu will not allow me a initialize the ".exe", in question.  I need someone to show/inform me on how to proceed so that I may fix this so we may return to programming in our respective discipline.  Any help would be greatly appreciated.  Thanks in advance!

Regards,
ButterFreedom (aka. Jaina B.)

---

### Post by MG&amp;TL on 2013-02-21
What laptop does your friend have? This sounds like a UEFI problem to me...

---

### Post by grahammechanical on 2013-02-21
We cannot run Windows exe files on the Linux operating system. but you can use the Ubuntu Software Centre to install virtualbox (a VM) and then you can try to install Windows inside virtualbox. How well it will run depends upon the hardware and the mount of RAM it has.

My advice is to go again into the BIOS/UEFI and check every setting to see if you can set the boot priority. I recently had a problem booting from a USB stick. I set the USB memory stick to boot before the hard drive but because I had the USB stick plugged in as I entered the BIOS (don't have UEFI) the BIOS saw it as another hard disk and put in another menu option which I did not notice. In this new menu option the USB stick (hard drive) was listed after the SATA hard drive. Once I changed that boot order I could then boot from the USB stick.

Regards.

---

