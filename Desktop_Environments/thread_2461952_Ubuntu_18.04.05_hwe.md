---
title: "Ubuntu 18.04.05 hwe"
date: 2021-05-10
forum: Desktop Environments
---

### Post by giobaxx on 2021-05-10
We tried to undestand the instability of some out the ubuntu-desktop installed and one of my collegue told to check id have enabled the HWE Kernel. I've never delved into the kernel topic but maybe is the time to do it

We are using the Ubuntu 18.04.5 that also seems to have the HWE stack enabled by default and trying  to get some information  from what i have understood  the HWE Kernel is installed by default since UBUNTU 18.04.2. It correct or I'm Wrong?

If what i said it is true, can we downgrade an ubuntu desktop installed with the the Ubuntu 18.04.5 ISO to the GA kernel ?

Thanks for the help

---

### Post by mikewhatever on 2021-05-10
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver)

You are welcome. :~)

---

### Post by Bashing-om on 2021-05-10
giobaxx - Hello :D

Yes: You have the right of the enablement.
> 
 The Ubuntu LTS enablement stacks provide newer kernel and X support for existing LTS releases, see 
               [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)


And yes one may revert back to the GA kernel
```

sudo apt install --install-recommends linux-generic xserver-xorg-core xserver-xorg xserver-xorg-video-all xserver-xorg-input-all libwayland-egl1-mesa

```
Then the cleanup:
```

sudo apt purge linux-generic-lts-bionic xserver-xorg-core-lts-bionic xserver-xorg-lts-bionic  xserver-xorg-video-all-lts-bionic xserver-xorg-input-all-lts-bionic libwayland-egl1-mesa-lts-bionic

```

[INDENT]my bit to try and help
[/INDENT]

ninja'd ^^ :D

---

### Post by guiverc on 2021-05-10
FYI:   You can have both GA & HWE stacks installed too.

It'll mean you have more packages that will need updating, more disk space used.. all you need to not do the the `purge` step, and you have more options in the "*Advanced Options for Ubunt*u"  (having both HWE or GA kernel options available) but I've found it helpful on some boxes when *testing* issues on other boxes (some older thinkpads didn't like the 5.4 HWE kernel for *bionic*).

FYI: Your installation media controlled if GA was the default (18.04, & 18.04.1 media defaulted to the GA stack; 18.04.2 & later media defaults to HWE for *bionic*); though of course it could be changed post-install.

- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by grahammechanical on 2021-05-11
Here is the link to the support that Ubuntu developers give to each series of kernels

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

When Ubuntu 18.04.0 was released it came with the 4.15 kernel which would be supported for five years until April 2023. The kernel in 20.04.1 would also be supported until April 2023. Those who then upgrade to 18.04.2 would get less support for the kernel in that version and would need to continue upgrading through to 18.04.5 to get continued kernel support.

Your systems are on 18.04.5. The kernels are supported until April 2023.  When we move on to the Hardware Enablement stack we get the advantage of  newer/upgraded hardware drivers (firmware) that come from the Linux  developers. Which would be needed if we were purchasing hardware that  came on the market after 18.04 was first released.

The same situation applies to those of us using 20.04. If we kept to 20.04.0 or 20.04.1 the kernel gets the full life time support. But the firmware (drivers) does not get upgraded for newer hardware. If we progress beyond 20.04.1 we need to keep upgrading through to 20.04.5. 

If you hardware dates to before 2018 then this reversion might be useful but on hardware that is newer than 2018 you might experience problems due to not having the drivers (firmware) for the newer hardware.

Ubuntu has these point releases so that Ubuntu will work on hardware that comes on the market after the Long Term Support version of Ubuntu was released.

Regards

---

