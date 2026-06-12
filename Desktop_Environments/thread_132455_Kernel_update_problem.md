---
title: "Kernel update problem"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Briquet on 2006-02-18
Hi, I updated my kernel to the last version of 2.6.12-10-686 and since then I cannot use Ubuntu anymore, the error message I can see after using 
dpkg-reconfigure linux-image-2.6.12-10-686 (using chroot with a live cd)  is

WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.12-10-686/kernel/drivers/net/bnx2.ko
Not touching initrd symlinks since we are being reinstalled (2.6.12-10.28 )
Not updating image symbolic links since we are being updated (2.6.12-10.28 )
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

And when I try to enter I can even see a message of kernel panic

Please any help!!!

---

### Post by bfonseca on 2006-02-18
Can you boot into linux-image-2.6.12-9-686?  if so you can go back into that and just do a complete uninstall of 2.6.12-10-686 and then reinstall.

If that doesn't work then you should be able to get into the terminal from the grub menu and here you can reinstall.  I did run into this problem and it happened because I tried to update to dapper.

If you can go into the 2.6.12-9-686 kernel then do that first, that should still work.

Brian

---

### Post by Briquet on 2006-02-18
Hi Brian, I tried to reinstall the kernel image through the live cd (apt-get install --reinstall linux-image-2.6.12-10-686) and it could be done but I got the same warning: Couldn't find symtab and strtab in module /lib/modules/2.6.12-10-686/kernel/drivers/net/bnx2.ko with the same final result
I also tried to install the 2.6.12-9-686, I thought I did it but after rebooting I realized that I didn't installed at all (I don't know what I did wrong here)

Thanks

---

