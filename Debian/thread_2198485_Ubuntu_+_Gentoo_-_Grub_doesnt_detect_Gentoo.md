---
title: "Ubuntu + Gentoo - Grub doesnt detect Gentoo"
date: 2014-01-09
forum: Debian
---

### Post by Tristan_Williams on 2014-01-09
I am running Ubuntu Minimal 13.10 on /dev/sda1
I have just installed gentoo on /dev/sdb (using this guide: [https://wiki.gentoo.org/wiki/User:666threesixes666#Install](https://wiki.gentoo.org/wiki/User:666threesixes666#Install) )

My Gentoo partition layout is:
/       = /dev/sda3
/boot = /dev/sda1
swap = /dev/sda2

In my ubuntu system, I run os-prober, and then run the following:
```

update-grub
update-grub2

```
The output is:
```

root: / $ update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.12.4-custom
Found initrd image: /boot/initrd.img-3.12.4-custom
Found linux image: /boot/vmlinuz-3.11.0-15-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-15-lowlatency
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-14-lowlatency
Found memtest86+ image: /boot/memtest86+.bin
Found Gentoo Base System release 2.2 on /dev/sdb3
done
root: / $update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.12.4-custom
Found initrd image: /boot/initrd.img-3.12.4-custom
Found linux image: /boot/vmlinuz-3.11.0-15-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-15-lowlatency
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-14-lowlatency
Found memtest86+ image: /boot/memtest86+.bin
Found Gentoo Base System release 2.2 on /dev/sdb3
done

```

As you can see, Grub detects "Gentoo Base System release 2.2 on /dev/sdb3"

However, when I boot, Grub does not show a menu entry for Gentoo.
I also tries booting directly to the Gentoo HDD from BIOS, but absolutely nothing happened.

What do I do???

---

### Post by carl4926 on 2014-01-09
Try mounting the Gentoo root partition
The update-grub

---

### Post by Tristan_Williams on 2014-01-09
The Gentoo partition is already mounted. That is the first thing I do when dealing with the Gentoo system. 
Here is the way I mount it:
```

mount /dev/sdb3 /mnt/gentoo
mount /dev/sdb1 /mnt/gentoo/boot
mount -t proc none /mnt/gentoo/proc/
mount --rbind /dev /mnt/gentoo/dev/
ntpdate pool.ntp.org
chroot /mnt/gentoo/ /bin/bash

```

---

### Post by carl4926 on 2014-01-09
I just mean open it in Nautlius

---

### Post by jdeca57 on 2014-01-09
> **Tristan_Williams said:**
> The Gentoo partition is already mounted. That is the first thing I do when dealing with the Gentoo system. 
Here is the way I mount it:
```

mount /dev/sdb3 /mnt/gentoo
mount /dev/sdb1 /mnt/gentoo/boot
mount -t proc none /mnt/gentoo/proc/
mount --rbind /dev /mnt/gentoo/dev/
ntpdate pool.ntp.org
chroot /mnt/gentoo/ /bin/bash

```
But if you do 
chroot /mnt/gentoo/ /bin/bash
you change the root and you're working under gentoo. So any changes to grub are placed in /mnt/gentoo/boot (appearing to be /boot) and not in the real /boot, which would be the reason why changes have no effect.
Or do I see that wrong?

---

