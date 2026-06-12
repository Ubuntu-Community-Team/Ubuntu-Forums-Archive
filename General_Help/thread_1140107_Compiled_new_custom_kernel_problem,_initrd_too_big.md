---
title: "Compiled new custom kernel problem, initrd too big."
date: 2009-04-27
forum: General Help
---

### Post by ThaddeusW on 2009-04-27
Hello everyone,

I just compiled a new kernel using the latest 2.6.30 kernel source from kernel.org [using this tutorial]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild"). The compile process went off without a hitch, rebooted and rebuilt my nvidia driver without a problem. But when I attempted to upgrade my system (using apt-get upgrade) I ran out of space on my boot partition and the upgrade exited on error. Upon checking the contents of /boot I found that my custom initrd is 52 megs in size! I was previously using the generic 2.6.24 Ubuntu kernel which has an initrd of only 8MB in size. My custom kernel image is only about 2.4MB in size.

If anyone is wondering why I chose to install a custom kernel, it was simply because I wanted to compile my first custom kernel. I have always used the generic kernels but this time I wanted to build my own. I have a basic understand of how the kernel works and the initrd is an initial ram disk to help load modules and other kernel extras. I think I might have specified too many devices to load via modules during configuration. The device option list is quite large and often some devices leave me questioning their relevance. I wind up leaving the default option or hitting m for module.

Is there a command line option or tool to compile the kernel using only the current system hardware? I remember reading there was a way to use a config file of the current running system while running a generic kernel. You then use that config to auto configure the new custom kernel and then compile it without having to manually select each piece of hardware.

Thanks.

---

### Post by atomizer on 2009-04-27
there should be a config file in /boot.


Maybe [this debian tutorial]("http://www.falkotimme.com/howtos/debian_kernel2.6_compile/") will give you some help with configuring your custom kernel.

should be the same for ubuntu, as it is debian based.


Good luck compiling!!


PS: dont forget that some options are needed in the beginning of the bootprocess, so you DONT compile them as modules (like your primary ide controller)

---

