---
title: "Inspiron 530 will not boot on 2.6.27"
date: 2009-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trent_shipley on 2009-04-07
Dell Inspiron 530, service tag 6NWC1G1:  Not altered from factory settings except for upgrade to 8.10 and a preference for Kubuntu.

All 2.6.27 kernels refuse to boot.  Before entering splash screen or rolling startup messages the system produces a "not responding (n.nnnnn)" error and then tries to reboot itself.  Booting is not intermittent, all attempts fail.

2.6.22-14 boots no problem, but then software dependent on 2.6.27 is unstable.

Will this Inspiron 530 boot from 2.6.27?

----------------------------------------
From GRUB:

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd		/boot/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

---

### Post by superm1 on 2009-04-08
> **trent_shipley said:**
> Dell Inspiron 530, service tag 6NWC1G1:  Not altered from factory settings except for upgrade to 8.10 and a preference for Kubuntu.

All 2.6.27 kernels refuse to boot.  Before entering splash screen or rolling startup messages the system produces a "not responding (n.nnnnn)" error and then tries to reboot itself.  Booting is not intermittent, all attempts fail.

2.6.22-14 boots no problem, but then software dependent on 2.6.27 is unstable.

Will this Inspiron 530 boot from 2.6.27?

----------------------------------------
From GRUB:

title        Ubuntu 8.10, kernel 2.6.27-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 8.10, kernel 2.6.27-13-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-13-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-13-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-13-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd        /boot/initrd.img-2.6.27-13-generic

title        Ubuntu 8.10, kernel 2.6.27-12-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-12-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-12-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-12-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro single
initrd        /boot/initrd.img-2.6.27-12-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=93640f13-66b2-4c35-beb1-2d73cf9b6e3f ro  single
initrd        /boot/initrd.img-2.6.22-14-generic
The best thing to do is to rule out problems with your upgrade, and try to boot off of an 8.10 live disk.

---

### Post by trent_shipley on 2009-04-08
It also refuses to boot off of a recent 8.04 cd downloaded from the Ubuntu site.

---

### Post by gbrainin on 2009-04-08
FWIW, my 530 has been running the 2.6.27 kernel for some time without incident.

---

### Post by unutbu on 2009-04-08
This report seems similar: [http://ubuntuforums.org/showthread.php?t=1117797](http://ubuntuforums.org/showthread.php?t=1117797)

PS. The error message you are seeing is (I believe) coming from the Linux kernel. The GRUB stage of the boot is over, so I don't think the problem has to do with GRUB.

---

### Post by superm1 on 2009-04-08
> **trent_shipley said:**
> It also refuses to boot off of a recent 8.04 cd downloaded from the Ubuntu site.
There is a bug regarding the hard drives and a BIOS setting present in 8.04.  

That other link that was posted sounds more like your problem than a general incompatibility with 8.10.

---

### Post by jamesisin on 2011-02-16
Sorry to dig this one up but I'm having essentially the same problem.

I have a system which has been running 8.10 for two years (and am preparing to rebuild, thanks).  Today I thought to reboot it and am now stuck in a boot-loop getting the "not responding" error.

I made no changes prior to the reboot (just felt it was time) other than moving documents off the main drive onto a spare (preparing for the rebuild).

I have tried booting into several of the previous kernels and I ran memtest (flying colors).  I keep getting the same error (though the number which follows the "not responding" seems to be getting larger).

Any ideas?  I wasn't quite finished preparing for the migration.

---

### Post by jamesisin on 2011-02-16
Oddly, it's related to my scanner:

[http://ubuntuforums.org/showthread.php?p=10464848](http://ubuntuforums.org/showthread.php?p=10464848)

---

