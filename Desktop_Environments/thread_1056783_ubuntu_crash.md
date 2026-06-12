---
title: "ubuntu crash"
date: 2009-02-01
forum: Desktop Environments
---

### Post by MPX11 on 2009-02-01
after having several applications running ubuntu 8.10 crashed, when I rebooted the desktop was black but everything else seems to be working fine, except for the desktop folders that have disappeared, now I cannot create any folders in the desktop,  I have 6 days with ubuntu and the more I get into it, the more problems arise, could anybody help me get my folders back or re-installation is my only hope.
Ps. I got my background back, but the folder creation is missing.

---

### Post by TenPlus1 on 2009-02-01
It sounds like a problem with Nautilus, you could try going into the Synaptic Package Manager and re-installing it again to make sure...

---

### Post by MPX11 on 2009-02-01
> **TenPlus1 said:**
> It sounds like a problem with Nautilus, you could try going into the Synaptic Package Manager and re-installing it again to make sure...

thank you for your help, but when I went to the SPM and reinstall the Nautilus packages it will go and install the packages successfully but when I closed the installation window the Nautilus will be grey out, and the package will not installed, I did this a couple of times, then after searching i found this:
"Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter"
 this has definitely fixed the problem.

---

