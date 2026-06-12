---
title: "Burning cd's under VMWare"
date: 2005-01-17
forum: General Help
---

### Post by CbrPad on 2005-01-17
Hi,

I'm have a question about cd-burning in Win'98 installed under VMWare 4.5.2.   

The issue is that Win'98 can read cd's with no problem when I turn on the 'Legacy' option, but it cannot detect the drive, let alone burn cd's, without this option.  

Looking at the VMWare website, it seems I need to run an ide-scsi option beforehand in order to enable this.  I've tried bunging this into /etc/modules and it's loaded but still with no luck. The VMWare site does say it should be part of the lilo/grub configuration, so does anyone know how to add this to grub, or indeed what exactly I should add ?

Thanks in advance.

---

### Post by Quest-Master on 2005-01-17
:\ No idea.

I'm still trying to get VMware to detect the bootable CD in my CD drive. Hopefully, once I get that setup, then..

---

### Post by CbrPad on 2005-01-18
I did have that problem earlier for no apparent reason, so I just configured it again several times and it eventually worked.

I have figured out how to add hdc=ide-scsi in the grub and noticed it does a modprobe on it when booting up.  
However, Ubuntu itself then can't detect the cdrom, and VMWare reports "CD-ROM: /dev/cdrom exists, but does not appear to be a CD-ROM device.  Device ide0:1 will start disconnected".  
Changing the VMWare options to /dev/hdc instead of /dev/cdrom and enabling/disabling DMA access in the guest Windows o/s also do nothing.  I'm stumped !  
All I can think is to somehow mount the cdrom in Ubuntu using those grub parameters, but I'll be darned if I know how, trying to mount cdrom or hdc doesn't work.

---

