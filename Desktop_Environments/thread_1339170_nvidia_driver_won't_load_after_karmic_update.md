---
title: "nvidia driver won't load after karmic update"
date: 2009-11-27
forum: Desktop Environments
---

### Post by smaring on 2009-11-27
I updated my Karmic laptop (with a dist-upgrade) and now X won't load and I get dropped to a console login that just flashes the screen at me and will only recognize about every 10th character I try typing.

After entering a chroot on a the 64-bit Karmic LiveCD and see the following in the logs ...

```
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```

I have tried to reinstall via the NVIDIA-Linux-x86_64-190.42-pkg2.run
It claims that the install went fine, but the same problem persists.

I think the flickering coincides with syslog getting filled up with these ...

```
Nov 26 09:55:14 lappy acpid: client 10901[0:0] has disconnected
Nov 26 09:55:14 lappy acpid: client connected from 10906[0:0]
Nov 26 09:55:14 lappy gdm-binary[10891]: WARNING: GdmDisplay: display lasted 0.085487 seconds
Nov 26 09:55:14 lappy gdm-simple-slave[10910]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
```

This bug seems somewhat related [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928)

there is no custom.conf in my /etc/gdm dir


-Steve Maring

---

### Post by smaring on 2009-11-27
another strange finding is that from within the chroot on the LiveCD I can "modprobe nvidia" and the module successfully loads.

---

### Post by smaring on 2009-11-27
well ... it looks like I originally installed the nvidia driver against kernel 2.6.31-14-generic and the update I did brought in 2.6.31-15-generic which is what killed the module.  I'm assuming that the installation compiles itself against the currently running kernel, and that is why recompiling from the LiveCD, which was running 2.6.31-14-generic, didn't help trying to load it in the new 2.6.31-15-generic kernel.

Once I RTFMed about holding down the Shift key to bring up the menu on boot with the new Grub 2, I selected the 2.6.31-14-generic kernel to boot and everything came up fine.

I there perhaps a fail-safe driver I could drop in my Xorg.conf to get the 2.6.31-15-generic kernel booted so that I can reinstall my nvidia driver against that?  I don't have the original backup to my Xorg.conf.

---

### Post by Shazaam on 2009-11-27
2 ways...
1. When grub2 boots select the new kernel recovery line and hit "e". Remove "quiet splash" from the end and add vga=771 then hit CTRL+X to boot. You should get to a screen with choices, scroll to the bottom and choose to drop to a prompt. When you get the prompt enter "login", go ahead and log in. Then cd to the driver location and run it. Choose "NO" at the warning, "Yes" to update xorg. Reboot.
2. (I don't know if this works) Edit xorg.conf (if you have one) and change the driver line from "nvidia" to "nv" and reboot. Then install the driver.

You will have to do it again on every subsequent kernel update.

---

