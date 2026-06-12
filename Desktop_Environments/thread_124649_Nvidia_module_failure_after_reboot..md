---
title: "Nvidia module failure after reboot."
date: 2006-02-01
forum: Desktop Environments
---

### Post by terrax on 2006-02-01
Hey there.

I just installed kubuntu today. And  must say, im rather suprised of the easy configuration.

I moved from gentoo, and Im still a gentoo fan. But kubuntu seems very good too.

I just got one problem. I have followed the guide to install the latest nvidia driver. It installs fine and all, BUT?

After every reboot I have to reinstall the nvidia driver from nvidias bin packages, to get the xserver starting up?

I get this error after every reboot.:

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:

What is kubuntu doing at the boot, which make the modules fail? :S

---

### Post by vnbuddy2002 on 2006-02-01
Try the following step(s), I hope it will help you solve the problem.
1. edit /etc/modules, make sure the 'nvidia' module is in the list, add if not.
2. remove all the kernel module
    rm /lib/linux-restricted-modules/`uname -r`/nvidia*
    rm  /lib/modules/`uname -r`/kernel/drivers/video/nvidia*
3. Try to recompile the nvidia driver again + reboot!
----------

---

### Post by terrax on 2006-02-01
Yeah thx. It helped :) I have actually just doing it, right before I saw your reply.

It was som old nvidia-drivers, which "blocked" the newer drivers. But thx anyway.

---

