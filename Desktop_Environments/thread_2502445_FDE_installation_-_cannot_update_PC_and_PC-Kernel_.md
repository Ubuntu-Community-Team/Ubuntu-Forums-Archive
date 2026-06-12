---
title: "FDE installation - cannot update PC and PC-Kernel Snaps"
date: 2024-11-14
forum: Desktop Environments
---

### Post by GrzesiekC on 2024-11-14
G'day

Ubuntu 24.04.1

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:    24.04
Codename:    noble

$ snap --version
snap    2.65.3+24.04
snapd   2.65.3+24.04
series  16
ubuntu  24.04
kernel  6.8.0-40-generic

A fresh FDE installation (with TPM2) done via the Ubuntu installer on a new Framework 13 laptop with 4TB SSD.

Next, a few weeks later, I shrunk the main LUKS partition (i.e. Ubuntu-Data), and added my 2 own LUKS partitions in the available free space (at the end of SSD).

After a while, I noticed that two Snap packages cannot upgrade any more:

$ sudo snap refresh pc
error: cannot perform the following tasks:
- Update assets from gadget "pc" (184) (could not map volume pc from gadget.yaml to any physical disk: cannot find physical disk laid out to map with volume pc)

$ sudo snap refresh pc-kernel
error: cannot perform the following tasks:
- Update assets from kernel "pc-kernel" (1996) (could not map volume pc from gadget.yaml to any physical disk: cannot find physical disk laid out to map with volume pc)

The 2 new partitions have got important data now, which I cannot easily move anywhere ...

So, is there any possible fixed or workaround the kernel not updating any more ?

Regards

---

### Post by grahammechanical on 2024-11-15
Your post caught my eye because just now I was experimenting with Ubuntu Core Desktop where all system components are snap packages. This includes a pc-desktop snap and a pc-kernel snap.

I was surprised that the kernel should be a snap package in Ubuntu 24.04.1 LTS. So, I did some searching (not much actually) and I found this:

> TPM-backed FDE on classic Ubuntu Desktop systems is based on the same architecture as [Ubuntu Core]("https://ubuntu.com/core/docs/uc20/full-disk-encryption"),  and it shares a number of its design and implementation principles.  Namely, the bootloader (shim and GRUB) and kernel assets will be  delivered as snap packages (via gadget and kernel snaps), as opposed to  being delivered as Debian packages. As such, it is the [Snapd agent ]("https://ubuntu.com/core/docs/snaps-in-ubuntu-core")which will be responsible for managing full disk encryption throughout its lifecycle

[https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu)

I do not know the solution to your problem. Ubuntu Core Desktop also has a ubuntu-data partition. I have yet to examine the contents of this partition. I was wondering where in Ubuntu Core Desktop user installed snap packaged applications would go. The other default partitions in Ubuntu Core Desktop are not very big. Perhaps it is the ubuntu-data partition.

I also saw this in the above web page link:

> As we will be rolling out TPM-backed FDE as an experimental feature  starting with Ubuntu 23.10, we invite all early adopters to try it out  and share their thoughts. A word of caution resonates here: we strongly  advise that you only venture into this feature exclusively with hardware  you&#8217;re prepared to wipe completely, and to be fully  aware of the  dangerous risks that come with testing it.

> For those who will take the plunge, your feedback will be crucial  in  this testing phase, and highly valuable in further shaping the ongoing  implementation of FDE ahead of the next LTS release of Ubuntu.

I never thought I would ever say this but you might consider going to AskUbuntu and asking why a re-sizing to the ubuntu-data partition should prevent the kernel snap from refreshing and what to do to fix it.

Regards

---

### Post by GrzesiekC on 2024-11-19
Thx grahammechanical,

so far, I have been able to establish more-or-less the same ...
Yes, snaps land on the Ubuntu Data partition. 

BTW, for FDE installation there are also:
- ubuntu-seed (clr txt)
- ubuntu-boot (clr txt)
- ubuntu-save (LUKS)

---

### Post by GrzesiekC on 2024-11-19
From here - [https://ubuntu.com/core/docs/gadget-snaps](https://ubuntu.com/core/docs/gadget-snaps)

> **ubuntu-data** needs to be the last partition. No extra partitions can be inserted between **ubuntu-boot**, **ubuntu-save** and **ubuntu-data**. If extra partitions are required, they need to be declared and created before **ubuntu-boot**.

Yet still not sure how to fix it ;-)

---

### Post by grahammechanical on 2024-11-19
I am frustrated in my experiments with Ubuntu Core Desktop. I installed it on a 16 GB USB stick and it loads to a login screen and then a desktop environment. Which is a massive improvement on Ubuntu Core. But 16 GB is too small to build a usable desktop OS. I thought I could install Core Desktop to an external SATA drive but although the UEFI sees the drive as an EFI device it cannot boot it. But it boots the Ubuntu Core Desktop on the USB stick.

On Ubuntu Core Desktop Grub is a snap. Is this also true with an FDE installation? The App Centre is really an improved Snap Store. Will it update the pc and kernel snaps? Assuming you can still load Ubuntu.

Regards

---

