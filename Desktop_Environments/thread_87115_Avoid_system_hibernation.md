---
title: "Avoid system hibernation"
date: 2005-11-07
forum: Desktop Environments
---

### Post by joselin on 2005-11-07
Hi,

I have a IBM thinkpad T21 laptop... the problem comes when I close it, the system goes to hibernation mode and I want to avoid it. This laptop runs as server and I want the system runs as usual whenever is open or close. Someone can help me on that?

Regards.

---

### Post by lorenco on 2005-11-07
You might want to try and make changes to /etc/default/acpi-support
Her you cn play around with all the acpi settings...

---

### Post by joselin on 2005-11-09
[QUOTE=lorenco]You might want to try and make changes to /etc/default/acpi-support
Her you cn play around with all the acpi settings...[/QUOTE]

I don't use acpi, my kernel uses the parameter acpi=off, because if i don't use it, the network card does not work.

Any more ideas??

Thanks.
Regards.

---

### Post by wrtrdood on 2005-11-09
Seems I recall seeing something about the IBM laptops having a setting in the BIOS that controls the lid switch.  It sounds very much like you could have a hardware override going on.  Also, I think that APM is also compiled into the kernel and disabling ACPI shouldl cause APM to then take over.  Check for it in the startup with dmesg | grep APM.

---

