---
title: "Grub Error 17 when a USB drive is present"
date: 2009-01-30
forum: General Help
---

### Post by jychuah on 2009-01-30
Hi,

When I boot up my computer with a USB hard drive or pen drive attached my computer gives me a GRUB error 17. I can resolve this issue by removing the drive and then booting up, but it's less than convenient. Is there a way to correct this error, perhaps by simply re-installing GRUB from an xterm while the drive is plugged in and mounted? It's a little annoying to have to remove every USB storage device to get Linux to boot.

If necessary, i can post the results of the boot_info_script i've found on these forums.

Thanks.

---

### Post by caljohnsmith on 2009-01-30
It sounds like the issue is that your your USB drive is before your Ubuntu drive in the BIOS boot order. How about checking your BIOS boot order and see if that is the case, and if so, change it so your Ubuntu drive boots before any USB drive. I think that will solve your problem, but let me know how it goes.

---

### Post by jychuah on 2009-01-31
My BIOS (for a Gigabyte GA-K8NS-939-F2) registers the USB hard drive as just a plain vanilla hard drive instead of as a USB device. Unfortunately, I can't make the BIOS ignore it. However, it's still at the bottom of the list in terms of boot order. If GRUB is loading that would imply that it's reading the boot sector off of the hard drive, wouldn't it? (The USB drive doesn't have a boot loader written to it.)

Is there a workaround for this? Perhaps a setting in /boot/grub/menu.lst that makes GRUB identify boot devices by UUID instead of by logical hard drive order? (i.e., (hd0,1) etc) (Or is UUID of a hard drive dependent on the kernel loading first?)

---

### Post by caljohnsmith on 2009-01-31
It would help to first get more info about your setup related to booting, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Grub error 17 problem might be.

---

### Post by jychuah on 2009-01-31
Here is my RESULTS.TXT. I've unplugged the USBHDD, booted into linux, then plugged the USBHDD back in and mounted it, using device /dev/sdc1. /dev/sdb (on which Linux resides) has previously had Windows installed on it, but has since been formatted and repartitioned.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c347c34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,248,189   156,248,127  83 Linux
/dev/sdb2         156,248,190   171,879,434    15,631,245  82 Linux swap / Solaris
/dev/sdb3         171,879,435   625,137,344   453,257,910   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A264923964921061" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdb1: UUID="1080670c-ed4a-47e7-8256-532115b09a2d" TYPE="ext3" 
/dev/sdb2: UUID="502eb077-5d33-4da5-ab44-b388758be7c8" TYPE="swap" 
/dev/sdb3: UUID="7008568808564CEA" LABEL="E Drive" TYPE="ntfs" 
/dev/sdc1: UUID="C084A5AB84A5A47E" LABEL="FreeAgent Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,noatime,nodiratime,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb3 on /media/E Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jychuah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jychuah)
/dev/sdc1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
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
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1080670c-ed4a-47e7-8256-532115b09a2d /               ext3    relatime,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sdb2
UUID=502eb077-5d33-4da5-ab44-b388758be7c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb3	/media/E\040Drive auto rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

=================== sdb1: Location  of files loaded by Grub: ===================


  67.2GB: boot/grub/menu.lst
  67.1GB: boot/grub/stage2
  67.1GB: boot/initrd.img-2.6.24-19-generic
  67.1GB: boot/initrd.img-2.6.24-19-generic.bak
  67.1GB: boot/initrd.img-2.6.24-21-generic
  67.2GB: boot/initrd.img-2.6.24-21-generic.bak
  67.2GB: boot/initrd.img-2.6.24-22-generic
  67.2GB: boot/initrd.img-2.6.24-22-generic.bak
  67.2GB: boot/initrd.img-2.6.27-11-generic
  72.7GB: boot/initrd.img-2.6.27-9-generic
  67.1GB: boot/vmlinuz-2.6.24-19-generic
  67.1GB: boot/vmlinuz-2.6.24-21-generic
  67.1GB: boot/vmlinuz-2.6.24-22-generic
  67.1GB: boot/vmlinuz-2.6.27-11-generic
  67.2GB: boot/vmlinuz-2.6.27-9-generic
  67.2GB: initrd.img
  72.7GB: initrd.img.old
  67.1GB: vmlinuz
  67.2GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-01-31
It looks like the issue is that you have Ubuntu installed to your sdb drive, yet Grub is installed to the MBR (Master Boot Record) of your sda Windows drive. That means when you can successfully boot into Ubuntu, your sda drive must be first in the BIOS boot order, and your Ubuntu sdb drive must be 2nd. So if attaching a USB drive gives you a Grub error 17, that's means the Ubuntu drive was moved from 2nd in the boot order to maybe 3rd or any other position. Since you can change the BIOS boot order, it is much more ideal if you can just install Grub to the sdb drive (the drive that Ubuntu is on) and boot the sdb drive on start up; that way your drives will be completely independent of each other when it comes to booting, and you shouldn't get a Grub error 17. That also means if anything happens to either the Windows or Ubuntu drive, you should be able to boot the other drive OK. If that sounds good, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
gksudo gedit /boot/grub/menu.lst
```
And then change all your Ubuntu entries to use (hd0,0) instead of (hd1,0) similar to:
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1080670c-ed4a-47e7-8256-532115b09a2d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```
Also change the "# groot=(hd1,0)" line to:
```
# groot=[COLOR="Blue"](hd0,0)
[/COLOR]
```
Then change your Windows entry at the bottom to:
```

title		Windows XP (hd1)
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Windows XP (hd2)
root		(hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```
And lastly, to restore a Windows MBR to your Windows drive, how about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, set your sdb Ubuntu drive to boot first, and let me know how far you get about booting Ubuntu and Windows from your Grub menu. Also try connecting/disconnecting your USB drive and see how that affects booting Ubuntu. We can work from there if necessary.

---

### Post by jychuah on 2009-01-31
linux will now boot fine with USB HDD drive, but when i select the windows option from the grub menu it gives me an error "Unrecognizable device string." which, honestly, isn't the end of the world since i rarely use windows anymore.

thanks for your help so far!

---

### Post by caljohnsmith on 2009-01-31
> **jychuah said:**
> linux will now boot fine with USB HDD drive, but when i select the windows option from the grub menu it gives me an error "Unrecognizable device string." which, honestly, isn't the end of the world since i rarely use windows anymore.

thanks for your help so far!
Great, glad to hear you can at least boot Ubuntu now. Usually an "Unrecognizable device string" error means you have a typo in the Windows entry. Did you add both Windows entries from my previous post? Also, make sure you don't get zero mixed up with the letter O in those entries--the entries use zero in all places. If you still have trouble, please post your menu.lst. Let me know how that goes.

---

