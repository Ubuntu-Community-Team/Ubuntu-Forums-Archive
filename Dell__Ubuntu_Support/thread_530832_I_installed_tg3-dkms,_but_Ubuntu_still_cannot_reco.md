---
title: "I installed tg3-dkms, but Ubuntu still cannot recognize my broadcom network controlle"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by JangMunho on 2007-08-20
That's strange.
This is the second time that I installed Ubuntu on my laptop- inspiron 1420, just because MD3 distroyed my partition table. Last time I installed Ubuntu, the network controller could not recognize my network controller, then I installed dkms and tg3-dkms, the broadcom ethernet worked perfectly.But this time, I still use that packages, still that method, still that commands, but the ethernet seems still using the incorrect driver.
I reinstalled tg3-dkms several times, eveytime the terminal told me the installation accomplished successfully. But, the ethernet controller won't work at all.

Last time, before I installed tg3-dkms, the LED light on the network interface was always on, this meant that tha system was using a incorrect driver. But after I installed tg3-dkms, the light was off, then I tried "modprobe tg3", it worked. This time, even after the installation, the light was still on, tg3-dkms didn't stop the incorrect driver in the kernel, and everytime when system boots, the incorrect driver is loaded automatically. I redownloaded the packages, and reinstalled, but no effect at all.

Hi, guys, I'm tired out now. Do you know, tommorrow I'll go to the university, and must take the laptop, I must solve the problem today, but the god seems playing a trick on me...

Please, please, please help me! Thank you!!

---

### Post by JangMunho on 2007-08-21
The problem solved...
I tried "modprobe -r tg3" and then again "modprobe tg3", the ethernet controller worked, but after reboot, it became invalid again.
Then I tried "dpkg-reconfigure --all", this command solved the problem, though it made me wait for such a long time...

---

### Post by plehman on 2007-08-22
Thanks for posting the fix you found.  I was having similar problems on my Vostro 1400 and your solution to  re-modprobe the driver and reconfigure dpkg worked for me as well.

Thanks again.

---

