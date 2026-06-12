---
title: "GRUB problems"
date: 2005-08-25
forum: Desktop Environments
---

### Post by Shamanix on 2005-08-25
Updated many things in Synaptic, rebooted, then i got an "error 21" while GRUB was trying to load. What's wrong? Will it help to reinstall GRUB(how?)?

---

### Post by KrazyPenguin on 2005-08-26
This may not be the best answer, but you could download the Mepis Live CD.
Choose Install after it installs, and then reistall Grub.

Then you will have to edit it to boot Ubuntu. 
Might work with other distros too, but Mepis for sure.

Hopefully you have a high speed connection ;-)

---

### Post by amohanty on 2005-08-26
From:
[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

First off in your CMOS setup make sure all your drives are active and set to Auto. If that doesnt work try the following:

If you can somehow get to the recovery console then do so and make sure that /boot/grub/menu.lst is correct. Refer to manual (above) to do so. If there is some inconsistency between the partitions you have and the grub menu file correct it, or post the question about it. 

If you cannot boot into ubuntu at all, you need to fire up your live cd and reinstall grub at the very least. There are several howtos on the forums. Just search for 'reinstall grub'.

HTH
AM

---

### Post by Takis on 2005-08-26
I had this problem after I upgraded my motherboard. The new one was auto-set to using my SATA drive as a RAID device, but since the drive hadn't been in a RAID on my old motherboard, GRUB couldn't find it. I had to disable the RAID setting on the motherboard (set it to use SATA as IDE rather than RAID) and that fixed it up right away.

---

### Post by Harleen on 2005-08-27
I had the same problem. Not only when installing Ubuntu, but also some time ago with several SuSE versions. I never got grub working. In both cases my solution was chosing lilo as boot manager. Works fine for me and is probably less trouble than chasing down the grub problem.

---

