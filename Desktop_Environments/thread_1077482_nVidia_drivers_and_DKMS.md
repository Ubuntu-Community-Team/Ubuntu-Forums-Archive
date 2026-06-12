---
title: "nVidia drivers and DKMS"
date: 2009-02-22
forum: Desktop Environments
---

### Post by Pablo Pablovski on 2009-02-22
Hey, all.
Running Kubuntu Intrepid, nVidia GTS8800, with 180.29 drivers. 

I recently installed the latest nVidia closed source driver, 180.29, and all is working well on my current kernel, 2.6.27.11-generic.

However, I was recently prompted to upgrade the kernel to version .12. I did so, but I dumbly elected to preserve the current Grub menu.list, and when I rebooted I was in low graphics mode. Eventually, I uninstalled the new kernel and have been booting happily from .11. I'd like to resolve the issue with the .12 kernel + the nVidia driver.

Some investigation indicates that an error message appears when I try to boot with .12. Something about "AUTOINSTALL not set to yes in DKMS.comf" appears at the nVidia section of the DKMS process. I imagine that might explain the booting problem - I believe DKMS is the automagic tool that updates the drivers / kernels when there's a change like this.

Not quite sure what to do now, or what order to do stuff in - should I uninstall / re-install the nVidia driver, then the kernel, or the other way around?

I've uninstalled the .12 kernel, so would need to re-install it to try any fix (not sure what packages I should install).

Any help / pointers / advice gratefully received!

TIA,
PP

---

### Post by Pablo Pablovski on 2009-03-05
Shameless Bump....

I tried upgrading to .13, with the same result, so I restored from backup to .11. 

I then tried installing nvidia-glx from Synaptic, which seemed to work - a DKMS process ran as the driver installed, and it compiled the module and completed ok. 

However, the system booted into low graphics mode. I tried the XFIX thing from the recovery console, and got it up and running (tho compiz then didn't work).

Anyone got any magic bullets? For kubuntu, not me... yet.

PP

---

### Post by QNo on 2009-03-05
I had some different, but perhaps similar problems with nVidia drivers. I tried an uninstall of all nvidia related packages and a reinstall of linux-restricted-modules-generic. After that, i used the automatic restricted driver installation, and everything worked fine here. Perhaps that might help you, too.

---

### Post by Pablo Pablovski on 2009-03-05
Thanks, QNo - I'll give that a go.

---

### Post by Pablo Pablovski on 2009-03-07
OK, cracked it (finally!).

I needed to manually re-compile the new kernel module for the nVidia driver. I didn't know how to do that, but a bit of research on here indicated that the answer was to boot to recovery mode, cd to the location of the nVidia driver installer and run:

```
sudo sh NVIDIA-Linux-x86-180.29.pkg1.run -K
```

Previously, in my ignorance, I'd missed the -K switch, so was simply re-copying the driver on top of itself. 

Reboot, and hey presto, kernel version 2.6.27.13-generic with nVidia 180.29 driver, Compiz etc. all running. 

So, the process is:
1. install new kernel, include headers and source packages
2. boot to recovery prompt (or Ctrl-Alt-F1 to user prompt, then stop gdm / kdm)
3. compile new kernel module are described above
4. reboot

I've learnt something here. Mostly, it's don't faff about with kernels...

Phew...

PP

---

### Post by Speed Demon on 2009-03-07
I did that in Hardy..... took me 3 days to figure it out. Eventually I removed the nVidia one and installed Ubuntu's nVidia =)

---

