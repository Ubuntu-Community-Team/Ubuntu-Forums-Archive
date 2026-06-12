---
title: "Update Manager wants to update to an OLDER Kernel"
date: 2011-01-05
forum: Desktop Environments
---

### Post by ozzman2 on 2011-01-05
Recently installed Ubuntu 10.04 on a SSD.

I manually installed kernel [2.6.33]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.5-lucid/") (to enable TRIM).  My update manager keeps notifying me that an older kernel (2.6.32-27) is available.

Why does it not realize I already have a newer kernel installed?  Is there a workaround to resolve this?  Is there a better way I could have installed 2.6.33 (or used a different kernel altogether)?

---

### Post by Frogs Hair on 2011-01-05
I think you simply have to ignore it and set updates to notify only . The update manager downloads the next kernel for the release you are using in order , it does not detect your kernel.

---

### Post by TechWiz2100 on 2011-01-05
> **Frogs Hair said:**
> I think you simply have to ignore it and set updates to notify only . The update manager downloads the next kernel for the release you are using in order , **it does not detect your kernel.**

Wouldn't that one hell of an oversight?

I'm pretty sure the update manager is supposed to be able to tell which kernel you are on if it was installed properly and it is listed as a valid kernel in the repos because some packages are kernel specific and APT tells you when you can't install packages due to kernel dependencies.

I had issues using certain packages on another APT using distro because that distro did not have a kernel made for my architecture and build failed sporadically on the machine.

---

### Post by ozzman2 on 2011-01-06
Maybe I can ask the question differently.

Can someone explain how this page works?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)


Why are revisions still being made to the older 2.6.32.xx-lucid kernals when the 2.6.33+ lucid kernels are there?

---

### Post by TechWiz2100 on 2011-01-06
Beta maybe? Those are probably the latest unstables and packageman likes using stables only unless otherwise noted/configured

---

### Post by mcduck on 2011-01-06
> **TechWiz2100 said:**
> Wouldn't that one hell of an oversight?

I'm pretty sure the update manager is supposed to be able to tell which kernel you are on if it was installed properly and it is listed as a valid kernel in the repos because some packages are kernel specific and APT tells you when you can't install packages due to kernel dependencies.

I had issues using certain packages on another APT using distro because that distro did not have a kernel made for my architecture and build failed sporadically on the machine.

The update manager can only tell package versions for things that are actually installed through the package management.

Also, kernel updates are actually not a case of updating a kernel package, so it doesn't check what lernels you have installed and what you might be running. The mechanism is actually a lot simpler:

You have a metapackage called "linux-generic" installed. This is an empty package which has the latest official kernel version and related packages marked as it's dependencies. It's also the only package that is actually *updated* in kernel updates, the update installs latest version of this metapackage, causing the latest kernel packages to be *added* to your system as dependencies. (it must be done this way, otherwise it wouldn't be possible to keep the old kernel version installed, as updating a package always replaces the old one.)

So, if you want to use a custom kernel instead of the official one, and don't wish to install the official kernel updates any more, all you need to do is to remove the kernel-related metapackages.

---

### Post by Frogs Hair on 2011-01-06
Thanks mcduck !

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

