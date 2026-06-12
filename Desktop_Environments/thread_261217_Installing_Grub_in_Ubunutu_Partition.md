---
title: "Installing Grub in Ubunutu Partition"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Jim313 on 2006-09-19
I am multi-booting and want to get Ubuntu to install Grub in its partition but havn't been successful.  Either the option is not present during install or I have missed it three times.  Can anyone help?  I have other Linux OSes I am checking out and am utilizing chain booting.  The others have given me the option to install Grub in the MBR or os root partition.

If this is automatic than I have another problem to remediate.  I get a "file not found" error when trying to boot Ubuntu from my other Grub boot loader.

Thanks

JM

---

### Post by X.Cyclop on 2006-09-20
[QUOTE="PingunZ"]sudo grub

grub> find /boot/grub/stage1
 (hdx,y)
grub> root (hdx,y)
grub> setup (hdx)[/QUOTE]

;)

---

