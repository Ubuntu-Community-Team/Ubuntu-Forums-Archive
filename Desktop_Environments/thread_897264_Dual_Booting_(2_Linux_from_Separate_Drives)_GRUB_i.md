---
title: "Dual Booting (2 Linux from Separate Drives) GRUB issue."
date: 2008-08-22
forum: Desktop Environments
---

### Post by RensoreK on 2008-08-22
Hello everyone! 

I'm currently using PCLinuxOS and I want to dual boot with Ubuntu. The problem is Ubuntu is already installed on (hdb1 (/root), hdb6(/home)) and PCLinuxOS is on hda2(/root),hda3(/home). Problem is Grub does not see Ubuntu. Even though when I use the SuperGrub disk, it does see the Ubuntu partitions. Do I need to create some complicated /boot partition to make this work? I am entirely lost. Or would I need to somehow edit the Grub menu to find Ubuntu (Seems more logical?) If so, can someone help me get about doing this?

---

### Post by sandysandy on 2008-08-22
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

and [COLOR="Blue"]gksudo gedit /boot/grub/menu.lst[/COLOR]

u will need to add the Ubuntu entry manually to PC linux GRUB or the other way around.


regards

---

### Post by RensoreK on 2008-08-22
**fdisk -lu**

```


Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     4209029     2104483+  82  Linux swap / Solaris
/dev/hda2   *     4209030    46154744    20972857+  83  Linux
/dev/hda3        46154745   312576704   133210980   83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    41849324    20924631   83  Linux
/dev/hdb2        41849325   234436544    96293610    5  Extended
/dev/hdb5       224829738   234436544     4803403+  82  Linux swap / Solaris
/dev/hdb6        41849451   217295189    87722869+  83  Linux
/dev/hdb7       217295253   224829674     3767211   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641   83  Linux

Disk /dev/sdb: 4102 MB, 4102887936 bytes
127 heads, 62 sectors/track, 1017 cylinders, total 8013453 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     8007857     4003898    b  W95 FAT32

```

**contents of grub**

```
timeout 5
color black/cyan yellow/cyan
gfxmenu (hd0,1)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title PCLinuxOS 2007
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=PCLinuxOS_2007 root=/dev/hda2  acpi=on splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

title PCLinuxOS -noframebuffer
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=PCLinuxOS_-noframebuffer root=/dev/hda2  acpi=on
initrd (hd0,1)/boot/initrd.img

title PCLinuxOS Failsafe Mode
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=PCLinuxOS_Failsafe_Mode root=/dev/hda2  failsafe acpi=on
initrd (hd0,1)/boot/initrd.img
```

---

### Post by sandysandy on 2008-08-22
first [COLOR="Red"]BACKUP menu.lst file[/COLOR]

[COLOR="Green"]open [/COLOR][COLOR="Blue"]menu.lst[/COLOR] file of Ubuntu and [COLOR="Green"]copy the ubuntu entries[/COLOR] into menu.lst of PC linux.

[COLOR="Blue"]or[/COLOR] try adding this to menu.lst of PC linux

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5535979e-6581-4c96-a1b1-13a0bf803445 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

[COLOR="Red"]or[/COLOR]

u can copy the PC linux entries into Ubuntu menu.lst and then with super grub disk restore ubuntu's GRUB.

Remember to [COLOR="Red"]BACKUP menu.lst FILES[/COLOR]
regards

---

### Post by RensoreK on 2008-08-22
sandysandy thanks. I fixed it by booting from the liveCD, copying the menu.lst from ubuntu and pasting it in the primary drives MBR grub (PCLinuxOS), now reads:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9cd41300-5dc0-4adf-b832-d01162224030 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

---

