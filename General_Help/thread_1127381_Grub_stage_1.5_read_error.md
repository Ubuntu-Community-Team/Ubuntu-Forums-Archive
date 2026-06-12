---
title: "Grub stage 1.5 read error"
date: 2009-04-16
forum: General Help
---

### Post by Modoc on 2009-04-16
I get error: here is a dump of my configuration:
I am currently running off a CD.
Any help would be appreciated

Regards,


# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=d0eb93c4-a543-4d3a-9445-948d945009a0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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


title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0eb93c4-a543-4d3a-9445-948d945009a0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d0eb93c4-a543-4d3a-9445-948d945009a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=834d6847-1a99-4f32-bd6c-917d94f8152f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== hda1: Location of files loaded by Grub: ===================


   6.9GB: boot/grub/menu.lst
   6.9GB: boot/grub/stage2
   6.8GB: boot/initrd.img-2.6.22-14-generic
   6.8GB: boot/initrd.img-2.6.22-14-generic.bak
   6.9GB: boot/initrd.img-2.6.22-15-generic
   6.9GB: boot/initrd.img-2.6.22-15-generic.bak
   6.8GB: boot/initrd.img-2.6.24-19-generic
   6.9GB: boot/initrd.img-2.6.24-19-generic.bak
   6.9GB: boot/initrd.img-2.6.24-21-generic
   6.8GB: boot/initrd.img-2.6.24-21-generic.bak
   6.9GB: boot/initrd.img-2.6.24-22-generic
   6.9GB: boot/initrd.img-2.6.24-22-generic.bak
   6.9GB: boot/initrd.img-2.6.24-23-generic
   6.9GB: boot/initrd.img-2.6.24-23-generic.bak
   6.9GB: boot/vmlinuz-2.6.22-14-generic
   6.9GB: boot/vmlinuz-2.6.22-15-generic
   6.8GB: boot/vmlinuz-2.6.24-19-generic
   6.9GB: boot/vmlinuz-2.6.24-21-generic
   6.8GB: boot/vmlinuz-2.6.24-22-generic
   6.9GB: boot/vmlinuz-2.6.24-23-generic
   6.9GB: initrd.img
   6.9GB: initrd.img.old
   6.9GB: vmlinuz
   6.8GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hda2



=============================== StdErr Messages: ===============================

hexdump: /dev/hda2: No such file or directory
hexdump: /dev/hda2: No such file or directory

---

### Post by meierfra. on 2009-04-16
Could you please post the whole RESULTS.txt? The top half seems to be missing.

---

### Post by Modoc on 2009-04-16
> **meierfra. said:**
> Could you please post the whole RESULTS.txt? The top half seems to be missing.

Maybe I have a hardware problem because the problem is intermitant.
Today when I came home, the computer just booted up on its own.

I did to an FSCK this morning, however, this did not fix the problem.
Maybe it is the humidity?

Thanks
Barry

---

