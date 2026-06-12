---
title: "Regarding the kernel"
date: 2009-06-08
forum: General Help
---

### Post by dinkyverma279 on 2009-06-08
Hi guys,
 
I have installed the linux kernel 2.6.27.18-custom. Now I want to install the kernel version 2.6.10. I have taken the kernel source version 2.6.10 and i am using ubuntu linux. 
Now when i am trying make menuconfig for 2.6.10 kernel version, I am getting following problem:
 
Setting up menu (2.1.40ubuntu1) ...
 
Processing triggers for menu ...
root@xw0-1:/usr/src/linux-2.6.10# make menuconfig
scripts/kconfig/mconf arch/i386/Kconfig
#
# using defaults found in .config
#
' invalid for LOG_BUF_SHIFT7
make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2
 
The other question is if i use make mrproper and then start using make menuconfig, it will open the configuration window, now when i opening existing .config file, I am getting the same problem. Can anybody tell the work around for this.
 
Since /boot directory config file is 2.6.27.18, since the kernel version 2.6.27.18 is already installed, now to compile a 2.6.10 kernel, what changes need to be done in ubuntu linux?
 
Regards.
Dinky

---

### Post by Lampi on 2009-06-08
2.6.10 ... sounds old to me - why the particular interest in such an old kernel? I'm not sure you can build this one out of the box, mainly because there have been *major* code changes from 2.6.10 up to 2.6.27.

There are tons of howtos on how to build an ubuntu kernel in the forum and in the ubuntu wiki, but I recommend to downgrade the kernel to a more recent edition - better stick with a 2.6.20 generation kernel

---

