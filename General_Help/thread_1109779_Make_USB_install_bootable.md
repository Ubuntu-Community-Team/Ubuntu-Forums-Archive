---
title: "Make USB install bootable"
date: 2009-03-29
forum: General Help
---

### Post by miickEe on 2009-03-29
Hey there

I'm trying to make my usb flash drive bootable with ubuntu 8.10. It's installed on a 8gb flash drive, and my bios does support booting from usb. It says that there is an "invalid or damaged boot partition" or whatever when I try to boot. I've tried going to gparted on a livecd and making the ext3 main partition flag set to "boot", and apparently I have to set lba as a flag too, but it won't let me select both.

Any suggestions to make my usb bootable?

---

### Post by uidb4056 on 2009-03-29
When you install on USB you select advanced options to choose where the grub would be installed before start to installing it?, you have to choose to install grub on USB. Be aware that when you install on USB normally it is not identified as hd0 and the menu.lst is build-ed using a wrong hard-disk numbering in relation when you boot the system from USB and maybe you have to change this on menu.lst to be able to boot. Anyway before it you need grub to be installed in your USB.

---

### Post by miickEe on 2009-03-29
Thanks mate, reinstalling with grub on the usb stick really did work wonders.

---

