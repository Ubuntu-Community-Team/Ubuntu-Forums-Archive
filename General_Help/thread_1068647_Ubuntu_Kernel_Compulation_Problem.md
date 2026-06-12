---
title: "Ubuntu Kernel Compulation Problem"
date: 2009-02-13
forum: General Help
---

### Post by Chris_Smith on 2009-02-13
Hi Guys,

I am hoping that one of you will be able to help me with a problem that I have with recompiling a 2.6.22 kernel to be used on my mythbuntu 8.04.1 setup.

I am using a Hauppauge HVR-1300 TV card, and have discovered by trial and error using Debian etch, that all kernels greater than 2.6.22 cause problems with digital reception when tuned to 506 and 562MHz from the Crystal Palace transmitter in the UK. This means that I can't receive all the BBC and Five channels, the audio stutters, and the picture is full of large pixels. All the other frequencies are unaffected.

Mythbuntu 8.04.1 uses kernel 2.6.24, but when I compiled a 2.6.22 kernel using sources from both kernel.org and Ubuntu, it failed to boot because Ubuntu uses the sda, sdb ... numbering scheme to define their hard drives, and the recompiled kernel expects the numbering scheme to be hda, hdb etc. I have tried changing the root=/dev/sdb3 to hdb3 in grub's menu.lst, and changing the fstab entries, and got the kernel to boot, but none of the TV applications can get a signal lock! I have also tried using root=UUID= <hex number> to define the root drive, but that also failed.

Is it possible to compile the kernel so that it recognises the Ubuntu numbering scheme, or have Ubuntu patched their sources so that it is not possible to use a vanilla kernel?
-------------------
Best regards,
Chris Smith

---

### Post by Dies on 2009-02-13
> **Chris_Smith said:**
> 
Is it possible to compile the kernel so that it recognises the Ubuntu numbering scheme, or have Ubuntu patched their sources so that it is not possible to use a vanilla kernel?


Those particular patches are not Ubuntu or Debian specific but upstream.

Have you tried compiling V4L yourself against the normal kernel?

If you haven't filed a bug against V4L for regression yet, that would probably be a good idea.


Aside from that... :confused:


It is open source, so you can always diff a kernel that works against one that doesn't and see what changes were made in V4L. You can also look on patches.ubuntu.com to see what if any changes Ubuntu makes to the kernel or any other packages.

---

### Post by Chris_Smith on 2009-04-14
Hi Guys,

I have discovered how to solve the boot problem, but still can't get a channel/signal lock:

First enable CONFIG_ATA

Goto Device drivers > Serial ATA(Prod) and Parrallel ATA (Experimental) drivers. Enable this option, and pick a southbridge driver for the motherboard - in my case it was VIA PATA.

Then disable CONFIG_IDE

Goto ATA/ATAPI/MFM/RLL Support that handles IDE drives the old way, and disable this option.

Note, CONFIG_ATA depends on SCSI hard drive support, so if you are not using an initrd.img, make sure that SCSI hard drive support is compiled into the kernel, or it will not boot!

The new kernel will then recognize the Ubuntu sdxx hard drive naming scheme.

CS.

---

