---
title: "Cannot boot USB Ubuntu 10.04"
date: 2011-05-05
forum: Desktop Environments
---

### Post by LMD1990 on 2011-05-05
Hi folks,

I'm trying to create a bootable install of Ubuntu 10.04 which boots off an 8GB Kingston DataTraveler USB stick. I used the latest Universal USB installer from pendrivelinux to install it, and I used the I386 ISO of Ubuntu 10.04. It successfully installed to the USB stick and I enabled 4GB of persistence. However, when I put it into any machine it gives me the following message:

[I]Mount: mounting /dev/loop0 on //filesystem.squashfs failed: No such device
(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs[/I]

I tried redoing it, and redoing it without persistence enabled, but still no luck.

Any suggestions?

---

### Post by mörgæs on 2011-05-05
Try creating the stick with Unetbootin.

---

### Post by LMD1990 on 2011-05-05
Well that works so thank you very much for the suggestion- but does anyone know why the Universal USB Installer does not work? I would like to know and if anyone can make a bootable Ubuntu USB with it?

---

