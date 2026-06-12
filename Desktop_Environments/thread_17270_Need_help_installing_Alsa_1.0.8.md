---
title: "Need help installing Alsa 1.0.8"
date: 2005-02-27
forum: Desktop Environments
---

### Post by Tiede on 2005-02-27
OK. I have a SoundBalster 64 soundcard, and I cannot seem to have sound working on it. I tried [ a lot of differents ways ]( http://ubuntuforums.org/showthread.php?t=1805), but none seems to be working. Hence, I decided to upgrade to 1.0.8...(I have 0.9)
However, installation never gets completed, and this is what happens:

```

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 #

```

does anyone know why it is displaying those errors? Help is greatly appreciated.

---

### Post by macewan on 2005-02-27
[QUOTE=Tiede]OK. I have a SoundBalster 64 soundcard, and I cannot seem to have sound working on it. I tried [ a lot of differents ways ]( http://ubuntuforums.org/showthread.php?t=1805), but none seems to be working. Hence, I decided to upgrade to 1.0.8...(I have 0.9)
However, installation never gets completed, and this is what happens:

```

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 #

```

does anyone know why it is displaying those errors? Help is greatly appreciated.[/QUOTE]


sudo apt-get install gcc

---

### Post by Tiede on 2005-02-28
Thanks for the reply macewan
I still crashed at yet another wall though
with appropirate kernel adress and all
```


checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.
root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 #


```

This is what happened after I installed gcc (BTW I tought I installed it before, just forgot I did a fresh install after that, hence my previous post ;)  )

Last time I tried uninstaling alsa, it crashed the GDM, and I only had the command line to work with. Is there a way to stop the detection of alsa without uninstalling it, or uninstall it without affecting GDM

---

### Post by Tiede on 2005-03-01
Ok... I uninstalled Alsa 0.9 and squeezed in 1.0.8 (without restarting in fear of losing the GDM once again)

GDM restart after reinstalling alsa without problems (fieuhhhh!) :)

Yet, as always, one other birck wall just came up. Here is the messages I got during install, it is long, but I tought it might help to give it here:

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure --with-kernel=/usr/include/linux
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/include/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/include/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
Creating a dummy <linux/compiler.h>...
checking for kernel linux/pm.h... "no"
Creating a dummy <linux/pm.h>...
checking for kernel linux/spinlock.h... "no"
Creating a dummy <linux/spinlock.h>...
checking for kernel linux/irq.h... "no"
Creating a dummy <linux/irq.h>...
checking for kernel linux/threads.h... "no"
Creating a dummy <linux/threads.h>...
checking for kernel linux/rwsem.h... "no"
Creating a dummy <linux/rwsem.h>...
checking for kernel linux/gameport.h... "no"
Creating a dummy <linux/gameport.h>...
checking for kernel linux/devfs_fs_kernel.h... "no"
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... "no"
Creating a dummy <linux/highmem.h>...
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
Creating <linux/adb.h>...
checking for kernel linux/cuda.h... "no"
Creating <linux/cuda.h>...
checking for kernel linux/pmu.h... "no"
Creating <linux/pmu.h>...
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
Creating <linux/firmware.h>...
checking for exported symbol dump_stack... grep: /usr/include/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
Symlinking <linux/isapnp.h>...
checking for driver version... 1.0.8
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h

---

### Post by Tiede on 2005-03-01
Ok... I uninstalled Alsa 0.9 and squeezed in 1.0.8 (without restarting in fear of losing the GDM once again)

GDM restart after reinstalling alsa without problems (fieuhhhh!) :)

Yet, as always, one other birck wall just came up. Here is the messages I got during install, it is long, but I tought it might help to give it here:

root@Linuxed:/usr/src/alsa/alsa-driver-1.0.8 # ./configure --with-kernel=/usr/include/linux
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/include/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/include/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
Creating a dummy <linux/compiler.h>...
checking for kernel linux/pm.h... "no"
Creating a dummy <linux/pm.h>...
checking for kernel linux/spinlock.h... "no"
Creating a dummy <linux/spinlock.h>...
checking for kernel linux/irq.h... "no"
Creating a dummy <linux/irq.h>...
checking for kernel linux/threads.h... "no"
Creating a dummy <linux/threads.h>...
checking for kernel linux/rwsem.h... "no"
Creating a dummy <linux/rwsem.h>...
checking for kernel linux/gameport.h... "no"
Creating a dummy <linux/gameport.h>...
checking for kernel linux/devfs_fs_kernel.h... "no"
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... "no"
Creating a dummy <linux/highmem.h>...
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
Creating <linux/adb.h>...
checking for kernel linux/cuda.h... "no"
Creating <linux/cuda.h>...
checking for kernel linux/pmu.h... "no"
Creating <linux/pmu.h>...
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
Creating <linux/firmware.h>...
checking for exported symbol dump_stack... grep: /usr/include/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
Symlinking <linux/isapnp.h>...
checking for driver version... 1.0.8
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h


Is there something I am missing???

---

### Post by Tiede on 2005-03-02
here is the uotput of ls -al /usr/src
There is nothing about alsa in it... Is this normal
```

marc@Linuxed:~ $ ls -al /usr/src
total 12
drwxrwsr-x    3 root     src          4096 2005-03-02 04:26 .
drwxr-xr-x   12 root     root         4096 2005-03-02 03:05 ..
drwxr-xr-x    7 root     root         4096 2005-03-02 04:26 rpm
marc@Linuxed:~ $

```

EDIT: I found that command [ over there. ](http://ubuntuforums.org/showthread.php?t=6101&page=1&pp=10)

---

### Post by CookieNinja on 2005-03-11
The problem is the lack of kernel source or header files of the kernel being uesd.

It is also CRITICAL that the version of gcc used to compile the kernel is also used to compile ALSA. It will compile anyway, but the drivers won't work if you fail to do this.

---

### Post by Tiede on 2005-03-11
Thanks for the reply. Unfortunately, me BIG newbie to ubuntu and would need a guide on how to do this :)

BTW, I just installed KDE, do you think OSS might work (Last time I tried using Gnome it gave me a bunch of errors)...

---

### Post by CookieNinja on 2005-03-12
[QUOTE=Tiede]Thanks for the reply. Unfortunately, me BIG newbie to ubuntu and would need a guide on how to do this :)

BTW, I just installed KDE, do you think OSS might work (Last time I tried using Gnome it gave me a bunch of errors)...[/QUOTE]
 I think the drivers are critical for all the desktop environments.

Look in /boot/ and see what version of the kernel you have there. Then go to synaptic package manager and search there using the word header. you need to install something called kernel-headers-2.x.x.x  The numbers on the end should exactly reflect those on the end of some of the files inside /boot/ in order the work.

This line is also important:

checking for GCC version... Kernel compiler: Used compiler: gcc (GCC) 3.3.4 (Debian 1:3.3.4-9ubuntu5)

It says there that the compiler you are using is gcc v3.3.4. Once you have those kernel headers there will be a gcc version stated between "kernel compiler:" and "Used compiler". The kernel compiler and used compiler MUST be the same version.

For instructions on all the parts of ALSA you need to compile, look here, but don't go beyond the line that says "Now onto step 4." as the rest doesn't necessarily apply to ubuntu. Getting this far, without errors, means that ALSA has been compiled and installed suscessfully. There's more to do, but I'll stop there for now.

[http://fedoraforum.org/forum/showthread.php?p=204714](http://fedoraforum.org/forum/showthread.php?p=204714)

You might want to try restarting Ubuntu, and running alsamixer from the shell to see if it sees the soundcard and shows you volume controls. My memories on what I did after the above steps has faded a bit. I'll endevour to check over what I did and help you more if you need help beyond this point. I'm away for a week or so, though, so don't expect a reply TOO quickly . Maybe someone else will step in or it might just be working at this point.

The following might need adding to /etc/modprobe.d/alsa-base. I am not 100% but it seems to be in mine and that guide for fedora says to add the exact same to /etc/modprobe.conf in their distro. Mine has a lot more in there besides this, so I could be wrong about it's necessity. I did a lot of fiddling to get my card working, so (aside from the compile help above) I have lost track of what helped and what didn't :( None of what I did could cause any harm though, and I have it working on fedora and ubuntu, so i wasn't doing badly :)

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-emu10k1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

---

### Post by Tiede on 2005-03-14
Thanks again for replying.
unfirtunately, when I look in /boot/ I hae different ones...
here a the name of the files. Perhaps soemeone can figure out which one is the right one.
```

marc@Linuxed:~ $ dir /boot
config-2.6.8.1-3-386
config-2.6.8.1-5-386
grub
initrd.img-2.6.8.1-3-386
initrd.img-2.6.8.1-5-386
memtest86+.bin
System.map-2.6.8.1-3-386
System.map-2.6.8.1-5-386
vmlinuz-2.6.8.1-3-386
vmlinuz-2.6.8.1-5-386
marc@Linuxed:~ $

```

Is this even normal???
PS: Also, when I look in Synaptic, there is only one version of the kernel-headers available for 386, and it always depends on the leatest available, in other words I can only select:
kernel-headers-2.6.7-1-386
I selected it, and when I tried running ./configure, it gives me a **LOT** of errors...
What should I do next?
(Any help appreciated while I await the return of CookieNinja :) )

---

### Post by CookieNinja on 2005-03-20
[QUOTE=Tiede]Thanks again for replying.
unfirtunately, when I look in /boot/ I hae different ones...
here a the name of the files. Perhaps soemeone can figure out which one is the right one.
```

marc@Linuxed:~ $ dir /boot
config-2.6.8.1-3-386
config-2.6.8.1-5-386
grub
initrd.img-2.6.8.1-3-386
initrd.img-2.6.8.1-5-386
memtest86+.bin
System.map-2.6.8.1-3-386
System.map-2.6.8.1-5-386
vmlinuz-2.6.8.1-3-386
vmlinuz-2.6.8.1-5-386
marc@Linuxed:~ $

```

Is this even normal???
PS: Also, when I look in Synaptic, there is only one version of the kernel-headers available for 386, and it always depends on the leatest available, in other words I can only select:
kernel-headers-2.6.7-1-386
I selected it, and when I tried running ./configure, it gives me a **LOT** of errors...
What should I do next?
(Any help appreciated while I await the return of CookieNinja :) )[/QUOTE]
 Have a look in synaptic now, i can see the kernel headers you need in there :)

I'm going to download them now and keep them for you in case you have problems. You shouldn't ... but just playing safe.

---

### Post by Tiede on 2005-03-21
'Come Back CookieNinja,
Since  I cannot find the headers I need in Synaptic, I was thinking of actually downloading them directly from ftp, and istannl manually... Do you think it is a good idea, or is it too unwise?
Also, Since I installed KDE, I was thinking of actually trying OpenSound once more... (Last time I tried, it gave a a bunch of KDE-related errors...
I also want to add that I replaced ESD with polypaudio, and I there was no noticeable change in the computer...]
I recently did a dist-upgrade, did not do nothing than fill up my dire and put two other options in the grub menu on start-up... No sound from alsa, no alsaconf either.
To finish, just saying that I am now willing to make a full system reboot if it is what it takes too have sound... So if you know of a good way that might not work if someone already messed with the system, don't hesitate :)

And thanks again for your suggestions.

---

### Post by CookieNinja on 2005-03-22
[QUOTE=Tiede]'Come Back CookieNinja,
Since  I cannot find the headers I need in Synaptic, I was thinking of actually downloading them directly from ftp, and istannl manually... Do you think it is a good idea, or is it too unwise?
Also, Since I installed KDE, I was thinking of actually trying OpenSound once more... (Last time I tried, it gave a a bunch of KDE-related errors...
I also want to add that I replaced ESD with polypaudio, and I there was no noticeable change in the computer...]
I recently did a dist-upgrade, did not do nothing than fill up my dire and put two other options in the grub menu on start-up... No sound from alsa, no alsaconf either.
To finish, just saying that I am now willing to make a full system reboot if it is what it takes too have sound... So if you know of a good way that might not work if someone already messed with the system, don't hesitate :)

And thanks again for your suggestions.[/QUOTE]
 Which Ubuntu have you got installed horay henry or the previous one?

The reason I am asking is twofold:

1. I don't get why you still cannot see the kernel headers I can see that you need.

2. Since I have been away there is a new ALSA update, which I have been hesitant to install in case it is not the very latest one which I need.

There's one more option before resorting to 3rd party sources, I will get you to check the sources you are using for synaptic & compare with what you have. Before doing that, though, I am interested which ubuntu you are using. There's probably not a problem with using a 3rd party source, but we should be able to crack it without resorting to that.

---

### Post by Tiede on 2005-04-28
Hmmm... This started to sound a little too fishy...
But don't worry, I figured out how to make the Sound Card working this morning.
(And I love the Ubuntu Sounds) :)
For explanation purposes, in case anyone else has problem with SB and is installing alsa only for this purpose, [ here is the link to the post with the fix. ](http://ubuntuforums.org/showthread.php?p=151549#post151549)

Oh, by the way, the final version of ALSA I am staying with is 0.9
In case someone was wondering.

---

