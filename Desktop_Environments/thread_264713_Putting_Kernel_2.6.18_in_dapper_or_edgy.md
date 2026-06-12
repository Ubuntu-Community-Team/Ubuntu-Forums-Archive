---
title: "Putting Kernel 2.6.18 in dapper or edgy"
date: 2006-09-25
forum: Desktop Environments
---

### Post by mikedep333 on 2006-09-25
Hello, I recently bought a new motherboard, the Gigabyte GA-965P-S3. Much to my dismay, its brand new chipsets, the intel P96 northbridge and the ICH8 southbridge, are only supported by kernel 2.6.18 and newer. I read here:
[http://kerneltrap.org/node/7020](http://kerneltrap.org/node/7020)

[I]I got dapper on a DG965MS using a USB cdrom drive and acpi=off in the boot command. Once installed I droped 2.6.18-rc7 (64Bit build) on it with the config trimmed down to just the intel stuff.

I cant boot it without "acpi=off" and im looking at the kernel patches for that. Make sure you have the most recent bios on the DG965 motherboards.

Other that that, its running fine execpt for a slow mount on one of my sata partitions where it tries to mount sda2 and it cant find it for some reason.[/I]

Fortunately I can put together a USB cd burner, so I would like to put kernel 2.6.18 in either dapper or edgy. How do I go about doing this?
I can certainly install a bunch of .deb's if somebody can point me to them. I may be able to compile it if I have to, although I dont know how apt would like it if it doesn't see a package for the kernel.

btw: why is it that 2 (or 5) year old windows XP SP2 installs fine on this brand new hardware using generic motherboard drivers (although you will want to install the motherboard drivers from intel later on), but linux requires a brand spanking new kernel to work with it? Is it because the hardware manufacturers only bother to make hardware compatible with the existing versions of windows? Or is it because linux has a design whereby the kernel has to be tailored to specific hardware?

---

### Post by mikedep333 on 2006-09-30
I guess I should follow the directions here but for 2.6.18:
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)
I'll do that once edgy is out, but in the meantime, can anyone explain why my motherboard is incompatible?

---

### Post by mikedep333 on 2006-10-11
Oops, I forgot that the desktop CD off a usb drive won't be able to access my drives on SATA. I don't know what to do now as far as installing ubuntu.

Also, somebody on IRC explained to me why this incompatibility happened in the first place.

---

### Post by lfloyd on 2006-10-21
I'm having similar problems, but I'm using a pheonix v6.0 bios on an HP Pavillion because I need to see drives over 137gb.  I also have to boot with acpi=off.  But it hung while trying to install and something happened to the bios the time changed and the motherboard no longer sees the usb drives even thuogh I have reloaded the default saved bios settings.  Others are having similar problems.  I wish I new which bios or motherboard is compatible with ubuntu linux and hard drives over 137gb together.  Does anybody know which motherboard and or bios that is compatible with ubuntu linux with large drives?

---

