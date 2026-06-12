---
title: "ACPI question.... plz help me to understand."
date: 2005-07-30
forum: Desktop Environments
---

### Post by bravo_elf on 2005-07-30
I've asked before  but got no answer so maybe I'll try to spell it another way
On my laptop (TravelMate 4602WLMi) when I've installed Kubuntu I've setted "ACPI=off" cause it refused to install with ACPI enabled. But there is another problem appears, I can't  shut down my laptop it gives me some kind of error(read: [http://ubuntuforums.org/showthread.php?t=51260&highlight=unable+shut)](http://ubuntuforums.org/showthread.php?t=51260&highlight=unable+shut)).[color=red] All I need to know if this relates to ACPI or not? If "yes" how can I fix it? Futhermore I would prefer to receive some more explanations about ACPI in linux at all and how people configure it? [/color]

---

### Post by Lambert on 2005-08-01
[QUOTE=bravo_elf]I've asked before  but got no answer so maybe I'll try to spell it another way
On my laptop (TravelMate 4602WLMi) when I've installed Kubuntu I've setted "ACPI=off" cause it refused to install with ACPI enabled. But there is another problem appears, I can't  shut down my laptop it gives me some kind of error(read: [http://ubuntuforums.org/showthread.php?t=51260&highlight=unable+shut)](http://ubuntuforums.org/showthread.php?t=51260&highlight=unable+shut)).[color=red] All I need to know if this relates to ACPI or not? If "yes" how can I fix it? Futhermore I would prefer to receive some more explanations about ACPI in linux at all and how people configure it? [/color][/QUOTE]
 I can't be much help of your problem but here is a good link that might help you understand powermanagement  and linux.

[http://tuxmobil.org/apm_linux.html](http://tuxmobil.org/apm_linux.html)

---

### Post by az on 2005-08-01
What are your bios setting in terms of power management?

Can you tell your BIOS to use ACPI or APM only?

As it is now, what do you haqve plugged into your usb ports?  Since that error is new, maybe there is a device that is not playing nice with the other kids.

Also, as it is not, you have acpi disabled.  Try loading the apm module and shutting down


sudo modprobe apm

and see what happens...

---

