---
title: "Dual Boot: Ubuntu &amp; Sun Solaris"
date: 2006-01-07
forum: Desktop Environments
---

### Post by alamba on 2006-01-07
Hey all,

Has anyone here tried a dual boot with ubuntu and sun solaris 10? Any interesting resources available?

I'm considering dual booting my HP laptop like such, currently I just have ubuntu on it. 

Regards,
Akshay

---

### Post by alamba on 2006-01-07
Been ignored at the forums again!! Well here's a link that talks about exactly what I was proposing:

[http://blogs.sun.com/roller/page/sdebnath?entry=getting_solaris_and_linux_to](http://blogs.sun.com/roller/page/sdebnath?entry=getting_solaris_and_linux_to)

Akshay

---

### Post by dboot on 2006-01-08
Any luck with Solaris 10 and Ubuntu?

---

### Post by alamba on 2006-01-24
Yep. Got it going in a VM environment.

---

### Post by dboot on 2006-11-01
Just tried dual booting Ubuntu Edgy and Solaris 10 on my laptop. After some grub trouble, I finally got it working with these steps:

1. Install Edgy leaving unpartitioned space for Solaris 10.
2. Boot Edgy and write down the grub information from /boot/grub/menu.lst:
```

title Ubuntu Edgy
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```
3. Install Solaris 10 in unpartitioned disk space (it will recognize your Ubuntu partition).
4. Boot Solaris 10 and change /boot/grub/menu.lst (after backing up the file) by adding *only* the first 4 lines of your Ubuntu grub information after the Solaris 10 information. It should look something like this:
```

#------------ADDED BY BOOTADM - DO NOT EDIT -----------
title Solaris 10
root (hd0,3,a)
kernel /platform/i86pc/multiboot
module /platform/i86pc/boot_archive
#------------------END BOOTADM-------------------------
title Ubuntu Edgy
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
```
5. Reboot and enjoy. :-D

---

### Post by prkfriryce on 2006-12-15
Has anyone been successful with dual booting Solaris on 2 separate harddrives?:

Solaris = hd0
Ubuntu = hd1
Grub is installed on hd1 after Solaris was installed.

```

#------------ADDED BY BOOTADM - DO NOT EDIT -----------
title Solaris 10
root (hd0,2)
kernel /platform/i86pc/multiboot
module /platform/i86pc/boot_archive
#------------------END BOOTADM-------------------------
title Ubuntu Edgy
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
```

I keep receiving the "Filesystem type unknown" error of 0xbf (hd0,0) and 0x12 (hd0,1)

where 0xbf would be the Solaris partition and 0x12 is a Compaq diagnostic partition.


thanks! ;)

---

### Post by prkfriryce on 2006-12-18
so after some investigation, Solaris 10 ufs filesystem is not supported with linux-GRUB. Has anyone found a work-around for this issue or have successfully installed solaris-GRUb on the linux partition/HD??

---

### Post by prkfriryce on 2006-12-18
I've found a workaround by adding this to menu.list:
```
title Solaris 10
root (hd0,1)
chainloader +1
makeactive
boot 
```

makeactive is necessary to jump to the Solaris grub where it reads the ufs filesystem correctly.

All is well now.

: )

---

