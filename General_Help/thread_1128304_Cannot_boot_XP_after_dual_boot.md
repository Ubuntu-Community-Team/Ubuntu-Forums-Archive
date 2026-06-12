---
title: "Cannot boot XP after dual boot"
date: 2009-04-17
forum: General Help
---

### Post by poisoneggs on 2009-04-17
I installed Jaunty on my brother's laptop, then he asked me to also make an XP partition. I have successfully done this in my laptop some time ago (although I use Intrepid). I installed XP, and managed to boot into it, but after restoring the grub, I cannot boot it. Selecting Ubuntu works fine, but selecting XP gives me an error 12, invalid device requested.

here's the output for fdisk -l (not sure what for, but I saw it requested in all the posts I checked)
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82e5f1de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       18562   128616390   83  Linux
/dev/sda3           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris


and here is the content of menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
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
# kopt=root=UUID=ab0370ee-3355-49ac-87f6-213445d47a67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ab0370ee-3355-49ac-87f6-213445d47a67

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
uuid		ab0370ee-3355-49ac-87f6-213445d47a67
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ab0370ee-3355-49ac-87f6-213445d47a67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		ab0370ee-3355-49ac-87f6-213445d47a67
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ab0370ee-3355-49ac-87f6-213445d47a67 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		ab0370ee-3355-49ac-87f6-213445d47a67
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title	Windows XP
root (hd0,0)
makeactive
chainloader +1

Anyone know how to fix this?
Thanks in advance

*EDIT:*I tried root (hd0,0) to (hd0,4) for the XP part, the error 12 comes with the hd0,4. When I had it at hd0,0, it goes to Ubuntu, when it was hd0,1, it said something like 'unsupported format'.

---

### Post by egalvan on 2009-04-17
"fdisk -l" is saying that the first parttion is NTFS, the second is Linux.

The UUID's may be off...

so give us this info to check them...

```
sudo blkid
```

---

### Post by poisoneggs on 2009-04-17
output for sudo blkid

```
/dev/sda5: TYPE="swap" UUID="48571b16-0fb3-41bb-9693-d474a65afdef" 
/dev/sda2: UUID="ab0370ee-3355-49ac-87f6-213445d47a67" TYPE="ext3" 

```

---

### Post by poisoneggs on 2009-04-17
anyone?

---

### Post by poisoneggs on 2009-04-17
Just to clarify, when I tried
root    (hd0,0)
for the XP section, and I select Windows in the GRUB, it reloads the GRUB.
I hate Windows.

---

### Post by poisoneggs on 2009-04-17
Here's some more info in case it helps

This is the content of /etc/fstab

```
 /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ab0370ee-3355-49ac-87f6-213445d47a67 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48571b16-0fb3-41bb-9693-d474a65afdef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

If you require any more info just ask

Thanks

---

### Post by meierfra. on 2009-04-17
> When I had it at hd0,0, it goes to Ubuntu

It sound like, you installed grub to the boot sector of your windows partition.

You can use testdisk to restore the boot sector:

Download the testdisk-6.10.linux26.tar.bz2 package to your Ubuntu desktop, and then do:


```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda
```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm

then press "q" a few times to quit testdisk,



You also need to install grub to the MBR:


```
sudo grub
```
and at the "grub>" prompt:


```
root (hd0,1)
setup (hd0)
quit
```

---

### Post by poisoneggs on 2009-04-17
Thanks for the reply, I'll post an update once I try this.

---

### Post by poisoneggs on 2009-04-17
Wow, thanks a lot, that did it :)
If you have the time, could you tell me what the problem was? I followed the steps but I didn't really understand what was going on.
Thank you very much for your help

---

### Post by meierfra. on 2009-04-17
> that did it
Great.

> could you tell me what the problem was? 

The boot sector  of the Windows partition is  the first sector of that partition. It contains  data necessary to boot XP.
You must have installed grub to the XP boot sector. Did you do "grub-install /dev/sda1"  or "root (hd0,1), setup (hd0,0)" ?
So the boot sector now contained instructions to load the Grub menu and every time you tried to boot XP, you got the Grub menu instead.

Luckily XP keeps a backup of the boot sector in the last sector of partition. testdisk just looks for that backup boot sector and uses it to restore the original boot sector.

---

