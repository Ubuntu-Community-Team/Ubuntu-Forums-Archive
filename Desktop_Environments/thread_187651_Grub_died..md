---
title: "Grub died."
date: 2006-06-03
forum: Desktop Environments
---

### Post by Sam0r on 2006-06-03
I intended to use 5.10 for my new fileserver, but as the version of samba which came with it was broken, and there was no way of getting a newer version on there without compiling it, I decided to dist-upgrade to dapper.

Bad idea.

It seemed to work at first, although I had to use the old kernel at boot.

Then today, I decided to sort it out. So I did apt-get install linux-image-k7, and that just blew the whole thing to pieces.

When I rebooted to load the new kernel, I was greeted with the grub cli, and if i load the kernel with 'kerel /boot/vmlinuz-2.whatever' then 'boot root=/dev/hda1' it panics on me.

So now I've got a totally hosed system, and I could really do with some help repairing it because I need this thing back up and working.

---

### Post by turbojugend_gr on 2006-06-03
Well I believe you shouldn't dist-upgrade, I prefer backup and then a clean installation, it only took me one hour to make it working as I need it to, no big deal.
Anyway, I don't get it, you can only boot manually your system, using the Grub console? If yes you really need to define me which kernel you are trying to boot!

First o f all you should try and boot to your old kernel, I suppose i386.Generaly to boot a linux distro you Type theese commands:
```
grub> root (hd*,*)
grub> kernel /vmlinuz root=/dev/*THE PARTITION YOU HAVEW YOUR KERNEL IN*eg. sda1
grub> boot
```

since you are talking for a breezy installation it should be something like this
```
grub> root		(hd0,0)
grub> kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
grub> initrd		/boot/initrd.img-2.6.15-23-386
grub> boot
``` Though I believe you can ommit the initrd line...

Anyway when you manage to acces your system, or if you are less fortunate you end up just accesing your disks, I strongly reccomend a backup-reinstall procces, dapper is so easy to install and customize...

Notify me with your proccess

---

