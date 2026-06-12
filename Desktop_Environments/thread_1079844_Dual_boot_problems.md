---
title: "Dual boot problems"
date: 2009-02-24
forum: Desktop Environments
---

### Post by ncalkins on 2009-02-24
I'm a relatively new Linux user, but I've caught on pretty quickly from reading forums.  I ran into a few different problems while trying to set up my desktop to dual boot Ubuntu 8.10 and Vista.  Here's my menu.lst from Grub (nothing is changed except for the very end):


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
# kopt=root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a0a72047-4f00-454d-a924-af406dcaca1a

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
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/memtest86+.bin
quiet

title           Windows Vista
root            (hd1,1)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST



I've currently got two harddrives --- the first one has an old version of XP (I'm not really using it for anything right now), and the second one is partitioned in two, with Ubuntu on the first partition and Vista on the second.  Ubuntu works fine, but when I select Vista at startup, Grub freezes at "Starting up...".  

Here's the output of fdisk -l:

Cannot open /dev/sda
Cannot open /dev/sdb

I figure this might be part of the problem.  There are actually a few other issues I'm having, but for now I just want to get Vista working.  Any ideas?

---

### Post by caljohnsmith on 2009-02-24
How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Vista entry with:
```
title Windows Vista
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```
Reboot, and let me know if that new Vista entry works or not. We can work from there if necessary.

---

### Post by ncalkins on 2009-02-25
Hmm, that's actually something I recently tried.  I just tried it again, and this time it got about past "starting up" and then flickered, froze on a black screen for a while, and started PC recovery.  The pointer and a desktop background with a mountain loaded, but nothing else and I couldn't ctrl + alt + del so I had to punch it off.  I'm a little afraid to try it again :-?

---

### Post by caljohnsmith on 2009-02-25
OK, I think we're definitely going to need some more information about your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ncalkins on 2009-02-25
Ok, here we go:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 sdb2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 sdb2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 sdb2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 sdb2 ntfs-3g force 0 0

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   375,429,599   375,429,537   7 HPFS/NTFS
/dev/sda2    *    375,444,720   390,715,919    15,271,200   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007710b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   542,547,179   542,547,117  83 Linux
/dev/sdb2    *    542,547,968   958,550,015   416,002,048   7 HPFS/NTFS
/dev/sdb3         958,550,355   976,768,064    18,217,710   5 Extended
/dev/sdb5         958,550,418   976,768,064    18,217,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="47C7A96843588F20" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat" 
/dev/sdb1: UUID="a0a72047-4f00-454d-a924-af406dcaca1a" TYPE="ext3" 
/dev/sdb2: UUID="668071B180718877" TYPE="ntfs" 
/dev/sdb5: UUID="eb643b3f-2a0a-4306-9e10-93e3a304dfaa" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nathan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathan)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


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
# kopt=root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a0a72047-4f00-454d-a924-af406dcaca1a

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
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0a72047-4f00-454d-a924-af406dcaca1a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a0a72047-4f00-454d-a924-af406dcaca1a
kernel		/boot/memtest86+.bin
quiet

title Windows Vista
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0a72047-4f00-454d-a924-af406dcaca1a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=eb643b3f-2a0a-4306-9e10-93e3a304dfaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 243.7GB: boot/grub/menu.lst
 243.8GB: boot/grub/stage2
 243.7GB: boot/initrd.img-2.6.27-11-generic
 243.8GB: boot/initrd.img-2.6.27-7-generic
 243.8GB: boot/initrd.img-2.6.27-9-generic
 243.8GB: boot/vmlinuz-2.6.27-11-generic
 243.7GB: boot/vmlinuz-2.6.27-7-generic
 243.7GB: boot/vmlinuz-2.6.27-9-generic
 243.7GB: initrd.img
 243.8GB: initrd.img.old
 243.8GB: vmlinuz
 243.7GB: vmlinuz.old
```



Thanks for your quick responses!

---

### Post by caljohnsmith on 2009-02-25
It sounds like you may be booting your Vista/Ubuntu sdb drive on start up instead of your sda drive, and if that's the case, you should be using a different entry for Vista in your Grub menu:
```
title Windows Vista
root (hd0,1)
chainloader +1
```
Let me know exactly what happens when you try that entry from your Grub menu, and we can work from there.

---

### Post by ncalkins on 2009-02-25
That worked!  Thanks a lot for your help

---

### Post by caljohnsmith on 2009-02-25
Glad to hear that worked OK; cheers and enjoy your dual-boot Ubuntu/Vista setup. :)

---

