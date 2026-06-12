---
title: "Grub.lst missing entries, Grub loader is not"
date: 2009-05-14
forum: General Help
---

### Post by joey-elijah on 2009-05-14
I have Ubuntu installed, but yesterday also installed Kubuntu alongside it (as a separate installation as per some people on here's recommendations) however it's confused my grub loader.

On boot up i get something akin to as follows: -

Ubuntu 9.04
Ubuntu 9.04 Recovery
Mem Test
-other operating systems-
Ubuntu 9.01
Ubuntu 9.04 Recovery
Mem Test

The top set of 'Ubuntu 9.04's are actually KUbuntu, the bottom set being regular lovely Gnome UBuntu. As such the default OS is currently Kubuntu but i want to set it as UBuntu.

So i 'sudo gedit /boot/grub/menu.lst' however in it it's missing a 'set'.. and just lists the following: -

> [B]title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        cd29c2e0-f692-4847-9572-bef3e56baa03
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cd29c2e0-f692-4847-9572-bef3e56baa03 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        cd29c2e0-f692-4847-9572-bef3e56baa03
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cd29c2e0-f692-4847-9572-bef3e56baa03 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        cd29c2e0-f692-4847-9572-bef3e56baa03
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 7 (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
[/B]I'm lost.... i assume there are now two instances of Grub, one of which (elswhere) has the references to normal UBuntu and the one above is infact Kubuntu's? It'd help if it listed it's entry as Kubuntu as well... would make things easier to spot!

How can i sort this out?

---

### Post by unutbu on 2009-05-14
When you installed Kubuntu, it created a /boot/grub/menu.lst in the Kubuntu linux partition. Since your GRUB boot menu shows Kubuntu's entries first, I'm guessing that Kubuntu's menu.lst is now controlling your boot process. 

So to make Ubuntu the default boot option, you could
[list]
[*] Run a few grub commands to tell GRUB to look at Ubuntu's menu.lst instead of Kubuntu's. You'll also have to add something like
```

title      	Kubuntu
root       	(hdX,Y)
chainloader +1
```

so Ubuntu knows how to boot Kubuntu. If you'd like more help with the specific commands, post the output of 
```

sudo fdisk -l
```

[*] Boot Kubuntu. Change the line in Kubuntu's /boot/grub/menu.lst that says
```

default 0
```
to```

default 4
```

This will cause the 5th boot entry in Kubuntu's GRUB boot menu to boot by default.
[/list]

The first option has a slight advantage over the second option for the following reason.
If you update your linux kernel under Kubuntu, your Kubuntu menu.lst will change.
Under the first option, GRUB will read Ubuntu's menu.lst first, and read Kubuntu's menu.lst when Kubuntu is chainloaded. By reading Kubuntu's menu.lst before booting Kubuntu, you will not have to manually edit the menu.lst every time the linux kernel is updated.

Under the second option, Ubuntu's menu.lst will never get read. So if you update Ubuntu's linux kernel, you'll have to manually edit Kubuntu's menu.lst to be able to boot the new Ubuntu linux kernel.

---

### Post by joey-elijah on 2009-05-14
Thanks for the reply unutbu! I'm not brave enough (yet!) to trust my own intuition when it comes to grub; nothing worse than a no boot situation! So i'll take you up on your offer of help, if you don't mind. 

I would prefer GRUB to use Ubuntu's menu.lst than Kubuntu's - so what commands do i use to get GRUB reading the right page? 

My drives/partitions look a mess! Please excuse them.. =o P > 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156286976    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb3              27        9729    77939347+   5  Extended
/dev/sdb5            5141        9535    35302774+  83  Linux
/dev/sdb6            9536        9729     1558273+  82  Linux swap / Solaris
/dev/sdb7              27        2465    19591204+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   * 

---

### Post by unutbu on 2009-05-14
Is Ubuntu on sdb5 and Kubuntu on sdb7?
Also, which drive is the BIOS set to boot from first?
That is, on which drive is GRUB currently installed?

---

### Post by joey-elijah on 2009-05-14
> **unutbu said:**
> Is Ubuntu on sdb5 and Kubuntu on sdb7?

Correct.

> **unutbu said:**
> Also, which drive is the BIOS set to boot from first? That is, on which drive is GRUB currently installed?

As far as i am aware it's sdb (the 80GB HDD)

---

### Post by unutbu on 2009-05-14
Okay then. Boot Ubuntu and run
```

gksu gedit /boot/grub/menu.lst
```

Add ```


title      	Kubuntu
root       	(hd1,6)
chainloader +1
```

to the end of the file. Save and exit gedit.

Then, in the terminal, type:
```

sudo grub
root (hd1,4)     # tells GRUB to look on sdb5 for menu.lst
setup (hd1)      # installs GRUB to sdb hard drive

```

---

