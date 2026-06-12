---
title: "Kernel 2.6.29.1 Compile Problem"
date: 2009-04-03
forum: General Help
---

### Post by gus_zernial on 2009-04-03
I am setting up a new an AMD Phenom II X4 system, using Kubuntu Jaunty 9.04 beta, on Linux software RAID disk. The system worked fine with kernel 2.6.28-11-generic, the latest stock kernel release with Jaunty. 

Then I tried to compile and install a custom kernel using version 2.6.29.1, downloaded from kernel.org. I believe I did 

cp /boot/config-2.6.28.11-generic /usr/src/linux-2.6.29.1/.config
cd /usr/src/linux-2.6.29.1
make oldconfig (making "hopefully" correct choices)
make menuconfig (making "hopefully" correct choices)
make
make modules
make modules-install
make install
mkinitramfs -o /boot/initrd.img-2.6.29.1 2.6.29.1
update-grub
reboot

I confess I haven't done a kernel compile in a while, so probably I made some mistake, because ...

The system boots to grub, and gives the correct kernel entries to be booted (both 2.6.28-11-generic and 2.6.29.1, and both normal and recovery mode options for each). But the system won't boot *either* the new or previous kernels, even in recovery mode.

For *both* the new and old kernels I'm getting messages "mdX: unknown partition table". This suggests to me that I screwed up the setting of some RAID option in the .config file, although I'm unclear on why that would prevent me from booting the previously working 2.6.28-11-generic kernel. And worse yet, since I can't boot into *any* kernel, and my install is on RAID meta-devices, I'm not sure how to fix whatever mistakes I made.

Would appreciate recommendations on what's wrong, what I need to change, and how to boot to fix.

---

