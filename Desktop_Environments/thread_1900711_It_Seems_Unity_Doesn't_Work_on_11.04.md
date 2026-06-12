---
title: "It Seems Unity Doesn't Work on 11.04"
date: 2011-12-27
forum: Desktop Environments
---

### Post by Souljah on 2011-12-27
Hi,

I recently installed ubuntu 11.04 (don't want to upgrade to 11.10 yet) and my GRUB boot menu screen as well as the boot up process appears to be not working. The grub boot menu appears to have a purple tinge to it, not the normal grub interface. When selecting ubuntu, it just stays on a blank screen with a purple like tinge. If I go into recovery mode and choose failsafe graphics mode, it works. What would be the issue here and how would I go about rectifying this?

My system setup is AMD BE 2350, ATI HD 6670, 3 GB of RAM.

---

### Post by 3Miro on 2011-12-27
I would think that ATI 6xxx should work fine with the default driver, but I guess not in your case. Try going to Additional Drivers (System->Admin in the classic menu) and then activate the proprietary ATI driver.

If it is a driver issue, 11.10 **may** work much better as it comes with newer drivers.

---

### Post by 2F4U on 2011-12-27
It works in failsafe mode probably because this mode adds nomodeset to the grub kernel parameters. You can try the same for your usual grub menu entry.

---

### Post by grahammechanical on 2011-12-27
It could also be a break in one of the wires making up the monitor cable. I had something similar on a CRT monitor some years ago. I was able to bypass the broken wire with another wire and I could continue using the monitor until it finally failed in some other way that I could work around.

Regards.

---

