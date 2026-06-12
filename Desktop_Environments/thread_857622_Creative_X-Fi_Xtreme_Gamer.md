---
title: "Creative X-Fi Xtreme Gamer"
date: 2008-07-12
forum: Desktop Environments
---

### Post by Idire on 2008-07-12
Right, so the reason why I stopped using Ubuntu before was the lack of support for my sound card (and my tv card wintv nova td - but thats a different matter)

I found a 32bit linux driver for my card here:

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

Attempted to install it and got this:

```

Installation is in progress. Please wait...


checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-16-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2

```

Any ideas, i'm proficient with computers but fairly novice at linux. (i tried to install as mentioned in the readme file but found no uninstaller/configurer in the directory)

Thanks for any help.

---

### Post by Idire on 2008-07-12
There shouldnt be a hardware issue as it all functions correctly on my other operating system. Windows Vista

---

### Post by jim_p on 2008-07-13
Make sure you have the build-essential, alsabase, linux-sound-base and the linux-headers- for your kernel packages installed. To get your kernel's name```
uname -r
```
For instance, the output of "uname -r" for me is "2.6.24-1-686", so i must grab linux-headers-2.6.24-1-686.

---

### Post by Idire on 2008-07-13
> **jim_p said:**
> Make sure you have the build-essential, alsabase, linux-sound-base and the linux-headers- for your kernel packages installed. To get your kernel's name```
uname -r
```
For instance, the output of "uname -r" for me is "2.6.24-1-686", so i must grab linux-image-2.6.24-1-686.

I have Ubuntu 8.02, would the kernal be different for each pc?

---

### Post by jim_p on 2008-07-13
> **Idire said:**
> I have Ubuntu 8.02, would the kernal be different for each pc?

I know I have the 2.6.24-1-686 kernel because I installed in on purpose!
Ubuntu has some 2.6.24-something by default.
To find yours, issue the "uname -r" command at a terminal.

---

### Post by Idire on 2008-07-13
> **jim_p said:**
> I know I have the 2.6.24-1-686 kernel because I installed in on purpose!
Ubuntu has some 2.6.24-something by default.
To find yours, issue the "uname -r" command at a terminal.

Then after finding the kernel, what do I do?

---

### Post by jim_p on 2008-07-23
Install the **build-essential, alsabase, linux-sound-base and linux-headers-(name of kernel from uname -r)** and re-run the installation procedure again.

Excuse me for the delay, but I was away from home

---

### Post by LightRaven on 2008-07-28
Did you get this to work?

---

### Post by vladk2k on 2008-08-04
I have an X-Fi XtremeMusic and it's the same
I already have builed-essential, linxu-headers-`uname -r`, alsa-base and linux-sound-base (also installed alsa-source) but to no avail
found drivers in /opt/Creative/XFiDrv_Linux_US-1.18/drivers, ./configure looks ok, ./make exists with "*** [all] Error 2"

make I should specify the "alsa include folder"? (which I don't know where to find it)

---

### Post by Idire on 2008-08-06
> **LightRaven said:**
> Did you get this to work?

Not yet, having not checked this thread, but i will try now.

---

### Post by Idire on 2008-08-06
No it didnt work

same error as before, I checked all the packages, they all were installed already

I reinstalled them all for good measure. (including the alsa)

although from the error log it looks like its not finding the alsa module, (which the package manager tells me exists)

```

Copyright (c) 2008 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================
Installation is in progress. Please wait...
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-16-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful
andrew@andrew-ubuntu:~/Desktop/temp/XFiDrv_Linux_US-1.18$ 

```

I have a 2.6 kernal, ubuntu 8.04

---

### Post by Idire on 2008-08-06
What i tried after that was:

sudo ./installer --with-alsainc=/usr/share/alsa-base

and

sudo ./installer --with-alsainc=/usr/share/alsa

these are the locations I found also installed in, the error is the same, with alsa not found

---

### Post by s3kt0r on 2008-08-06
i have a xfi platinum and also tried to install this driver, along with the steps already show in the thread, but also haven't got it to work. maybe because gcc version isn't the same from the one used to compile the kernel? 
thanks,

---

### Post by Siyfion on 2008-08-23
Im having the exact same problems as vladk2k... I have all the packages installed but get a make: *** [all] Error 2 and make: *** [install] Error 2 message!?

---

### Post by Stenrad on 2008-10-13
Hi all!

I have exactly the same card and followed this guide:-

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675")

Hope that helps!

All the best,
Stenrad.

---

