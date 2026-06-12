---
title: "EFI installation"
date: 2018-11-01
forum: Debian
---

### Post by adam5252 on 2018-11-01
I'm actually using Debian 9, but I hope someone will be kind enough to look over this for me and lend a hand.  I've been using Debian since Potato (early 2000's) and Ubuntu for quite a while also, but have never dealt at all with EFI until now (thankfully).  Is it just me or is EFI more trouble than it's worth?  Actually, this is the second time I've collided with it.  The first time was when I was creating a custom Ubuntu install with Cubic.  It was a half day nightmare that time also.  I've been dealing with this new problem for a few days now and I'm stumped.

I installed a fresh system and wanted to clone the disk using dd - dd if=/dev/sda of=/tarballs/whatever.img

I didn't ask Debian to use EFI when I installed the system.  I'm assuming that it did but I don't have the machine where the actual installation is running right now.  I only have a copy of the image and a completely different kind of computer.  The image won't boot on the computer I have here at all and I've tried the boot repair instructions using an ubuntu live CD on USB and ran them using this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) as a guide.  Every time I have to start over it's frustrating because I have to copy the entire image back to the internal HD of this system with dd, which takes about an hour since it's a 120 GB drive.  

The original Debian installation was on a Gigabyte Z270N MB with a 120 GB SSD.  I used LVM so that I could encrypt the /home partition.  I let the installer do the original partitioning and the options I used were - Use LVM and create separate /home partition.  I did the encryption later after the installation.  The / partition is NOT encrypted.  

The real thing I want to know is if the image will work when imaged onto a new machine identical to the one that the original installation is running on.  I didn't have another machine to test that with, so I don't know.  

Anyway, now when I try to boot off of the SSD in the new machine (which is completely different hardware than the original machine where Debian is installed) it won't boot.  I get a replace system disk error from the BIOS.  Not a grub error.  It doesn't even hand off to grub.

Here is boot-repairs output at pastebin.  Will someone please help and at least point me in the right direction?

[http://paste.ubuntu.com/p/FsqKybbJ8b/](http://paste.ubuntu.com/p/FsqKybbJ8b/)

Thanks in advance.  

Adam

---

### Post by oldfred on 2018-11-01
Moved to Debian sub-forum.

Boot-Repair will not (it seems) as to un-encrypt an encrypted install. You need to un-encrypt it and then run Boot-Repair.

It looks like an old standard BIOS/MBR configuration with what is shown.
UEFI used gpt partitioning and first partition is an ESP - efi system partition which is FAT32.

But if system is new UEFI and has UEFI Secure Boot on, it will not boot in BIOS/CSM/Legacy mode as that is not secure.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by adam5252 on 2018-11-02
Thanks for the reply.  Thanks for the info.

---

