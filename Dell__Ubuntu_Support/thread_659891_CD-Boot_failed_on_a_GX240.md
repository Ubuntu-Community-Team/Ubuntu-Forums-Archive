---
title: "CD-Boot failed on a GX240"
date: 2008-01-06
forum: Dell  Ubuntu Support
---

### Post by thomm on 2008-01-06
I've tried booting with several distributions (Ubuntu, Mandriva, Knoppix, Fedora, Kanotix) and had every time the same result. Also after a BIOS-Update to A05.
With the Kubuntu 7.04 alternate CD I got the message: "CD-ROM couldn't be mounted" after the menu. I tried some kernel options (noacpi=force, noapic nolapic) as discribed in former threads, but it don't work.
Then I would like to save the debug logs to floppy and I got the message: "Floppy couldn't be mounted".
The drive is a Samsung SN-124, Chipset is Intel 82845.
Has anyone an Idea what I can do? Do I need a special kernel parameter for the chipset?

---

### Post by .nedberg on 2008-01-06
Have you checked in BIOS if your machine can boot from removable devices?

---

### Post by thomm on 2008-01-06
Yes, of course. The first boot steps are working. It boots until the main menu of Kubuntu. I can choose the ash shell. When I try to mount the CD with "mount /dev/scd0 /cdrom" I got "No medium found". The CD is still in the drive. I guess, scd0 is the device of the CD-ROM?
When I try to mount a floppy with "mount /dev/fd0 /floppy" I got "Invalid arguments".

---

### Post by .nedberg on 2008-01-07
I would guess /dev/sdc is your cd-drive

---

