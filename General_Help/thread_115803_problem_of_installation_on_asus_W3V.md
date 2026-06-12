---
title: "problem of installation on asus W3V"
date: 2006-01-11
forum: General Help
---

### Post by pat85 on 2006-01-11
Hi all, yesterday i tryed to install on my Notebook (asus W3V) Ubuntu (2.6.12-9-386) but I had some big problem..
after the intallation my NB try to boot ubuntu but stop at 1/3 of the loading and have problem with "starting hotplug subsystem"...
I try to boot with recovery mode but it dosn't run.. it take me the following errors:


"snd-hda-intel: can't be loaded"
"missing kernel or user mode driver snd-hda-intel"
"<3>hw_random: RNG not detected"
"hw_random:can't be loades"
"missing Kernel or user mode driver hw_random"
 
what can i do??

thanks

---

### Post by milstead on 2006-01-11
Interrupt grub and edit the standard boot line to add some combination of the following at the end:

apm=off
acpi=off
apic=off

Boot from the first line and see what works.
Make the working change permenant by editting /boot/grub/menu.lst

Timie Milie.

---

### Post by pat85 on 2006-01-11
hi. when start grub i press "e" and after i go to the second line and press "e" after i add to the line one of the three option, press "enter" and after i press "b" from the first line.. is correct?? becouse i try with all the three option but however it cant boot...

thanks a lot

---

### Post by milstead on 2006-01-12
Yep that is the right way to do it.
Looks like it is something else :( .
There are plenty of other things ones can add at this stage.
e.g. things to control the ide driver etc.
These can all help with your problem although it might be something completely different.
I'd suggest look them up and trying a few.
Sorry I can't be more useful.

Timie Milie

---

### Post by Gardar on 2006-03-20
I've got the exact same problem, nothing I've tryed seems to work. :/

---

