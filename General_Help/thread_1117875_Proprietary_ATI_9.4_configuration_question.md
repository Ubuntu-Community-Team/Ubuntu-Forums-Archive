---
title: "Proprietary ATI 9.4 configuration question"
date: 2009-04-06
forum: General Help
---

### Post by Didius Falco on 2009-04-06
I have just successfully installed the latest (v9.4) drivers from ATI. The ATI control loads and works, the Screen Resolution utility loads and works, videos look good, etc.

Just out of curiosity, I loaded up the Restricted Drivers utility, and it shows that the proprietary driver is not loaded.

I'm pretty sure this is because I'm using a driver beyond the one available on the Restricted Repository, so it won't even show up as loaded on that screen, but I thought I'd better get confirmation from users with a lot more experience (about ten days) than I have.

Is that the reason it isn't showing?

---

### Post by cariboo on 2009-04-06
System-->Administration-->Hardware Drivers, only show drivers that were installed from the repositories. The advantage of this is that every time there is a new driver, your system gets automatically updated, whereas if you install the driver manually, every time the kernel gets updated, you have to reinstall the driver.

Jim

---

### Post by Didius Falco on 2009-04-06
Thanks for the fast response and the information. For example, I was unaware that I'll need to reinstall the driver every time the kernel gets updated.

---

### Post by markbuntu on 2009-04-06
This problem is so common because many people do not remove old drivers or their kernel modules before installing a new driver so the kernel installer is confronted with more than one set of kernel modules and so to be safe it loads none of them. You will see a little message about that if you watch the terminal while the kernel is installing.

If you have no previous driver kernel modules installed then the kernel update should not cause any problem.

That said it is easy enough to recover from. Just boot into recovery mode and choose fix x or xfix, whatever, then continue. When you get to your desktop just reinstall the driver again and reboot. Takes less than 5 minutes.

FYI, ati is dropping support for anything previous to the HD2000 series cards after the 9.3 driver.

---

### Post by Didius Falco on 2009-04-06
> **markbuntu said:**
> This problem is so common because many people do not remove old drivers or their kernel modules before installing a new driver so the kernel installer is confronted with more than one set of kernel modules and so to be safe it loads none of them. You will see a little message about that if you watch the terminal while the kernel is installing.

If you have no previous driver kernel modules installed then the kernel update should not cause any problem.

That said it is easy enough to recover from. Just boot into recovery mode and choose fix x or xfix, whatever, then continue. When you get to your desktop just reinstall the driver again and reboot. Takes less than 5 minutes.

FYI, ati is dropping support for anything previous to the HD2000 series cards after the 9.3 driver.

All good to know. The dropped support shouldn't affect me for a while - I'm using an HD 4870.

I don't really want/need all the flashy desktop eye-candy, but I do want high quality video playback. 

BTW, I did uninstall the prior drivers, but I didn't purge them from the system, just in case the 9.4 drivers didn't work out.

Thanks all around for the advice and information.

---

