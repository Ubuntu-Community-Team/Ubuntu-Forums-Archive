---
title: "Linux not starting (starting in grub command line)"
date: 2009-04-16
forum: General Help
---

### Post by megaerathia on 2009-04-16
I've just installed Ubuntu, the newest version. What happens is it boots up with the grub line. And I don't know what the hell I have to do to start it in vista or ubuntu again. It gives rapid beeps when trying to start linux from harddrive using the live cd. What's wrong and what do I have to do to fix it?

Yours sincerely, 

Megaerathia.

---

### Post by meierfra. on 2009-04-16
In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by megaerathia on 2009-04-17
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1037173880 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 1219201373 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98985422

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2          20,467,712   635,633,663   615,165,952   6 FAT16
/dev/sda3         635,633,664 1,017,500,803   381,867,140   7 HPFS/NTFS
/dev/sda4       1,017,508,966 1,250,263,508   232,754,543   f W95 Ext d (LBA)
/dev/sda5       1,229,783,040 1,250,263,508    20,480,469   7 HPFS/NTFS
/dev/sda6       1,017,508,968 1,221,068,519   203,559,552  83 Linux
/dev/sda7       1,221,068,583 1,229,775,749     8,707,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="CEF8160CF815F385" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="08BC1B54BC1B3B9E" LABEL="XP" TYPE="ntfs" 
/dev/sda6: UUID="c801541c-8f87-46cc-ae05-e4d14ba88431" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="f76e9ccb-6d5e-4b0b-9abd-6bf7a4dcef9e" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=vinterthrone)
/dev/sda3 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c801541c-8f87-46cc-ae05-e4d14ba88431

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
uuid		c801541c-8f87-46cc-ae05-e4d14ba88431
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c801541c-8f87-46cc-ae05-e4d14ba88431
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c801541c-8f87-46cc-ae05-e4d14ba88431
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c801541c-8f87-46cc-ae05-e4d14ba88431
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c801541c-8f87-46cc-ae05-e4d14ba88431
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c801541c-8f87-46cc-ae05-e4d14ba88431 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f76e9ccb-6d5e-4b0b-9abd-6bf7a4dcef9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 531.1GB: boot/grub/menu.lst
 531.0GB: boot/grub/stage2
 531.1GB: boot/initrd.img-2.6.27-11-generic
 531.0GB: boot/initrd.img-2.6.27-7-generic
 531.1GB: boot/vmlinuz-2.6.27-11-generic
 531.1GB: boot/vmlinuz-2.6.27-7-generic
 531.1GB: initrd.img
 531.0GB: initrd.img.old
 531.1GB: vmlinuz
 531.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  31 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |1.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bf 05 00 31 c0  |...PW.........1.|
00000020  b2 80 cd 13 73 07 4f 74  02 eb f3 eb fe bd 88 07  |....s.Ot........|
00000030  80 7e 00 5a 74 54 f8 b8  10 96 b3 15 cd 15 72 16  |.~.ZtT........r.|
00000040  81 f9 00 00 74 2b f8 b8  10 96 b3 16 cd 15 72 06  |....t+........r.|
00000050  81 f9 01 00 74 1b f8 b8  10 96 b3 18 cd 15 72 06  |....t.........r.|
00000060  81 f9 01 00 75 24 f8 b8  81 ca cd 15 80 fa 01 74  |....u$.........t|
00000070  19 be be 07 b1 04 38 2c  7c 08 75 0b 81 c6 10 00  |......8,|.u.....|
00000080  e2 f4 89 f5 e9 6f 00 e9  69 00 bd be 07 66 8b 5e  |.....o..i....f.^|
00000090  08 60 68 00 00 68 00 00  66 53 68 00 00 68 00 7c  |.`h..h..fSh..h.||
000000a0  68 01 00 68 10 00 b4 42  b2 80 89 e6 cd 13 61 61  |h..h...B......aa|
000000b0  73 0b 4f 74 08 30 e4 b2  80 cd 13 eb cd e8 7b 00  |s.Ot.0........{.|
000000c0  bd be 7f c6 46 00 80 c6  46 10 00 c6 46 20 00 c6  |....F...F...F ..|
000000d0  46 04 0b a0 89 7f a8 04  74 04 80 4e 24 10 a0 89  |F.......t..N$...|
000000e0  7f a8 08 74 04 80 4e 34  10 e8 72 00 68 00 00 68  |...t..N4..r.h..h|
000000f0  00 7c cb bd ce 07 66 8b  5e 08 60 68 00 00 68 00  |.|....f.^.`h..h.|
00000100  00 66 53 68 00 00 68 00  7c 68 01 00 68 10 00 b4  |.fSh..h.|h..h...|
00000110  42 b2 80 89 e6 cd 13 61  61 73 0b 4f 74 08 30 e4  |B......aas.Ot.0.|
00000120  b2 80 cd 13 eb cd e8 12  00 bd be 7f 80 7e 04 27  |.............~.'|
00000130  74 ba c6 46 04 27 e8 25  00 eb b1 bf 05 00 31 c0  |t..F.'.%......1.|
00000140  8e c0 bb 00 7e b8 01 02  b5 00 b1 01 b6 00 b2 80  |....~...........|
00000150  cd 13 73 09 4f 74 06 30  e4 cd 0d eb de c3 bf 05  |..s.Ot.0........|
00000160  00 31 c0 8e c0 bb 00 7e  b8 01 03 b5 00 b1 01 b6  |.1.....~........|
00000170  00 b2 80 cd 13 73 09 4f  74 06 30 e4 cd 0d eb de  |.....s.Ot.0.....|
00000180  c3 00 00 41 63 65 72 2e  33 00 00 73 79 73 74 65  |...Acer.3..syste|
00000190  6d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |m...............|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  22 54 98 98 00 00 80 01  |........"T......|
000001c0  01 00 27 fe ff ff 3f 00  00 00 3b 4c 38 01 00 fe  |..'...?...;L8...|
000001d0  ff ff 06 fe ff ff 00 50  38 01 00 b0 aa 24 00 fe  |.......P8....$..|
000001e0  ff ff 07 fe ff ff 00 00  e3 25 84 d4 c2 16 00 fe  |.........%......|
000001f0  ff ff 0f fe ff ff 66 f4  a5 3c 6f 8d df 0d 55 aa  |......f..<o...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by codeseer on 2009-04-17
It seems like there's some conflicts and maybe more than one grub.

I'd give this a go with the 'quick solution':
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub")

If the quick solution doesn't fix it up, you can do the manual fix by selecting the drives for it.

---

### Post by meierfra. on 2009-04-17
There are various problems with your current setup and Super Grub will not be able to solve all your problems. In particular, you will need to do some extra work to be able to boot into Vita. But give Super Grub a try, and if it does not succeed to boot Ubuntu, report any error messages you got. We will work from there.

---

