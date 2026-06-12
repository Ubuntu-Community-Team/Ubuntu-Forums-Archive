---
title: "UEFI dual boot"
date: 2013-04-07
forum: Desktop Environments
---

### Post by Vegan on 2013-04-07
I use 64-bit operating systems primarily as I detest the short word. I would be happier with 128-bit so that quantitative easing can be managed with using a register instead of mutiprecision assembler.

So my M5A99FX PRO R2.0 is UEFI so any problems to dual boot 64-bit Linux.

---

### Post by oldfred on 2013-04-07
Is this a server install?
Does your UEFI have secure boot. So far only Windows 8 pre-installed systems have secure boot. But new systems may have it soon.
Even if you do not have secure boot, I would only consider the newest versions as they also have more updates to UEFI, which is a work in progress. Each vendor has implemented the UEFI "standard" differently.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by Vegan on 2013-04-14
sounds like a real can of worms, my latest motherboard is gaming oriented board but it will be a server in the not too distant future

I am next upgrading my server and new boards are almost all UEFI so I wanted to be sure I can install Linux

Right now I have 12.04.2 install in a virtual machine and Hyper-V is currently not compelling secure boot. That may change as security issues force the issue.

I would love for Ubuntu and the kernel team to better support Hyper-V in addition to the usual suspects out there, Hyper-V is free too, but its aimed at Windows shops. 

I am managing Linux from the Server 2012 and a local host connection so its relatively safe from any undesirable assaults, right now I am running BIND9 where it makes do with 1/3 of the machine Windows Server wants

---

