---
title: "guys i need to know abt the partition"
date: 2009-05-14
forum: General Help
---

### Post by coolbuddy88 on 2009-05-14
guys i had uninstalled ubuntu..but when i tried to install xp, i cant able to do..because it shows the error as could not be installed in raw partition.hw could i overcome this?????????

Which partition manager i have to use.....hw should i use........(by bootable disk???????)

---

### Post by KhurramM on 2009-05-14
Its not a good sign to format Linux and install XP

Anyhow, format the whole disk and install XP.

U really must join a XP forum. Try VISTA or Win7 for latest viruses and trojans.....

---

### Post by mechdave on 2009-05-14
Generally it is a good idea to install XP first as it demands being started from the first partition on the first drive. If you install XP second it will overwrite the GRUB boot loader that Ubuntu needs to be able to boot.
When I do an install I give windows a decent slice of the hard disk (roughly 20 to 50 Gig) and install Ubuntu on about 20 to 30 Gig, this allows windows a bit of room to move, believe me you will need it :) By installing Ubuntu last you will automatically add a boot option to boot windows in the GRUB boot manager. I suggest you remove all partitions from your drive and start again by installing windows first and Ubuntu afterward...
Happy Linuxing,
MechDave

---

### Post by coolbuddy88 on 2009-05-14
thanx for ur reply.....may i know which bootable partition manager is good???????

---

