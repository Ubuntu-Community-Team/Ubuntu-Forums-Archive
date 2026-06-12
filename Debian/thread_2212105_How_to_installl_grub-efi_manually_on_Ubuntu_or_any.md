---
title: "How to installl grub-efi manually on Ubuntu or any other linux system?"
date: 2014-03-19
forum: Debian
---

### Post by hamishmb on 2014-03-19
I've been writing a free application for linux distros (no specific distro, just anything that supports the dependencies), and I've called it wxfixboot. It's designed to make it easy and fast to switch from grub or lilo BIOS bootloader to the UEFI version, and also the other way around, while also providing other useful features such as checking devices for bad sectors, backing up the bootloader, that sort of thing. It's now nearing completion, but I've been having a serious issue: It isn't too difficult to install grub-mbr or lilo-mbr to a hard disk, using the gathered info about the system it's running on, but for some reason I can't find a way to install either grub-efi or elilo. I'm trying this in virtualbox, but have also tryed it in vmware player, with the overall result that I can create an efi partition, and install elilo or grub-efi to it, but when I try to boot the .efi file, the cpu triple faults, and the vm is halted in guru meditation mode or similar. So what I'm asking is, does anyone know how to install grub-efi or elilo manually to a hard drive, and what commands and info about the system I need to do that? Thanks in advance, I appreciate any help that anyone can give!

Hamish

---

### Post by Kris_Spencer on 2014-03-21
Before trying the install, you probably need to mount the efivarfs:

mount -t efivarfs efivarfs /sys/firmware/efi/efivars

I've only had to do this once with Grub. I was install Arch on my friend's laptop. After mounting that, if it was needed, you can install like this:

grub-install --target=x86_64-efi --efi-directory=$esp

The Arch wiki pages might be handy. There isn't a page for elilo really:

Grub: [https://wiki.archlinux.org/index.php/GRUB#UEFI_systems_2](https://wiki.archlinux.org/index.php/GRUB#UEFI_systems_2)

EFI: [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

---

### Post by hamishmb on 2014-03-21
Thank you very much, I remember grub-efi complaining about efi variables! I can probably derive something from that for elilo! Is the efivarfs present even if the system is booted from a live disk, or in CSM mode on an efi system? Are these fairly universal instructions for grub-efi? Thanks, that may well solve it, I'll look into it when I have some time :) Is there anything else related to this that you could tell me?

Hamish

---

### Post by Kris_Spencer on 2014-03-21
The install instruction is universal with Grub, as long as you aren't using the old legacy version (doesn't even support EFI anyway). The efivarfs should be, as it was for Arch and I imagine that it'd be required for all Linux based systems. That's all I got for you. I hope it helps. :)

---

### Post by hamishmb on 2014-03-24
Yes, I think it'd be a lot of work to support grub legacy, especially since it's basically dead anyway. Thank you very much, I'm sure it will help, I'm 99% certain this is exactly the problem I'm having. I'll let you know in a few months if it works.

Hamish

---

### Post by oldfred on 2014-03-24
You can take a look at Boot-Repair as it does some of the same things.
I think it just in effect chroots into install and then un-installs grub-pc and installs grub-efi. 
But you have to boot it in secure boot mode to get it to install in secure boot mode with signed grub & kernels. 
UEFI in secure boot only shows systems that will boot in secure boot mode.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Also
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

But if system is installed in BIOS boot mode with MBR partitioning, you will not be able to install in UEFI boot mode as UEFI needs gpt partitioning with an efi partition. And with BIOS boot on gpt drives need the bios_grub partition.
Windows only boots from gpt with UEFI.
Both Ubuntu and Windows only boot from MBR(msdos) with BIOS.
But Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI if correct support partitions are on drive.

---

### Post by hamishmb on 2014-03-24
Yes, that's what I thought, but it wasn't working, but now I know it's because of efi variables not being available. I was intentding to have a look at boot-repair's source to get the general idea of how it works, but it's very convoluted and impossible for me to understand. Yes the chroot system I similar to what I do, except it'll look to see what package manager the OS uses (dpkg, yum, possibly others), rather than going on the assumption that it's dpkg and debian-based. Besides, I thought some very recent BIOS systems could boot gpt disks? Anyways, thanks for the info!

---

### Post by oldfred on 2014-03-24
I only have BIOS and have booted from gpt disks since 10.10, but that is not too common.

I believe users should install Windows on a separate drive and Ubuntu on all other drives. And then all Ubuntu drives can be gpt partitioned. Its only that XP will not even read gpt partitioned drives, but that should soon be moot.

---

### Post by hamishmb on 2014-03-25
There isn't really any benefit to having linux and windows on multiple drives, as far as I know, at least. If you've got a small HDD then perhaps, but I don't think firmware would be good athandling different partition styles on different disks. It's really a lot easier and cheaper to just install on one drive, as gpt doesn't have an awful lot of benefits anyway. There probably will still be quite a few people who stick with XP anyway.

---

### Post by hamishmb on 2014-04-01
Thank you so much Kris_Spencer, that solved it! I also needed to manaully create a boot option in virtualbox, as it was too stupid to remember the one grub created for it! With a real system, you don't even necessarily need to use efi variables (I didn't with mine!), but it's good to experiment with vbox, which probably has the worst efi implementation ever, because I can be absolutely certain that nothing will ever be pickier!

Best Regards,
Hamish

---

### Post by max-atak on 2014-04-01
Hi,
 
I want to do this:
rEFIT menu list bootcamp, macOS, and legacy grub2 entry.
Grub2 entry list his menu with Bootcamp using setpci for ahci and the 2nd gpu, with no others hardware pb.
 
i think I have to install grub2 in the FAT32 EFI partition like this : /EFI/BOOT/BOOTX64.EFI
But how ?
 
 
My HD looks like this :
 
Fat32 EFI system 200mb
HFS+ Mac OSx partition 339gb => _with rEFIT_

#Unknown partition 618,89mb hybrideMBR I think#
NTFS Bootcamp partition 64,11Gb
 
I really need to boot windows with a grub2 patched (using firmware vars) to enable ahci and the 2nd gpu in windows 7.
  I have so much docs about this on google but i'm a bit confused about  how to do this correctly, where find package, how to compile grub2 etc.
Anyone can help me to install grub2 without touching my partitions please.

---

### Post by hamishmb on 2014-04-02
I don't have the knowledge to help with this, but please ask a seperate question so this gets noticed, as this one is marked solved, and I'd like to keep it tidy, so I can refer back later. It's generally good practice to ask a new question, with a new title, so it can be seen, especially since you've got a complicated question.

Hamish

---

### Post by hamishmb on 2014-04-02
I see you've already got another thread actually, so why post here?

---

