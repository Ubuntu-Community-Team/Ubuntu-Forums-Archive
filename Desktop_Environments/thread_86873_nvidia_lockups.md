---
title: "nvidia lockups"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Akita on 2005-11-06
Machine boots, shows nvidia logo, lets me log on via GUI. The second I try to log out, shut down, etc. I get a complete machine lockup (no keyboard, no mouse, can't ssh into the box, etc.). Pixelated background like you usually see when gdm is resetting. This didn't happen with the older nvidia binaries on Hoary and I don't have any problems with the nv drivers. Happens 100% with nvidia-glx on both generic 386 and K7 kernels (with restricted-386 and restricted-k7 respectively). Tried the legacy drivers to no avail, they won't even load. I've tried a few of the fixes mentioned here and there for curing issues with X lockups (commenting GLCore and DRI for instance) without success. Any ideas what else to try besides waiting for nvidia to come out with new drivers? :-)

Thanks

---

### Post by Xian on 2005-11-06
If it were my box I'd download the nVidia drivers from their website and install them locally by hand. This way you could find out for certain whether the problem is in how Ubuntu packaged the drivers or if it is a machine specific problem.

---

### Post by Akita on 2005-11-18
Same issue using the latest from nvidia :confused:

---

