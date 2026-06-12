---
title: "PAE removal"
date: 2011-05-24
forum: Desktop Environments
---

### Post by CJ_Hudson on 2011-05-24
Hi, 
Please, how do I remove the PAE kernal which seems to have been installed by default on my computer? 
(I had 4 GB of RAM but it wasn't all recognised even WITH PAE. Tried 64 bit, didn't work, long story! I now have 3 GB RAM installed, the maximum it will recognise on my system.)
I am using Natty 11.04
I have run: 

dpkg --list | grep linux-image

..and get:

rc  linux-image-2.6.35-27-generic-pae     2.6.35-27.48                               Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-28-generic-pae     2.6.35-28.50                               Linux kernel image for version 2.6.35 on x86
ii  linux-image-2.6.38-8-generic-pae      2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86
ii  linux-image-generic-pae               2.6.38.8.22                                Generic Linux kernel image

...and when I type:

sudo update-grub

..I get:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

Please, is the PAE kernal doing any harm there?
Do I want to remove it, and if so, how?:confused:

---

### Post by tgalati4 on 2011-05-24
Post the output of:

free
uname -a

To remove any kernel:

sudo apt-get remove linux-image-2.6.38-8-generic-pae linux-headers-2.6.38-8-generic-pae

Unless you have a motherboard limitation (or perhaps a BIOS setting is wrong), pae is generally harmless and it lets you see all 4 GB instead of ~3.2 GB when 4 GB is installed.  64-bit (amd64) does not need pae--it can already address RAM greater than 4 GB.  Only certain processors can use 64-bit.

---

### Post by CJ_Hudson on 2011-06-02
Hi tgalati4,
First, sorry I took so long to respond.

The output of 

free

is as follows:

   total       used       free     shared    buffers     cached
Mem:       3094956     984212    2110744          0      53296     520724
-/+ buffers/cache:     410192    2684764
Swap:      4000180          0    4000180

Obviously when I installed my previous version of Ubuntu I set the swap file at 4 G hoping PAE would work. But as you say the Motherboard is restricted, and, quite old!

The output of

uname -a

is as follows:

Linux chris-System-Product-Name 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

Even with 4 Gb physical RAM installed the computer could only use 3.1 Gb.
Thanks.

---

### Post by CJ_Hudson on 2011-06-09
Bump

---

### Post by 3Miro on 2011-06-09
The 4GB issue sounds like a BIOS limitations.

For the PAE kernel, you can got System -> Admin -> Synaptic Package Manager and then install the generic kernel (non pae). Then reboot into the new kernel to make sure it works. If it works, you can use Synaptic to remove the pae.

---

### Post by CJ_Hudson on 2011-06-15
Thankyou. Please, what is the non-PAE kernal indexed under in synaptic?

---

### Post by kronick on 2011-06-15
linux-image-2.6.38-8-generic

---

### Post by mcduck on 2011-06-16
> **MogBug said:**
> Thankyou. Please, what is the non-PAE kernal indexed under in synaptic?

linux-generic

(You'll definitely want to install that metapackage instead of just directly installing a certain kernel image version, as the metapackage is the one that makes sure you get all the required packages and that you'll also get updates for your kernel.)

---

### Post by kronick on 2011-06-16
i forgot about that metapackage

---

### Post by CJ_Hudson on 2011-06-18
Okay thanks guys,:KS that should tidy things up a bit.

EDIT: Please, do  I also need to change the swap file partition size on the hard drive? It is currently set at 4 GB or thereabouts, so will I need to change it to 3GB? I am not desperately short of disc space under Ubuntu.
Edit 2: .. and please, is a reboot required between uninstalling the PAE kernal and re-installing the original generic kernal?

---

### Post by kronick on 2011-06-18
you don't need to change swap size, however as far as I know linux won't be able to use more than 3 gigs of it.
I could be wrong though

---

### Post by mcduck on 2011-06-18
> **MogBug said:**
> Okay thanks guys,:KS that should tidy things up a bit.

EDIT: Please, do  I also need to change the swap file partition size on the hard drive? It is currently set at 4 GB or thereabouts, so will I need to change it to 3GB? I am not desperately short of disc space under Ubuntu.
Edit 2: .. and please, is a reboot required between uninstalling the PAE kernal and re-installing the original generic kernal?

Install the generic kernel first, before you remove the PAE kernel. A reboot isn't required to do the install, but the geenric one won't be used until you have rebooted.

And no need to resize the swap if you don't need the extra gigabyte of disk space back for now.  :)

---

### Post by CJ_Hudson on 2011-06-20
Thankyou very much to you all, that's very helpful.

---

