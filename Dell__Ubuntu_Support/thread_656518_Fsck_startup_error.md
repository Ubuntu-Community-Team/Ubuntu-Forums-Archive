---
title: "Fsck startup error"
date: 2008-01-02
forum: Dell  Ubuntu Support
---

### Post by PhoenixBlade on 2008-01-02
Hiya

I'm quite new to ubuntu (configuring it, I've installed it about 5 times on the same computer) (I like having different operating systems on one computer). Now I've managed 4(~5) partitions on my laptop and it comes up with an fsck error when I start up (I just type 'exit' then everything continues normally).

The checkfs file reads: 
```

Log of fsck -C -R -A -a 
Wed Jan  2 21:24:17 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=872771fa-402a-4494-a2cc-40bd3e0be98e'

fsck.ext3: Unable to resolve 'UUID=69d2d46c-9a37-4681-a0da-ea4a3d5f589c'

fsck died with exit status 8

Wed Jan  2 21:24:18 2008
----------------

```

My partitions (from System->Admin->Partition Manager) are as follows: 
/dev/sda1   - ntfs  // Windows XP
/dev/sda3   - unknown  // FreeBSD
/dev/sda2   - extended
  /dev/sda5    - ext3  // Ubuntu (mountpoint: /)
  /dev/sda6    - linux-swap
  unalloc  // Spare

I've looked through other posts related to this, but I'm not sure how to apply their fixes with my situation, but I've run some commands recommended in a similar situation:

ls -l /dev/disk/by-uuid
```

total 0
lrwxrwxrwx 1 root root 10 2008-01-02 21:24 56cb12d5-e6ca-4d26-bba1-0ec05b782f5b -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-02 21:48 72288EC6288E88B5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-02 21:48 a9cb47ca-e1a6-4158-9f3c-873b41e7f005 -> ../../sda6

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=872771fa-402a-4494-a2cc-40bd3e0be98e /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=EC5C85485C850E90 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=69d2d46c-9a37-4681-a0da-ea4a3d5f589c /media/sda3     ext3    defaults        0       2
# /dev/sda6
UUID=57cc525b-5ae1-4e35-918b-9e8e71dca3ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

sudo fdisk -l /dev/sda
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            2819        4211    11189272+   f  W95 Ext'd (LBA)
/dev/sda3            1913        2818     7277445   a5  FreeBSD
/dev/sda5   *        2819        4081    10145016   83  Linux
/dev/sda6            4082        4211     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

And this is the grub menu.lst file (I've edited this myself, just to change defaults and the names displayed):
```

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
# kopt=root=UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=56cb12d5-e6ca-4d26-bba1-0ec05b782f5b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

title		FreeBSD
root		(hd0,2)
makeactive
chainloader	+1

```

Any help would be much appreciated.
Thanks

---

### Post by tgilber1 on 2008-01-02
It looks like your /etc/fsab file has the following:


/dev/sda1 has incorrect filesystem type (ext3) - fdisk has sda1 as a Windows partition

/dev/sda2 is extended partition - should not be in /etc/fstab

/dev/sda3 has incorrect filesystem type (ext3) - fdisk has sda3 as a BSD partition.

Verify proper way of populating /etc/fstab.

check out the following examples and type "man fstab" at the terminal to read manual

/usr/share/doc/mount/examples/fstab
/usr/share/doc/util-linux/examples/fstab.example2
/usr/share/doc/m4/examples/fstab.m4
/usr/share/apps/katepart/syntax/fstab.xml
/usr/share/vim/vim71/syntax/fstab.vim
/usr/share/ubuntu-docs/ubuntu/sample/fstab_automountnetworkfoldersall
/usr/share/ubuntu-docs/ubuntu/sample/fstab_automountfat
/usr/share/ubuntu-docs/ubuntu/sample/fstab_automountnetworkfolders
/usr/share/ubuntu-docs/ubuntu/sample/fstab_automountntfs
/usr/include/fstab.h
/usr/lib/udev/migrate-fstab-to-uuid.sh

---

