---
title: "Grub Error 17"
date: 2009-04-15
forum: General Help
---

### Post by davideotape on 2009-04-15
I get grub error 17 - cannot mount selected partition. Useful outputs:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29739   238878486    7  HPFS/NTFS
/dev/sda2           29740       30383     5170048    7  HPFS/NTFS
/dev/sda3           30383       30402      148476    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b96ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2373    19061091   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris

```

```
#splashimage=(hd1,0)/boot/grub/splashimages/mac05.xpm.gz
default		4
timeout		4

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2d6eba4a-670f-447e-a46e-1428027e6e5a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=773

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2d6eba4a-670f-447e-a46e-1428027e6e5a ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2d6eba4a-670f-447e-a46e-1428027e6e5a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd0,1)
chainloader +1
savedefault
makeactive

```

Here's the story behind this:

After purchasing a new graphics card for my PC, I decided it would also be a good time to re-install windows. So, I removed sdb so windows didn't mess up my ubuntu installation, and then installed my graphics card on the windows installation. Then, after putting sdb back in, I realised that I was booting from the grub on sda (windows drive) before. So, I tried booting from the grub on sdb, but no luck - I get grub error message 17. Does anyone know how I can solve this?

All help appreciated :D

David

---

### Post by ajgreeny on 2009-04-15
Try restoring grub with the live ubuntu CD.
Boot into the ubuntu live CD
open a terminal and run :
   ```
 sudo grub
```
This gets you to a simple grub command line.  Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hd0,1) ,probably]  then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.  Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by davideotape on 2009-04-15
That seemed to work fine :D (Though I haven't tried booting windows yet)

However, I don't see why I can't get grub to work on the linux partition...

I'm also very impressed that jaunty didn't throw a wobbly over my new graphics card (I changed from a geforce 7500LE to a geforce 9400gt)

Thanks again,

David

---

