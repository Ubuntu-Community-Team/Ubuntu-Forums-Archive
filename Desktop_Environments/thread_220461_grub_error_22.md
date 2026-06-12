---
title: "grub error 22"
date: 2006-07-21
forum: Desktop Environments
---

### Post by skix on 2006-07-21
hi

I'm not too experienced with ubuntu or linux at all so please bear with me

i have an issue with grub that only occurs when i have a hard drive plugged in via the sis 180 chipset on my motherboard (ecs kn1 extreme)

when i installed ubuntu this hard drive was not even an option in the partitioning wizard so i assume i need drivers for the chipset

before grub even loads it says error 22
but if i unplug the hard drive grub loads without a problem and i can start any os

any ideas? or am i missing something obvious?

thanks

---

### Post by philippe_carlo on 2006-07-21
From the grub docs:
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

Was there something on the hard drive before? 

I remember having troubles with SiS chips myself. Make sure that the drive is not on a RAID connector, and make sure it is listed as the second drive in the BIOS.

---

### Post by skix on 2006-07-21
yes the drive is full of stuff that i don't want to lose, but i can copy it to another computer if its neccesary to format it or something (no OS is installed on the drive). and yes it is the last drive in the BIOS boot order if that's what you mean

i have the drive plugged in at the moment, though i had to boot off the cd and select boot off first hard drive in order to load grub without the error.
before i started ubuntu i used the command line in grub to see if it even detects the hard drive and it does--is there anything i should do from there?
but now that i'v logged in to ubuntu grub fails to detect the hard drive. its not set up in a RAID array and is a plain IDE drive

---

### Post by skix on 2006-07-22
ok iv managed to fix grub ..... i don't know how but it involved breaking everything in the process

however i still cannot access the drive on the sis chipset through ubuntu
any help on that?

thanks

---

