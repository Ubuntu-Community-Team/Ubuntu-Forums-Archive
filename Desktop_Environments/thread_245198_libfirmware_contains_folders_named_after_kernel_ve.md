---
title: "/lib/firmware contains folders named after kernel versions"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Vinze on 2006-08-27
Hey, I got some problems with my network card, and it searches for the firmware in /lib/firmware, but when I go to that folder I only see folders named after all the kernel versions I have installed. Is this normal?

---

### Post by lagagnon on 2006-08-27
Yes it is normal. Did you look inside the folders. There are a bunch of firmware binary files in there. If there is no firmware specific to your network card you may have to download the appropriate firmware from the manufacturer's website. You often then put the firmware onto a bootable floppy in order to re-flash your network card - assuming that is what you plan to do. Check out the appropriate cards website. You will of course need the EXACT model number. Look at the chipset number also.

---

### Post by Vinze on 2006-08-28
> **lagagnon said:**
> Yes it is normal. Did you look inside the folders. There are a bunch of firmware binary files in there. If there is no firmware specific to your network card you may have to download the appropriate firmware from the manufacturer's website. You often then put the firmware onto a bootable floppy in order to re-flash your network card - assuming that is what you plan to do. Check out the appropriate cards website. You will of course need the EXACT model number. Look at the chipset number also.

OK, but if it's normal, why does it look for the firmware in /lib/firmware/acx ? Is there a way to correct this?

---

