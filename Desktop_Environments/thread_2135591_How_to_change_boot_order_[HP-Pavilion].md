---
title: "How to change boot order [HP-Pavilion]"
date: 2013-04-14
forum: Desktop Environments
---

### Post by Xemnas2010 on 2013-04-14
I'm trying to set up a friend with ubuntu 11.10 because her windows is refusing to recover. however, the bios setup is giving me a headache. What I think is the 'boot order' is doing absolutely nothing, and I've been up and down google trying to find an answer. It an HP-Pavilion p7-1421 desktop with Hewlett-Packard Setup Utility Version 2.15.1227. I was also wondering if it was possible to install an Asus or a Pheonix Bios setup as I'm very familiar with those layouts, and if anybody has any ideas or solutions I'm open to anything.

---

### Post by ibjsb4 on 2013-04-14
Can't you just change it in grub?

```
gksudo gedit /etc/default/grub
```

[http://ubuntuforums.org/showthread.php?t=1753396](http://ubuntuforums.org/showthread.php?t=1753396)

---

### Post by oldfred on 2013-04-14
Is this a Windows 8 system with secure boot UEFI.
You cannot change BIOS/UEFI as it is designed for the specific hardware you have.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

