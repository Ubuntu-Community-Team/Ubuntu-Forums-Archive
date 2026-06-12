---
title: "Problem after latest update"
date: 2022-07-15
forum: Desktop Environments
---

### Post by Autodave on 2022-07-15
Xubuntu 20.04  Big update last night, problems today.  Everything *seems* to be running normally, but get these errors when booting:

---

### Post by TheFu on 2022-07-15
Did you disable BT in the BIOS yet?  That just a good practice for security reasons.  I've been hacked OVER bluetooth.

As for the nvidia stuff, whenever a new kernel is installed, if I don't see that dkms handles relinking the nvidia driver (it never does), then I just reinstall the current driver to force a re-link.

This week, there are some important kernel and Xorg patches.   

I vaguely remember seeing that the kernel patches had some issues and were pulled when some more testing revealed more issues.  They were trying to fix another kernel issue and broke some things. Don't recall the specific kernels impacted.  Think it was discovered in 5.19.x, but backported to a number of others. May you have patched when the not-so-great kernel was out for a day or so?  There's another 5.19 issue that was causing problems on AMD GPUs thanks to DRM - who wanted DRM again?

The xorg stuff was are remote root escalation if X11Forward is enabled over ssh.  I use that all the time ... actually, this browser window is using it, now.
[https://www.phoronix.com/scan.php?page=news_item&px=X.Org-July-12-Security](https://www.phoronix.com/scan.php?page=news_item&px=X.Org-July-12-Security)  CVE-2022-2319 and CVE-2022-2320

I patch once a week, usually on Saturday mornings.  More often seems to catch patch sets that might not be ready for prime time use.

---

### Post by Autodave on 2022-07-15
As I recall, 5.15 is my current kernel.  I will have to check that.  I did try booting to the older kernel, but no difference....same errors.  I also tried installing the newest nVidia driver....same thing.

---

