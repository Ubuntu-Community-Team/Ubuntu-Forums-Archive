---
title: "how to install 2.6.30rc6?"
date: 2009-05-21
forum: General Help
---

### Post by keypox on 2009-05-21
All i can find is threads pointing here [http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/)

which is fine but what do i do after that?  I downloaded files from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/)

The amd64 ones, installed them but when i restart the new kernel doesnt show up in grub.  

I also tried .29 and it added to grub but wont boot.

---

### Post by Zorael on 2009-05-21
For amd64, download [headers_amd64](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb), [headers_all](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-headers-2.6.30-020630rc6_2.6.30-020630rc6_all.deb) and [image_amd64](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb). Then install, via a terminal or with gdebi. It should configure grub by itself, and add the appropriate entries there.

```
$ cd *<directory you downloaded the .deb files to>*
$ sudo dpkg -i linux*020630rc6*.deb
```

To force grub to update itself, if for some random offworld reason it doesn't automatically, do the following.
```
$ sudo update-grub
```

---

### Post by keypox on 2009-05-21
> **Zorael said:**
> For amd64, download [headers_amd64](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb), [headers_all](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-headers-2.6.30-020630rc6_2.6.30-020630rc6_all.deb) and [image_amd64](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb). Then install, via a terminal or with gdebi. It should configure grub by itself, and add the appropriate entries there.

```
$ cd *<directory you downloaded the .deb files to>*
$ sudo dpkg -i linux*020630rc6*.deb
```

To force grub to update itself, if for some random offworld reason it doesn't automatically, do the following.
```
$ sudo update-grub
```

thanks will try this brb'

I like installing via terminal, shows me whats going on.  Anyways it still didnt add to grub here is what terminal gave me

"

(Reading database ... 151235 files and directories currently installed.)
Preparing to replace linux-headers-2.6.30-020630rc6 2.6.30-020630rc6 (using linux-headers-2.6.30-020630rc6_2.6.30-020630rc6_all.deb) ...
Unpacking replacement linux-headers-2.6.30-020630rc6 ...
Preparing to replace linux-headers-2.6.30-020630rc6-generic 2.6.30-020630rc6 (using linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb) ...
Unpacking replacement linux-headers-2.6.30-020630rc6-generic ...
Preparing to replace linux-image-2.6.30-020630rc6-generic 2.6.30-020630rc6 (using linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-020630rc6-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630rc6-generic
Found kernel: /boot/vmlinuz-2.6.29-02062903-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.30-020630rc6 (2.6.30-020630rc6) ...
Setting up linux-headers-2.6.30-020630rc6-generic (2.6.30-020630rc6) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.30-020630rc6-generic (2.6.30-020630rc6) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-020630rc6-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.30-020630rc6 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.30-020630rc6 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630rc6-generic
Found kernel: /boot/vmlinuz-2.6.29-02062903-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
"

Update Grub said this: 
sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630rc6-generic
Found kernel: /boot/vmlinuz-2.6.29-02062903-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

but did not add .30rc6

---

### Post by keypox on 2009-05-21
anyone know how to add it to the boot menu?  I think its installed but not in grub. 

sudo update-grub doesnt work.

---

### Post by Zorael on 2009-05-21
```
sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
**Found kernel: /boot/vmlinuz-2.6.30-020630[COLOR="Lime"]_rc6_[/COLOR]-generic**
Found kernel: /boot/vmlinuz-2.6.29-02062903-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
**Updating /boot/grub/menu.lst ... done**
```
> **keypox said:**
> but did not add .30rc6
It looks like it did, though?

---

### Post by keypox on 2009-05-21
> **Zorael said:**
> ```
sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
**Found kernel: /boot/vmlinuz-2.6.30-020630[COLOR="Lime"]_rc6_[/COLOR]-generic**
Found kernel: /boot/vmlinuz-2.6.29-02062903-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
**Updating /boot/grub/menu.lst ... done**
```

It looks like it did, though?

Yes it does look like it did, but it did not. 

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		517c925a-3860-4182-b35e-d8f8e527cce0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=517c925a-3860-4182-b35e-d8f8e527cce0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		517c925a-3860-4182-b35e-d8f8e527cce0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=517c925a-3860-4182-b35e-d8f8e527cce0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		517c925a-3860-4182-b35e-d8f8e527cce0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=517c925a-3860-4182-b35e-d8f8e527cce0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		517c925a-3860-4182-b35e-d8f8e527cce0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=517c925a-3860-4182-b35e-d8f8e527cce0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		517c925a-3860-4182-b35e-d8f8e527cce0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by keypox on 2009-05-21
i think i mayhave found out why

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

I said keep old version as did these people, i had no idea what i meant... should have looked into it more.

And here is how to fix it  [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009/comments/29](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009/comments/29)

Sucks i lost my windows 7 and vista entries but hopefully i can just add them in, as i backed up the old menu.lst

---

### Post by keypox on 2009-05-21
well it worked, but .30 boots to a blank screen, as did .29 wtf am i doing wrong.

---

### Post by Zorael on 2009-05-21
Usual gotcha: proprietary video driver (NVIDIA/ATI)? They'd need to be reinstalled when you upgrade your kernel.

---

### Post by keypox on 2009-05-21
> **Zorael said:**
> Usual gotcha: proprietary video driver (NVIDIA/ATI)? They'd need to be reinstalled when you upgrade your kernel.

lol yeah, 

Well i can't even boot with the new kernel. Can i force mesa drivers or something?  I figure the drivers are causing the issues.

Nevermind install failed completely after tyrin a few things... reinstalling and gonna go straight to 2.6.30

---

### Post by Zorael on 2009-05-22
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```
That should reset your /etc/X11/xorg.conf file and make it load the nv driver.

---

