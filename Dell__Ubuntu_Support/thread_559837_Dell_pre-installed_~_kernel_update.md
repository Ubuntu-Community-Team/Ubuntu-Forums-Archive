---
title: "Dell pre-installed ~ kernel update"
date: 2007-09-25
forum: Dell  Ubuntu Support
---

### Post by Linicks on 2007-09-25
Hi all,

I have a Dell Inspiron 6400 (UK) now for 2 weeks - very, very pleased I am too - it all just works superbly (better than I ever imagined on a laptop - I am an old Linux user used to desktops).

Today I was notified by Ubuntu update manager there was new security updates ~ kernel image and headers etc.

So, if you are similar, I had no issues.

Update report:


> Updating /boot/grub/menu.lst ... done

Preparing to replace linux-libc-dev 2.6.20-16.31 (using .../linux-libc-dev_2.6.20-16.32_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-headers-2.6.20-16 (2.6.20-16.32) ...
Running postinst hook script /etc/kernel/postinst.d/dkms.


Setting up linux-headers-2.6.20-16-generic (2.6.20-16.32) ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.20-16.31 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.20-16.31 was configured last, according to dpkg)
Running postinst hook script /etc/kernel/postinst.d/dkms.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

Setting up linux-libc-dev (2.6.20-16.32) ...


The only thing that happened was /boot/grub/menu.lst was updated, and as I run without the 'quiet' option, that got added back.

So, looks good.   Very good.  And too easy...

Nick

---

### Post by darth_indy on 2007-09-25
I had a MAJOR problem! After updating the kernel, and restarting, it no longer even recognized my built in wireless card as working! If I use GRUB when I boot up and revert back to the original, it works fine, but if I just let it start up it never sees the wi-fi card.

Does anyone have the solution, or know how to rollback an install? Please help, as I'm leaving on a trip tomorrow at 6 am!

---

### Post by ccfiel on 2007-09-26
you can edit your grub and make the old kernel the default one. :)

---

