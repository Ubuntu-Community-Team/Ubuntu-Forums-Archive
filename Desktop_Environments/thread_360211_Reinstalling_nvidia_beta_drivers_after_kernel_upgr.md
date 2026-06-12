---
title: "Reinstalling nvidia beta drivers after kernel upgrade"
date: 2007-02-12
forum: Desktop Environments
---

### Post by coolen on 2007-02-12
I just upgraded my kernel, and I know this has been heard before, but after the upgrade the binary nvidia driver did not work.
There was a very nice looking program called Envy which would fix the problem by setting up a new driver, but it gets the latest stable driver...I use the beta driver for AIGLX, and would like to keep it as such.
Anyway, I went into Synaptic, and found an update for linux-restricted-modules. It didn't come up in Update Manager, though (if I understand the APT package naming scheme correctly, package names and version numbers are usually separated by a '_', so I think it's just recognising them as different packages).
So, my question is, would this fix my problem? The nvidia-glx package doesn't list either of these packages as a dependancy, although they all depend on linux-restricted-modules-common, so my thinking is the kernel needs the new version specific to it.
I'm no expert, of course. This is just what makes sense to me, but I often find that what makes sense to me just isn't the case (Vista's DRM doesn't bother you? Whaaaa?!). Please, tell me if I'm way off.

---

### Post by shareMenaPeace on 2007-02-12
You could install envy from here
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Login with the older kernel from the GRUB boot loader than once you logged in download and install envy.

Relog with the new kernel and after the xserver breaks login to the console and run "envy".

---

### Post by newsledbans on 2007-02-13
Is the envy download hosted anywhere else?  I keep getting an internal server error when trying to download it.

---

### Post by shareMenaPeace on 2007-02-13
Works 
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

---

