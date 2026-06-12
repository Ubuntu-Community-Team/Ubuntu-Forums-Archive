---
title: "SWAP Partition Boot Options"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Geffers on 2006-04-30
Using a Boot Floppy I then use the following commands from the GRUB prompt to boot my system after losing GRUB from my hard drive.

root (hd0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3
initrd /boot/initrd.img-2.6.12-9-386
boot

Should I be mentioning the SWAP partition on hda7 anywhere of is this done when the system loads.

Geffers

---

### Post by Ramses de Norre on 2006-04-30
This is taken care of by fstab.

---

### Post by Geffers on 2006-05-01
[QUOTE=Ramses de Norre]This is taken care of by fstab.[/QUOTE]

Right, thanks.

Geffers

---

