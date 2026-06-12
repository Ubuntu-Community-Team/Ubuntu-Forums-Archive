---
title: "KDE problems (automount, hibernate) after kernel upgrade"
date: 2007-10-15
forum: Desktop Environments
---

### Post by vob on 2007-10-15
Dear all,

Short problem version:

after an upgrade to the recent gutsy kernel I am having troubles with KDE: autodetection of USB devices no longer works, and the 'hibernate' entry in my klaptop panel entry is gone. Manually mounting USB devices is still possible, and manually hibernating the laptop via klaptop_acpi_helper also works flawlessly.

So, why does KDE deny its services here? Can KDE be instructed to recover these lost capabilities, and if so, how? 


Long version:

I am running Kubuntu Dapper on a Dell D620 laptop with KDE 3.5.2 and security patches installed.

Last week, I decided to install an up-to-date kernel, in order to get access to the zd1211rw driver for my WLAN USB stick. This driver requires a kernel > 2.6.18, so the dapper kernel (2.6.25) was no longer an option. I decided to use the (then) latest kernel from kernel.org, 2.6.22.9. Since finding the correct parameters for kernel configuration was a bit troublesome, I eventually tried the kernel package for ubuntu 7.10 (gutsy), more as an idea of last resort, but this allowed me to boot almost flawlessly. What I finally did was to use the kernel configuration file from gutsy and modified it for my CPU (Core 2 Duo instead of i586 and the snd-hda-intel driver). I also patched the 2.6.22.9 sources from kernel.org to get rid of some nasty
device-mapper error messages and then recompiled. I now have an up-to-date kernel again, with good wireless support. So far so good.

Since then, KDE refuses to autodetect USB devices, i.e. when inserting the memory stick it is properly detected in the syslog as /dev/sdb1, and after setting up a mount point (/media/usbstick), I am able to mount it manually. Before the upgrade, there was no need for that mount point, as the KDE automounter detected the stick, showed an icon on the screen, asked me what to do, and mounted the device to /media/sdb1. 

Likewise, when right-clicking on the battery icon in the panel I was able to select 'suspend' and 'hibernate' from a pop up menu. Now, the menu is still there, but it is missing the 'hibernate' entry, while suspending still works. I now have to invoke 'klaptop_acpi_helper --hibernate' from the command line in order to hibernate the machine.

Both problems are not fatal, but annoying and I would like to have them back again. So far, google was of no great help. As both functionalities are still there after the kernel upgrade, they cannot be a kernel problem. I rather suspect some problems of KDE to find and/or access config files or similar, but I have absolutely no ideawhere to start looking at. Any help or attempt to enlighten me would be greatly appreciated.

Thanks in advance!

---

