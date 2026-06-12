---
title: "GRUB question"
date: 2009-01-25
forum: General Help
---

### Post by sinamorawej on 2009-01-25
Hi - sorry if i'm repeating a question here, i did look around and nothing seem to be related. Here is the problem:

I've installed Ubuntu on my SATA drive and have xp on my ide drive. In my grub menu on bootup i get both ubuntu and xp but when i select any them  grub comes back with error 17. The only way around this is to mess around with boot order of the drives until something works. Here is what fdisk -l says:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f123f11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

To me this is totally wrong! My ntfs should be on sdb (ide drive) and linux on sda1. Any ideas??

---

### Post by dcstar on 2009-01-25
> **sinamorawej said:**
> Hi - sorry if i'm repeating a question here, i did look around and nothing seem to be related. Here is the problem:

I've installed Ubuntu on my SATA drive and have xp on my ide drive. In my grub menu on bootup i get both ubuntu and xp but when i select any them  grub comes back with error 17. The only way around this is to mess around with boot order of the drives until something works. Here is what fdisk -l says:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f123f11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

To me this is totally wrong! My ntfs should be on sdb (ide drive) and linux on sda1. Any ideas??

Post the contents of the /boot/grub/menu.lst file.

---

### Post by sinamorawej on 2009-01-25
> **dcstar said:**
> Post the contents of the /boot/grub/menu.lst file.
# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2009-01-25
Do you know which drive you are booting on start up? In order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by sinamorawej on 2009-01-25
> **caljohnsmith said:**
> Do you know which drive you are booting on start up? In order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Following is the result - I can change the boot order from bios however, the order seem to default to SATA drive after few boot ups and this causes (i guess) grub to become completely inactive and give error 17.

```



============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f123f11

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  149,838,254  149,838,192  83 Linux
/dev/sda2        149,838,255  156,296,384    6,458,130   5 Extended
/dev/sda5        149,838,318  156,296,384    6,458,067  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaed475

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63  120,085,874  120,085,812   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b3ea3a4d-fac3-4d80-8d8a-4db409b61651" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="acabc988-44b7-4992-834c-0cb350c7a37d" 
/dev/sdb1: UUID="F60CA56A0CA52699" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=acabc988-44b7-4992-834c-0cb350c7a37d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  30.5GB: boot/grub/menu.lst
  30.5GB: boot/grub/stage2
  30.5GB: boot/initrd.img-2.6.24-23-generic
  30.5GB: boot/initrd.img-2.6.24-23-generic.bak
  30.4GB: boot/vmlinuz-2.6.24-23-generic
  30.5GB: initrd.img
  30.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-25
OK, you have Grub installed to the MBR (Master Boot Record) of both your drives, but your menu.lst is currently configured for when you boot the sdb Windows drive on start up. I would recommend changing your menu.lst so you can boot the Ubuntu sda drive on start up instead, and then restore a Windows MBR to your sdb drive; that way your drives will be independent as far as booting is concerned, so if anything happens to one of them, you should be able to boot the other one just fine. If that sounds good, how about doing:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```
Also change the "# groot..." line to:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Next change your Windows entry at the bottom to:
```
title    Microsoft Windows XP Professional
root	 (hd1,0)
map      (hd1) (hd0)
map      (hd0) (hd1)
chainloader	+1
```
And lastly, to restore a Windows MBR to your Windows drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
Reboot, make sure your BIOS is set to boot the sda Ubuntu drive on start up, and let me know how far you get. We can work from there if necessary.

---

### Post by sinamorawej on 2009-01-25
> **caljohnsmith said:**
> OK, you have Grub installed to the MBR (Master Boot Record) of both your drives, but your menu.lst is currently configured for when you boot the sdb Windows drive on start up. I would recommend changing your menu.lst so you can boot the Ubuntu sda drive on start up instead, and then restore a Windows MBR to your sdb drive; that way your drives will be independent as far as booting is concerned, so if anything happens to one of them, you should be able to boot the other one just fine. If that sounds good, how about doing:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b3ea3a4d-fac3-4d80-8d8a-4db409b61651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```
Also change the "# groot..." line to:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Next change your Windows entry at the bottom to:
```
title    Microsoft Windows XP Professional
root	 (hd1,0)
map      (hd1) (hd0)
map      (hd0) (hd1)
chainloader	+1
```
And lastly, to restore a Windows MBR to your Windows drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
Reboot, make sure your BIOS is set to boot the sda Ubuntu drive on start up, and let me know how far you get. We can work from there if necessary.

everything worked fine (i managed to boot both xp and linux with the new settings) until i restored the mbr on windows partition - now when i boot it tells me No Boot Signature Found on Partition.

---

### Post by caljohnsmith on 2009-01-25
OK, how about posting:
```
sudo fdisk -lu
```
And can you boot the sda drive on start up still and get the Grub menu, or do you always get the "no boot signature" error?

---

### Post by sinamorawej on 2009-01-25
> **caljohnsmith said:**
> OK, how about posting:
```
sudo fdisk -lu
```
And can you boot the sda drive on start up still and get the Grub menu, or do you always get the "no boot signature" error?


no - i don't get to grub anymore.



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f123f11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaed475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   120085874    60042906    7  HPFS/NTFS

---

### Post by caljohnsmith on 2009-01-25
I think the problem might be that your drive letters are changing, because in your first post, Ubuntu is on sdb, but the in subsequent posts Ubuntu is on sda. How about doing the fdisk command again just to make sure Ubuntu is on sda, and then do the following to restore Grub to that drive:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sda[/COLOR]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
So if Ubuntu is actually on the sdb drive, just replace sda with sdb above. Reboot, and let me know how far you get.

---

### Post by sinamorawej on 2009-01-25
> **caljohnsmith said:**
> I think the problem might be that your drive letters are changing, because in your first post, Ubuntu is on sdb, but the in subsequent posts Ubuntu is on sda. How about doing the fdisk command again just to make sure Ubuntu is on sda, and then do the following to restore Grub to that drive:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sda[/COLOR]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
So if Ubuntu is actually on the sdb drive, just replace sda with sdb above. Reboot, and let me know how far you get.

everything workes now! thanks for all your help :)

---

### Post by sinamorawej on 2009-01-25
> **caljohnsmith said:**
> I think the problem might be that your drive letters are changing, because in your first post, Ubuntu is on sdb, but the in subsequent posts Ubuntu is on sda. How about doing the fdisk command again just to make sure Ubuntu is on sda, and then do the following to restore Grub to that drive:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sda[/COLOR]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
So if Ubuntu is actually on the sdb drive, just replace sda with sdb above. Reboot, and let me know how far you get.

cool, all working now! thanks for all your help :)

---

