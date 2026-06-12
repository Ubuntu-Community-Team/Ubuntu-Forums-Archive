---
title: "Dual Booting Vista and Ubuntu problem!!"
date: 2009-02-19
forum: General Help
---

### Post by bigsicky03 on 2009-02-19
I recently installed Ubuntu on my Toshiba Satellite A135 that was running Vista before.  I partitioned my hard drive through the live CD and and then installed Ubuntu.  I wanted to run a dual boot, but when I went to start up Vista I had a problem.  I came to the screen where you can select either Vista or Ubuntu, went with Vista, and got nothing but black screen saying "Starting..." it just stays there and does nothing.  Went on a few forums to see if I could fix it, ended up messing everything up with the MBR and nothing would start up, but finally got it to where Ubuntu would boot up.  I really like Ubuntu, but would like to have it where I can boot both like I originally wanted to.  Can someone please help me!!!  It is just very frustrating, there are programs for school that can only run with my Windows for class, so any help would be AMAZING!!

---

### Post by avtolle on 2009-02-19
You do have a Vista DVD handy with which to reinstall it, correct?

I suspect that you did not use the Vista tools to resize the Vista drive before partitioning with the Live CD; if this is incorrect, I apologize for the assumption. From reading a whole lot of things on this and other forums, using Gparted, etc.  to resize a Vista drive can often result in a corrputed Vista system, which requires reinstallation to "fix".

---

### Post by caljohnsmith on 2009-02-19
I disagree with avtolle, I don't think we have enough information about your setup yet to urge you to reinstall Vista. I think there is a good chance that Vista is just fine, but may need a few minor fixes in order to boot again. In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by avtolle on 2009-02-19
You are hopefully correct, caljohnsmith, and I apologize to the OP for jumping to a conclusion not, at this time, supported by the information available. 

To anyone reading, here is a link to yet another web page on not using gparted to resize a vista partition: [http://ask.metafilter.com/111364/Partition-troubles](http://ask.metafilter.com/111364/Partition-troubles).

---

### Post by bigsicky03 on 2009-02-19
here is what it came up with


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 3074048. But according to the info from 
                       fdisk, sda2 starts at sector 3084480. The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 287962506 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d702ecc

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,084,480   275,723,594   272,639,115   7 HPFS/NTFS
/dev/sda3         275,723,595   312,576,704    36,853,110   5 Extended
/dev/sda5         275,723,658   310,938,074    35,214,417  83 Linux
/dev/sda6         310,938,138   312,576,704     1,638,567  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="389C406D9C4027A8" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="EC52458E52455F08" LABEL="SQ004286V02" TYPE="ntfs" 
/dev/sda5: UUID="616c20a3-b3de-4595-bbd0-053f72903a2a" TYPE="ext3" 
/dev/sda6: UUID="12df5db7-a545-4993-a0d6-7c970d4ae6ed" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/joshua/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joshua)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=616c20a3-b3de-4595-bbd0-053f72903a2a

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
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=616c20a3-b3de-4595-bbd0-053f72903a2a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		616c20a3-b3de-4595-bbd0-053f72903a2a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other Operating System :
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=616c20a3-b3de-4595-bbd0-053f72903a2a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=12df5db7-a545-4993-a0d6-7c970d4ae6ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 147.4GB: boot/grub/menu.lst
 147.4GB: boot/grub/stage2
 147.4GB: boot/initrd.img-2.6.27-11-generic
 147.4GB: boot/initrd.img-2.6.27-7-generic
 147.3GB: boot/initrd.img-2.6.27-9-generic
 147.4GB: boot/vmlinuz-2.6.27-11-generic
 147.4GB: boot/vmlinuz-2.6.27-7-generic
 147.4GB: boot/vmlinuz-2.6.27-9-generic
 147.4GB: initrd.img
 147.3GB: initrd.img.old
 147.4GB: vmlinuz
 147.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  e9 5e 3a cd 06 00 00 00  |FILE0....^:.....|
00000010  01 00 01 00 38 00 01 00  b8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  07 00 00 00 00 00 00 00  |................|
00000030  bf 04 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  35 5a 15 43 ef 38 c7 01  35 5a 15 43 ef 38 c7 01  |5Z.C.8..5Z.C.8..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  35 5a 15 43 ef 38 c7 01  |........5Z.C.8..|
000000c0  35 5a 15 43 ef 38 c7 01  35 5a 15 43 ef 38 c7 01  |5Z.C.8..5Z.C.8..|
000000d0  35 5a 15 43 ef 38 c7 01  00 00 12 0a 00 00 00 00  |5Z.C.8..........|
000000e0  00 00 12 0a 00 00 00 00  06 00 00 00 00 00 00 00  |................|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  1f a1 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 12 0a 00 00 00 00  |@...............|
00000130  00 00 12 0a 00 00 00 00  00 00 12 0a 00 00 00 00  |................|
00000140  32 c0 4a 00 00 0c 32 60  56 86 96 3b 00 d0 0d 88  |2.J...2`V..;....|
00000150  b0 00 00 00 60 00 00 00  01 00 40 00 00 00 06 00  |....`.....@.....|
00000160  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 60 00 00 00 00 00 00  |@........`......|
00000180  90 50 00 00 00 00 00 00  90 50 00 00 00 00 00 00  |.P.......P......|
00000190  31 01 ff ff 0b 31 01 86  96 3b 31 01 14 09 d4 31  |1....1...;1....1|
000001a0  01 8f 06 17 11 01 d1 41  01 44 4f 1b 01 00 00 00  |.......A.DO.....|
000001b0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001f0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 bf 04  |................|
00000200

```

---

### Post by caljohnsmith on 2009-02-19
OK, it looks like at least part of the issue is the starting sector position of your Vista partition that is embedded in the boot sector is incorrect; that sometimes occurs after resizing an NTFS partition. But the good news is that "testdisk" can usually fix problems like that. To use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda2 Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows Vista from the Grub menu. We can work from there if necessary.

---

### Post by bigsicky03 on 2009-02-19
I would like to thank you very much! Restarted and can boot in both Vista and Ubuntu, no doubt I will be using Ubuntu more..Thanks again!!

---

### Post by caljohnsmith on 2009-02-19
> **bigsicky03 said:**
> I would like to thank you very much! Restarted and can boot in both Vista and Ubuntu, no doubt I will be using Ubuntu more..Thanks again!!
You're welcome, I'm glad you can boot Vista now; cheers and enjoy your dual-boot setup. :)

---

