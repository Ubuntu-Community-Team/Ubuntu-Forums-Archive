---
title: "[SOLVED] Error 2 on GRUB"
date: 2009-01-07
forum: General Help
---

### Post by _sluimers_ on 2009-01-07
Hi there!

I have an error 2 on GRUB and am forced to boot on my USB stick.
That's the only way my computer will start.
How do I get rid of this problem?

I have a VB8001 with an Award BIOS.
I tried changing all the hd(x,x) in menu.lst and don't know what setting changes might help in BIOS.
My HD is Sata connected 2.5" drive.

---

### Post by caljohnsmith on 2009-01-07
Is your Ubuntu a fresh install, or did you just recently start getting the Grub error 2? And do you get the Grub error 2 before seeing the Grub menu, or after you get the Grub menu and select Ubuntu? In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by _sluimers_ on 2009-01-07
I got the error on a fresh install and before I can see the menu.

Why highlight it if it's already in code tags?

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f1f43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 504 MB, 504365056 bytes
255 heads, 63 sectors/track, 61 cylinders, total 985088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dfb3a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      979964      489951   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ca910c89-825b-4239-a11e-c3121e806f6c" TYPE="ext3" 
/dev/sda5: UUID="52b0c0f6-d978-4340-a9cb-4440006575e8" TYPE="swap" 
/dev/sdb1: LABEL="miniU" UUID="494A-7E0F" TYPE="vfat" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/rogier/.Private on /home/rogier/Private type ecryptfs (rw,ecryptfs_sig=1d37ee1f6124fc9c,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=rogier)
gvfs-fuse-daemon on /home/rogier/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rogier)
/dev/sdb1 on /media/miniU type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

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
# kopt=root=UUID=ca910c89-825b-4239-a11e-c3121e806f6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca910c89-825b-4239-a11e-c3121e806f6c

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ca910c89-825b-4239-a11e-c3121e806f6c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca910c89-825b-4239-a11e-c3121e806f6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ca910c89-825b-4239-a11e-c3121e806f6c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca910c89-825b-4239-a11e-c3121e806f6c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		ca910c89-825b-4239-a11e-c3121e806f6c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ca910c89-825b-4239-a11e-c3121e806f6c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=52b0c0f6-d978-4340-a9cb-4440006575e8 none            swap    sw              0       0

================================== sda1/boot: ==================================

total 12828
drwxr-xr-x  3 root root    4096 2008-12-19 05:47 .
drwxr-xr-x 21 root root    4096 2009-01-07 18:33 ..
-rw-r--r--  1 root root  503560 2008-11-21 00:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-21 00:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 03:24 grub
-rw-r--r--  1 root root 8664083 2008-12-19 05:47 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-21 00:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-21 00:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339712 2008-11-21 00:30 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 03:24 .
drwxr-xr-x 3 root root   4096 2008-12-19 05:47 ..
-rw-r--r-- 1 root root    197 2008-12-19 04:53 default
-rw-r--r-- 1 root root     30 2008-12-19 04:53 device.map
-rw-r--r-- 1 root root   8108 2008-12-19 04:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-19 04:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-19 04:53 installed-version
-rw-r--r-- 1 root root   8712 2008-12-19 04:53 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2008-12-20 09:32 menu.lst
-rw-r--r-- 1 root root   4310 2008-12-19 04:53 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-19 04:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-19 04:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-19 04:53 stage1
-rw-r--r-- 1 root root 121460 2008-12-19 04:53 stage2
-rw-r--r-- 1 root root   9556 2008-12-19 04:53 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-07
It looks like you have Grub correctly installed to the MBR of the sda drive as we would expect since it is a new install. Often a Grub error 2 in your type of situation is due to an issue with how your HDD is set up in BIOS. Can you go into your BIOS and let me know what HDD-related settings you have? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. And are you sure you have the sda drive jumpered correctly? Is it set for master or maybe cable-select? Also, one thing that would be good to do is mark one of your sda drive partitions bootable, because otherwise it can cause problems with some BIOSes. So how about doing:
```
sudo sfdisk -A1 /dev/sda
```
And see if by chance that changes the booting behavior. Let me know how that goes.

---

### Post by _sluimers_ on 2009-01-07
I did the last thing first, because I noticed that in the "RESULTS.txt" file.

I now get a different error now. Drat, I forgot the exact sentence.
It was something like: "Image kernel not found: linux"
and I'm send into the boot program? It shows me this:

boot>

At least the first time. Now I get error 2 again.

I'll search the BIOS now.

The HDD is on IDE channel 2 master auto-detecting 

SATA Controller Mode is IDE
Sata Controller is enabled

IDE DMA transfer access is enabled
IDE prefeych mode is enabled

ACPI suspend type is S1&S3

That's it for LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.\

The jumpers are the same as when I had Hardy running. I am now running Ibix.

---

### Post by caljohnsmith on 2009-01-07
Did you run the sfdisk command from previous post, and if so, did it change anything about your HDD's booting behavior? When you say you are getting a different error, is that when you boot the HDD or when you boot the USB stick? How about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), try using that to restore Grub to the MBR, and see if that makes any difference. Let me know how that goes.

---

### Post by _sluimers_ on 2009-01-07
> Did you run the sfdisk command from previous post
Yes, 
> if so, did it change anything about your HDD's booting behavior?
only the first time, after that it was error 2 again
> is that when you boot the HDD or when you boot the USB stick?
HDD, USB stick booting continues to work fine.


> How about downloading the Super Grub Disk
I'll try, but the USB stick is the only thing besides my HDD my BIOS recognizes. Not my other USB stick, nor my external DVD-ROM drive.

---

### Post by _sluimers_ on 2009-01-09
My USB stick gives an "Error 17: Cannot mount selected partition"
after a "setup (hd3)", so I cannot install supergrub either.

---

### Post by _sluimers_ on 2009-01-09
Okay, I've got that fixed. Now if I reboot in supergrub I get:

```

Booting 'Super Grub Disk'

USBshift
configfile(HD1,0)/boot/sgd/sgd.lst

Error 15: file not found


```

---

### Post by _sluimers_ on 2009-01-09
Okay, solved that problem as well:

So instead I got a Error 25: disk not found

And now have a Error 15 whenever I restart,not even going into supergrub anymore.

---

### Post by _sluimers_ on 2009-01-09
Thank you Cal John Smith and thank **you** Supergrub!

---

### Post by caljohnsmith on 2009-01-09
> **_sluimers_ said:**
> Thank you Cal John Smith and thank **you** Supergrub!
Glad to hear you got it working; cheers and have fun with Ubuntu. :)

---

