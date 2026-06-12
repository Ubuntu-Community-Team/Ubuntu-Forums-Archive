---
title: "update nukes wireless"
date: 2005-11-23
forum: Desktop Environments
---

### Post by bobterri on 2005-11-23
I updated kernel, acpi-support, etc. yesterday and when I rebooted I lost my wifi configuration.  I am using the linuxant wifi driver, which was working perfectly.  When i tried to download the driver and configure again, linuxant said it did not have a package for the kernel I was using, or something like that.

Anyone have any suggestions?  Maybe I should try to reverse the update (if that is possible).

---

### Post by bobterri on 2005-11-23
Well, maybe someone knows how to reverse updates?  Anyone?

---

### Post by termite on 2005-11-23
you don't need to reverse the update.  Go to Synaptic, search for madwifi and install whatever 'restricted' package corresponds to your new kernel.  Worked for me :)

---

### Post by bobterri on 2005-11-23
Thanks Termite, I'll give it a try and let you know how it goes.

---

### Post by bobterri on 2005-11-23
I went Synaptic and searched for madwifi.  I found that there were two linux-restricted-modules, 2.6.12.4-11.1 and 2.6.12.4-11.  Should there be two?

---

### Post by passcode on 2005-11-29
I also had the same problem, if you use 2.6.12.4-11 (the older one) and select the linux-image-2.6.12.9-386(also the older one). this should undo the update and fix your problem.

I do not know why this bug happend, and I still am looking for a solution that will alow me to use the updated kernel image. If I find any thing I will keep you posted.

P.S. you will have to reboot, and you do not need to remove linux-image-2.6.12-10 or the linux-restricted-modules-2.6.12-10 just select the older kernel from grub on boot

---

