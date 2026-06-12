---
title: "[SOLVED] Help with modifying bootloader."
date: 2008-12-30
forum: General Help
---

### Post by JamilD on 2008-12-30
Hi All,

I'm new to Ubuntu and the general operating system of Linux, and well, this is what happened.

I have 2 hard drives, one of about 350GB and one about 35GB. The larger one has windows installed, and as of yesterday, the smaller one has Ubuntu (the one I'm on right now). But the Ubuntu bootloader was installed on the primary hard drive [Windows], and now I can't boot into windows. Is there any way that I can "move" the bootloader so that when I choose to boot into the Windows drive, it does exactly that.

Or even better, when I boot into the Windows drive, it gives an option to boot into Ubuntu

Thanks in advance.

---

### Post by JamilD on 2008-12-30
Sorry to bump this thread so soon, but I need help!

---

### Post by oldos2er on 2008-12-30
This is confusing; first you say you can't boot into Windows, then you say when you boot Windows there's an option to boot Ubuntu? Did you install with Wubi? Or install from the LiveCD and booting via Grub?

---

### Post by ByKeLaO on 2008-12-30
Just to clarify (correct me if I'm wrong):
Your primary disk is the 350GB one that has Windows installed.
Your secondary disk is the 35GB one with Ubuntu.
The Ubuntu installer put GRUB onto the primary hard disk, overwriting the Windows bootloader, and the Windows option in the GRUB menu does not work.

Could you show us your /boot/grub/menu.lst file so we can have a look at it? Perhaps the Ubuntu installer messed up the GRUB configuration (it did that to me too :()

---

### Post by sekander94 on 2008-12-30
What do you mean by you can't boot into windows? When you turn on your computer, does it prompt you for an operating system?

Post the contents of /boot/grub/menu.lst

---

### Post by JamilD on 2008-12-30
Yeah, that's what happened. And the menu.lst is this:

```
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
# kopt=root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4a07d888-81d1-4e28-aa7c-3c08e1090d69

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

EDIT: When I choose the HD to boot into, when I select the 30GB one, it doesn't do anything, just waits.
When I choose the 350GB one, it boots Ubuntu. Thanks for your help so far!

There's not even a Windows XP Media Center edition selection in the bootloader.

---

### Post by ByKeLaO on 2008-12-30
Here's what happened:
Most people don't like using the BIOS to select their startup disk, so they use a bootloader like GRUB. In your case Ubuntu has put GRUB on your primary disk. When you boot the disk it *should* let you choose which installation to boot into, but your menu.lst file has been configured wrong so that doesn't work.
Please open gedit as an administrator (type "gksudo gedit" in the terminal and enter your password), open the /boot/grub/menu.lst file and change this line:
```
hiddenmenu
```
to this:
```
# hiddenmenu
```

This will allow you to choose which OS to boot into.
Next, add this to the bottom of the file:

```
title		Other operating systems:
root
title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

That tells GRUB where to find your Windows installation.

---

### Post by JamilD on 2008-12-30
Thank you so much. I'm rebooting now to see if it works; I'll edit this post to show you the results.

---

### Post by JamilD on 2008-12-30
Looks like everything went well; but one problem. When I try and boot into windows, it gives me an error: NTDLR is Missing, Press Ctrl+Alt+Del to restart.

Thanks again in advance and for your help

---

### Post by ByKeLaO on 2008-12-30
Provided both your disks are SATA disks, please post the output of this command:
```
fdisk -l /dev/sdb
```

If they are not, please let me know so I can change the command

---

### Post by JamilD on 2008-12-30
```
cannot open /dev/sdb
```

How can I find what kind of disks they are?

Thanks again.

---

### Post by JamilD on 2008-12-30
sorry to bump again, but...
bump.

---

### Post by ByKeLaO on 2008-12-30
OK, post the output of these commands:
```
ls /dev/sd*
ls /dev/hd*
sudo fdisk -l
```
fdisk -l will tell you what your Ubuntu disk is called (probably /dev/sda or /dev/hda but it may be different)
The other 2 commands will tell you what hard disks you have in your computer, and what partitions your hard disks have.

---

### Post by JamilD on 2008-12-30
Okay, I got a not found for /dev/hd*, and here are the others:

ls /dev/sd*
```
/dev/sda   /dev/sda2  /dev/sdb   /dev/sdc   /dev/sdd  /dev/sdf
/dev/sda1  /dev/sda5  /dev/sdb1  /dev/sdc1  /dev/sde

```

sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf093f093

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4661    37439451   83  Linux
/dev/sda2            4662        4866     1646662+   5  Extended
/dev/sda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4a106f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       43776   351630688+   7  HPFS/NTFS

Disk /dev/sdc: 8078 MB, 8078491136 bytes
8 heads, 32 sectors/track, 61633 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       61634     7889135+   b  W95 FAT32

```

---

### Post by ByKeLaO on 2008-12-30
Ah, it looks like your Windows XP partition is a logical partition. Open your menu.lst file as an administrator again, and delete the line
```
makeactive
```
From the end of your file.

---

### Post by JamilD on 2008-12-30
EDIT: Forget everything I typed here.

---

### Post by ByKeLaO on 2008-12-30
1. Does it allow you to boot into Windows XP now?
2. Would you also like to add your other Windows installation to the boot menu?

---

### Post by JamilD on 2008-12-30
1. Same error :( Is it a prob with the Windows installation; it worked fine yesterday.

2. I'm fine; I just want to boot into my major windows installation (the one with the 350GB).

---

### Post by ByKeLaO on 2008-12-30
damn.
Do you still have the original Windows XP disk? If you do, then here's what we'll do:
1. Reinstall the Windows bootloader
2. Install GRUB into the master boot record of your Linux disk and make it bootable

---

### Post by JamilD on 2008-12-30
How do i go about doing these? [Sorry I'm new at this]

I have the WinXP disk.

Is 1. Like :

```
bootcfg /rebuild
fixboot
fixmbr

```

from recovery console?

---

### Post by ByKeLaO on 2008-12-30
It should be easy. Just pop in the Windows disk, boot onto it and press R to enter the recovery system.
Select your Windows XP installation and type in your administrator password.
Type in "fixmbr" and accept the scary warning message it gives you.
Reboot to make sure it worked, then we'll try and get Ubuntu working again.

EDIT: looks like you beat me to it. Fixmbr should be enough, but if that doesn't work you could try the other 2 commands aswell, they may help.

---

### Post by JamilD on 2008-12-30
Okay... i'll try that

sorry i posted earlier...

---

### Post by ByKeLaO on 2008-12-30
Did fixmbr not work?

---

### Post by JamilD on 2008-12-30
The administrator password did not work! Should I try a complete reinstall with backup?

Are you sure there is no way to fix using the menu file?

---

### Post by ByKeLaO on 2008-12-30
I feared that might happen. It's a bug in Windows XP, check out this link: [http://support.microsoft.com/default.aspx?scid=kb;EN-US;308402](http://support.microsoft.com/default.aspx?scid=kb;EN-US;308402)
I'm sure there must be a way to get this working using GRUB. Give me a few minutes to look into it and I'll edit this post when I'm done.

---

### Post by caljohnsmith on 2008-12-30
> **JamilD said:**
> The administrator password did not work! Should I try a complete reinstall with backup?
You shouldn't need to do a reinstall to fix your MBR. :) How about instead booting your Live CD, open a terminal (Applications > accessories > terminal) and do:
```
sudo lilo -M  /dev/sdb mbr
```
That will restore a Windows MBR to your sdb Windows drive. How about giving that a shot and let me know how it goes.

---

### Post by JamilD on 2008-12-30
I'm on Ubuntu right now, so I'm going to type the above command in terminal.

---

### Post by ByKeLaO on 2008-12-30
Argh!
The way I told you to set up GRUB's menu.lst file only works if Windows is on the same hard disk as Linux!
Open up gedit as an administrator again and replace the Windows entry with this:
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

EDIT: Somebody beat me :(
If you want to use the BIOS to select the boot disk then try caljohnsmith's suggestion. If you want to have a GRUB bootloader, try mine :D

---

### Post by JamilD on 2008-12-30
When I tried your's [RobinJam], it gave me Error 13: Invalid or unsupported executable format, and then returns me to the GRUB selection screen.

again, here's my added code to menu.lst:
```

title		Other operating systems:
root
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

```

---

### Post by caljohnsmith on 2008-12-30
JamilD, in order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by JamilD on 2008-12-30
RESULTS.txt
```
============================= Boot Info Summary: ==============================

 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for its boot files.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Win_98
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf093f093

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    74878964    37439451   83  Linux
/dev/sda2        74878965    78172289     1646662+   5  Extended
/dev/sda5        74879028    78172289     1646631   82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4a106f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   703261439   351630688+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 8078 MB, 8078491136 bytes
8 heads, 32 sectors/track, 61633 cylinders, total 15778303 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    15778302     7889135+   b  W95 FAT32

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4a07d888-81d1-4e28-aa7c-3c08e1090d69" TYPE="ext3" 
/dev/sda5: UUID="4403481a-dc5a-4b2e-a37a-71a27a7d47b4" TYPE="swap" 
/dev/sdb1: UUID="B474870F7486D390" TYPE="ntfs" 
/dev/sdc1: UUID="6413-0209" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamil)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jamil)

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4a07d888-81d1-4e28-aa7c-3c08e1090d69

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4a07d888-81d1-4e28-aa7c-3c08e1090d69
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4a07d888-81d1-4e28-aa7c-3c08e1090d69 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=4403481a-dc5a-4b2e-a37a-71a27a7d47b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11940
drwxr-xr-x  3 root root    4096 2008-12-29 22:18 .
drwxr-xr-x 20 root root    4096 2008-12-29 21:59 ..
-rw-r--r--  1 root root  507665 2008-10-24 04:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 04:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-30 20:32 grub
-rw-r--r--  1 root root 8169016 2008-12-29 22:18 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 04:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 04:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 04:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2008-12-30 20:32 .
drwxr-xr-x 3 root root   4096 2008-12-29 22:18 ..
-rw-r--r-- 1 root root    197 2008-12-29 21:59 default
-rw-r--r-- 1 root root     45 2008-12-29 21:59 device.map
-rw-r--r-- 1 root root   8108 2008-12-29 21:59 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-29 21:59 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 21:59 installed-version
-rw-r--r-- 1 root root   8712 2008-12-29 21:59 jfs_stage1_5
-rw-r--r-- 1 root root   4424 2008-12-30 20:32 menu.lst
-rw-r--r-- 1 root root   4406 2008-12-30 19:53 menu.lst~
-rw-r--r-- 1 root root   4310 2008-12-30 18:23 menu.lst_backup
-rw-r--r-- 1 root root   7352 2008-12-29 21:59 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-29 21:59 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 21:59 stage1
-rw-r--r-- 1 root root 121460 2008-12-29 21:59 stage2
-rw-r--r-- 1 root root   9556 2008-12-29 21:59 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
```

Thanks again.

It also created a boot_info_script.txt, here it is:
```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  12/27/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs and some fats displays the offset of the partition
#            as recorded  in  the boot sector (no booting fats
#            seems to use 0 as the offset)
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -V"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Test the script on different distros.
#   Use command line options, to choose what information to display.
#   On vfat partition "ntldr" and "ntdetect.com" are 
#       list in all lowercase and in all caps
#   Fat partition used for booting seem to record
#        the offset in the same place as NTFS partition. But
#        needs to be examined more closely.
#   Rewrite the whole script. Use functions instead of copying and pasting 
#         whole blocks of codes. Add comments.  

Boot_Codes_Dir="
    /
    /NST/
    "

Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /NST/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done
		echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1; }

Dir=$(cd $(dirname $0);pwd);

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt



exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );

echo '============================= Boot Info Summary: =============================='; echo
for drive in  $All_Hard_Drives;
do
        size=$(sfdisk -s $drive);        
        if [ 0 -lt $size 2>>$Trash ];
	then
	 Hard_Drives=$Hard_Drives" "$drive; 
        else
          echo " => Drive $(basename $drive) does not have a valid partition table."
    fi;
done;

for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt $((2*$(sfdisk -s $hdd))) ]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a stage2 file is at this location on $stage2_hdd\) and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message the same partition) 
                        else
                           Message=$(echo $Message partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message and looks on the same drive in partition \#$pa for its boot files.)
              else
               Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	fceb) BL=Bootit;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
 
    done
    echo;

for drive in $Hard_Drives;
 do
for part  in  $(ls $drive?* 2>>$Trash)
   do
      BSI=""      
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo $name: _________________________________________________________________________; echo
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 

          Bytes8081=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
          case $Bytes8081  in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
		      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file);
                    
                        if [ "$pa" = T  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
           if [[ "$type" = "ntfs"  ||   "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"   ]] ;
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to the info in the boot sector, $name starts at sector $offset.)   
      fi;


            echo "    Boot sector type:  "$BST
       if  mount $part $name 2>$Mount_Error; then
       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS="Windows XP"
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue) && OS=${OS%%\\*}
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              if ! [ -h $name$file ];
              then
                 cat $name$file >> $Log1;
              fi;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


       for file in $Boot_Dir;
       do
          if [ -d $name$file ];
          then
	      BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
             
	  fi;
       done;

       for file in $Boot_Codes_Dir
       do
	   if [ -d $name$file ];
	   then  
		  for loader in $( ls  $name$file );
		  do
                   if [ -f $name$file$loader ];
		   then		     
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		      sig=$(hexdump -s 0x17f -n 4  -e '4/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "GRUB" ];
                      then
                          offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $name$file$loader 2>>$Trash);
                          dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $name$file$loader);
                          pa=-1
                          for hdd in $Hard_Drives;
		          do
                             if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			     then
		                  tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                                  if [ "$tmp" = 3be5652 ];
                                  then
                                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                                       stage2_hdd=$hdd
                                   fi;
		              fi;
                           done;
                           dr=$((dr-127))
                            BSI=$(echo $BSI Grub in the file $file$loader  looks at sector $offset )        
                           if [ "$dr" = 128 ];
                           then
                                BSI=$(echo $BSI of the same hard drive) 
                           else
                                BSI=$(echo $BSI on boot drive \#$dr)
		           fi;
                           BSI=$(echo $BSI for the stage2 file);
                    
                           if [ "$pa" = T  ]
		           then
		                BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                           else
                                 pa=$((pa+1))
                                 BSI=$(echo $BSI  \(a stage2 file is at this location on $stage2_hdd\)  and on )                       
                                 if [ "$pa" = 256 ];
                                 then
                                     BSI=$(echo $BSI the same partition) 
                                 else
                                       BSI=$(echo $BSI partition \#$pa )
	                         fi;
                                 BSI=$(echo $BSI for menu.lst.)
                            fi;
                         fi;
 		       fi;
		  done;
              fi;
           done
 
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      echo "    Operating System:  "$OS
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
     umount $name || umount -l $name; 
     else
     echo "    Mounting failed:";  
     cat $Mount_Error 
     fi;
     fi;
     echo;
 
     done;
     done;

echo '=========================== Drive/Partition Info: ============================='; echo
for drive in $All_Hard_Drives;
 do
     echo "Drive $(basename $drive): _____________________________________________________________________"
     echo
     echo "fdisk -lu $drive:"
     fdisk -lu $drive;
     echo;
     echo "sfdisk -V $drive:"; echo
     sfdisk -V $drive 2>&1
     echo   
 done
echo "blkid -c /dev/null: ____________________________________________________________"; echo
blkid -c /dev/null
echo;
echo '=============================== "mount" output: ==============================='; echo
mount
echo >> $Log1
echo "=============================== StdErr Messages: ===============================">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
[ -s $Error_Log ] && cat $Error_Log || echo "No errors were reported."
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile) located in $Dir


```

---

### Post by ByKeLaO on 2008-12-30
It seems that someone in this thread: [http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)
had the same problem as you. This fixed it in their case:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by JamilD on 2008-12-30
Same error again :( :(

Error 13.

EDIT: if I use caljohnsmith's idea of things:
```
sudo lilo -M  /dev/sdb mbr
```

will i be able to select which HD i want, and It'll boot into Win or Ubuntu?

---

### Post by caljohnsmith on 2008-12-30
Can you set your BIOS to boot your sda Ubuntu drive on start up? That would be ideal, because right now you are booting the sdb Windows drive on start up which has Grub in its MBR. If you can change your BIOS to boot the Ubuntu drive, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
That will install Grub to the MBR of your Ubuntu sda drive so it should be bootable. Also, it doesn't appear you successfully restored a Windows MBR to your sdb drive, so I would run the "lilo" command I gave in my previous post to fix that. If Ubuntu complains that lilo is not installed, do the following:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sdb mbr
```
Also, your Windows entry won't work unless you boot the Ubuntu drive instead of the Windows drive like you are currently doing. So try the above steps, reboot, set your BIOS to boot the sda Ubuntu drive, and let me know how far you get.

---

### Post by ByKeLaO on 2008-12-30
In that case I'm gonna step back and let someone else with more experience help you :(
I really hope you get this fixed, but just in case you don't, you can boot into your Windows XP installation using a Super GRUB disk: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Good luck!

---

### Post by JamilD on 2008-12-30
I did all that you suggested. Rebooting now.

Thanks to robinjam for all his help.

---

### Post by JamilD on 2008-12-30
I'm back to the error I got previously:

NTDLR Missing, Ctrl+Alt+Del to reboot.

EDIT: Ubuntu boots fine, Windows makes me get that error. And I can't get into recovery console.

So is this a problem w/ Windows? It worked fine yesterday before Ubuntu Install.

---

### Post by caljohnsmith on 2008-12-30
Looking over the output of that script you ran, I see the problem is that your Windows partition is missing its boot files; that's unfortunately why you are getting a "NTLDR missing error." I've attached the boot files you need to this post, so just download the "WinXP_boot_files1.zip" to your Ubuntu desktop and do:
```
sudo mount /dev/sdb1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt

```
Reboot, try to boot XP from Grub again, and let me know what happens.

---

### Post by JamilD on 2008-12-30
Okay trying now. If this doesn't work, I will have to go. Thanks for your help, and when I come back, is it okay if I send you a PM?

Thanks.

---

### Post by JamilD on 2008-12-30
It worked! What a relief! Thank you guys so much; this is one of the most helpful forums I've come across.

---

### Post by caljohnsmith on 2008-12-30
Glad that worked OK; cheers and enjoy your dual-boot setup. :)

---

### Post by ByKeLaO on 2008-12-30
I'm glad you got everything sorted out.
Unless you have any more questions, go to the top of this page and under "Thread tools" click "Mark thread as solved".
Have fun with Ubuntu and welcome to the community!

---

