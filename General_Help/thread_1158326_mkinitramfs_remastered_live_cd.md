---
title: "mkinitramfs remastered live cd"
date: 2009-05-13
forum: General Help
---

### Post by dstempfley on 2009-05-13
I am remastering a live cd and need to modify the initrd.gz.  I started by unbundling the version from the iso making the changes the packing it back up.  But had problems booting sometimes.  

I decided to use mkinitramfs in the chrooted root environment.  I came up with one problem.  The live cd did not have linux-image installed as a base package in the squafs.root, so there is no /boot/vmlinuz-${version} or /boot/initrd.img-${version}.  I assume is because the kernel that boots is in the /casper directory on the ISO.  mkinitramfs doesn't make an image because it can't find a kernel.

I can hack up the tools to do copy a kernel from the iso and then remove it for space purposes, but I figure there are tools to do this already. What would be the best way to make sure that the updates from installed packages and my customizations are include in the initrd.gz on the iso?

---

### Post by dstempfley on 2009-05-13
I think i got it... tell me if I'm wrong, but as long as I pass the kernel version to mkinitramfs, it doesn't complain.  Even if it can't find the /boot/vmlinuz-${version}

/Dion

---

