---
title: "Kernel 2.6.15-26 Update Broke USB Storage"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Avian00 on 2006-07-14
Am I the only one who's experienced this?  When I boot into the recently updated 2.6.15-26 Kernel, my USB storage devices fail to mount.  If I tail -f /var/log/messages, I just see a bunch of attempts to assign it a device ID, but it fails to mount.  Other USB peripherals work fine.  It's just USB storage devices.  When I boot into the previous Kernel (2.6.15-25), everthing is fine again.  I'll continue to use this Kernel for now.  Does anybody know what causes this?  I hope it is resolved in the next update.  Is there an official way I can report this bug?  Thanks!

Matt

---

### Post by fragos on 2006-07-14
I haven't had that problem with the kernel update.  To double check I tried an SD card in a USB reader which worked fine.

---

### Post by Avian00 on 2006-07-14
Perhaps, then, it could be related to a specific USB host chipset?  Mine is a VIA VT82xxxxx (that's what Device Manager reports) host controller.  Is yours different than that?

---

### Post by Gentist on 2006-07-15
I appear to have the same problem, and I also have a VIA chipset.

---

### Post by Gentist on 2006-07-16
I searched through the forums and found a similar (though not exactly the same) error. Removing the ehci_hcd module ("modprobe -r ehci_hcd") seems to be a temporary fix. I'm not sure why it works when it's removed though. Must be interfering with some part of the process.

---

