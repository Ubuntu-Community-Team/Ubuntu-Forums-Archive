---
title: "Tweaking the boot loader"
date: 2009-03-06
forum: General Help
---

### Post by glennzo on 2009-03-06
Lesse. I'm playing around with **configfile** in **/boot/grub/menu.lst** on my desktop. This box boots F10, F11, Ubuntu, Debian and XP. Debian is the last installed Linux OS so Debain's grub is making the calls. When I installed the other Linux OS's I let their installers set up grub also. As things progressed multi-booting was working perfectly. All was well with the Debian grub configuration also but as we all know, get a kernel update for any one of these OS's and you need to do some editing so that the new kernel is available in the menu. This can be tricky at best, but, I've done things this way for a long time now. I was thinking that the configfile option would be a much easier way to handle things, and it should be, and is, but there's one hitch. I can't for the life of me get the Ubuntu install to boot. Here's the deal:
```
debian:~# /sbin/fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06afd788

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS [COLOR="Red"]< -- Storage only.[/COLOR]

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x014b717e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS [COLOR="Red"]< - EXPee[/COLOR]
/dev/hda2            2612        9729    57175335   83  Linux [COLOR="Red"]< - Fedora 10[/COLOR]

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         261     2096451   82  Linux swap / Solaris
/dev/hdb2             262        5483    41945715   83  Linux [COLOR="Red"]< - Ubuntu[/COLOR]
/dev/hdb3            5484        8094    20972857+  83  Linux [COLOR="Red"]< - Fedora 11[/COLOR]
/dev/hdb4            8095       10705    20972857+  83  Linux [COLOR="Red"]< - Debian[/COLOR]

```

Debian's menu.lst:
```
debian:~# cat /boot/grub/menu.lst
default		2
timeout		30
color cyan/blue white/blue

title		Debian
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/hdb4 ro quiet vga=791
initrd		/boot/initrd.img-2.6.26-1-686

title		EXPee
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title   	Fedora 10
root 		(hd0,1)
configfile	/boot/grub/menu.lst

title		Fedora 10
root		(hd0,1)
configfile	/boot/grub/menu.lst

title		Ubuntu 8.10
root		(hd1,1)
configfile	/boot/grub/menu.lst

title 		Fedora 11 Alpha
root 		(hd1,2)
configfile	/boot/grub/menu.lst

```
All OS's boot with the exception of Ubuntu. If I choose Ubuntu I do in fact get Ubuntu's boot menu but choosing the one option there gets me a grub error 15, file not found. I can usually fix this sort of thing myself but not this time. One thing I'm considering is the fact that the SATA 500GB disk, seen as /dev/sda in Debian, is seen as /dev/sdc in Fedora 10 or 11. Ubuntu also sees this disk as /dev/sdc. That said, I'm wondering if this is the root of the issue. 

Here's another caveat. I just rebooted that box, chose Fedora 10 and got it's boot menu. From there I chose Ubuntu and it booted fine. What's going on here?

The working Ubuntu entry in Fedora's boot menu:
> title	Ubuntu 8.10 (2.6.27-11-generic)
	root (hd1,1)
	kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=7d675030-7523-4987-a9e1-4230d536ec2c ro quiet splash 
	initrd /boot/initrd.img-2.6.27-11-generic
	quiet


Ubuntu's boot menu, loaded by Debian's boot loader:
> default		0
timeout		30
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7d675030-7523-4987-a9e1-4230d536ec2c
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/hdb2 ro quiet vga=791
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7d675030-7523-4987-a9e1-4230d536ec2c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

I've made this change,
> #kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/hdb2 ro quiet vga=791
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7d675030-7523-4987-a9e1-4230d536ec2c ro quiet splash to no avail.

My brain is burning. Anyone interested enough to offer their thoughts? This should work but apparently I'm missing something, obvious or not.

---

### Post by lha on 2009-03-07
Debians Grub doesn't (yet) support command 'uuid', I believe. You'll have to replace
uuid 7d675030-7523-4987-a9e1-4230d536ec2c
with
root (hd1,1)
to make it work. (See the Ubuntu boot entry in Fedora's menu.lst.)

I'd (re-)install Ubuntu's Grub. That would let you use configfile for all distros.

---

### Post by glennzo on 2009-03-07
Thank you for your reply. That is essentially what I did and it now works flawlessly.

---

