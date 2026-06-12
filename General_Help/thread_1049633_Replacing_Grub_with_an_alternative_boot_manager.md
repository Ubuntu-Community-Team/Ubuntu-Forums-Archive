---
title: "Replacing Grub with an alternative boot manager"
date: 2009-01-24
forum: General Help
---

### Post by StevePerkins on 2009-01-24
I have a desktop PC, with a single hard drive, dual-booting with the following scheme:

Partition #1 (Primary) - Windows Vista
Partition #2 (Extended)
   Partition #2a (Logical) - Ubuntu Hardy
   Partition #2b (Logical) - swap

Vista was hogging most of the hard drive, but Ubuntu is my primary OS, so I just resized the partitions to shift a ton of space from #1 to #2a.  This completely confused GRUB and stopped the machine from booting (I had a feeling that might happen based on reading I had done beforehand).  

However, I'm not really here to "fix" GRUB.  On my previous machine I had used another boot manager called GAG ([http://gag.sourceforge.net](http://gag.sourceforge.net)), which was self-contained in the MBR and very easy to use.  I would prefer going back to that, so I went ahead and installed it to the MBR of this machine.  

Vista on the first partition boots fine, but I cannot boot into Ubuntu.  I believe this is because some kind of boot loader (GRUB, LILO, whatever) needs to be installed on the superblock of that logical partition.  I can boot into Linux using an Ubuntu live CD with no problems, but my GRUB "menu.lst" is kind of a wreck at this point from all the previous experimenting.  Can anyone tell me what is the easiest way to get a boot loader on the superblock of my logical Linux partition, so the boot loader already on the MBR can boot that partition?  Thanks!

Steve

P.S.  I am also somewhat curious as to why GRUB uses the model that it does (i.e. installing files into a "/boot" directory on some partition, rather than being self-contained in the MBR).  I remember that LILO (the old standard prior to GRUB) was self-contained in the MBR, and it was a snap to use and trivial to fix when you changed around partitions.  I'm interested in the background on how GRUB took over as the default standard, when it seems like the self-contained-in-MBR model is more appropriate for most normal desktop users?  However, I'd much prefer to get my partition booting first and THEN dive into the potential flamewar second!  :)

---

### Post by caljohnsmith on 2009-01-24
I think it would help to get a clearer picture of your setup related to booting, so how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and most likely what it will take to boot Ubuntu with GAG.

---

### Post by StevePerkins on 2009-01-25
Results file is below.  Just wanting to put a boot loader (LILO, GRUB, whatever) on the superblock of the Linux partition (apparently /dev/sda5)... so that GAG in the MBR can point there and boot it up.  Thanks!

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce5973cb

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   71,682,029   71,681,967   7 HPFS/NTFS
/dev/sda2         71,682,030  156,296,384   84,614,355   5 Extended
/dev/sda5         71,682,093  155,477,069   83,794,977  83 Linux
/dev/sda6        155,477,133  156,296,384      819,252  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0D1C237639BE7844" TYPE="ntfs" 
/dev/sda5: UUID="867f93d5-ed14-450a-aefe-a9ff9caf7756" TYPE="ext3" 
/dev/sda6: UUID="98f58761-8ec3-434f-b4c7-b4e770849db1" TYPE="swap" 
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
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
timeout		-1

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
# kopt=root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet
#
#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro single
#initrd		/boot/initrd.img-2.6.24-22-generic
#
#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet
#
#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro single
#initrd		/boot/initrd.img-2.6.24-21-generic
#
#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet
#
#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro single
#initrd		/boot/initrd.img-2.6.24-19-generic
#
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet
#
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
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
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=867f93d5-ed14-450a-aefe-a9ff9caf7756 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=98f58761-8ec3-434f-b4c7-b4e770849db1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


  39.9GB: boot/grub/menu.lst
  39.9GB: boot/grub/stage2
  39.2GB: boot/initrd.img-2.6.24-16-generic
  39.3GB: boot/initrd.img-2.6.24-16-generic.bak
  39.3GB: boot/initrd.img-2.6.24-19-generic
  39.3GB: boot/initrd.img-2.6.24-19-generic.bak
  39.5GB: boot/initrd.img-2.6.24-21-generic
  39.5GB: boot/initrd.img-2.6.24-21-generic.bak
  39.4GB: boot/initrd.img-2.6.24-22-generic
  39.3GB: boot/initrd.img-2.6.24-22-generic.bak
  39.7GB: boot/initrd.img-2.6.24-23-generic
  39.7GB: boot/initrd.img-2.6.24-23-generic.bak
  39.3GB: boot/vmlinuz-2.6.24-16-generic
  39.3GB: boot/vmlinuz-2.6.24-19-generic
  39.2GB: boot/vmlinuz-2.6.24-21-generic
  39.3GB: boot/vmlinuz-2.6.24-22-generic
  39.2GB: boot/vmlinuz-2.6.24-23-generic
  39.7GB: initrd.img
  39.4GB: initrd.img.old
  39.2GB: vmlinuz
  39.3GB: vmlinuz.old

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sda

00000000  fc 33 c0 8e d8 8e c0 be  00 7c bf 00 06 b9 00 01  |.3.......|......|
00000010  f3 a5 ea 2e 06 00 00 47  41 47 3a 20 90 00 10 00  |.......GAG: ....|
00000020  01 00 00 7c 00 00 00 00  00 00 00 00 00 00 bf 17  |...|............|
00000030  06 b4 0e bb 07 00 8a 05  3c 90 74 07 57 cd 10 5f  |........<.t.W.._|
00000040  47 eb ee bf 1d 06 80 3d  00 75 65 b4 02 cd 16 a9  |G......=.ue.....|
00000050  0f 00 74 5c 33 c0 8e d8  8e c0 be be 7d b9 04 00  |..t\3.......}...|
00000060  80 3c 80 74 0a 83 c6 10  e2 f6 b0 32 e9 cd 00 b2  |.<.t.......2....|
00000070  80 b4 41 bb aa 55 cd 13  72 67 81 fb 55 aa 75 61  |..A..U..rg..U.ua|
00000080  bf 26 06 8b 4c 08 89 0d  8b 4c 0a 89 4d 02 b4 42  |.&..L....L..M..B|
00000090  be 1e 06 bb 03 00 50 56  53 b2 80 cd 13 73 3c 33  |......PVS....s<3|
000000a0  c0 b2 80 cd 13 5b 5e 58  4b 75 eb b0 31 e9 8c 00  |.....[^XKu..1...|
000000b0  bb 7f 01 b8 00 10 8e d8  8e c0 b9 03 00 51 ba 80  |.............Q..|
000000c0  00 b9 02 00 b4 02 b0 3d  90 cd 13 73 52 33 c0 b2  |.......=...sR3..|
000000d0  80 cd 13 59 e2 e7 b0 31  eb 62 90 5b 5e 58 eb 2d  |...Y...1.b.[^X.-|
000000e0  90 b2 80 8a 74 01 8b 4c  02 bb 03 00 53 51 52 bb  |....t..L....SQR.|
000000f0  00 7c b8 01 02 cd 13 73  11 33 c0 b2 80 cd 13 5a  |.|.....s.3.....Z|
00000100  59 5b 4b 75 e7 b0 31 eb  33 90 5a 59 5b 81 3e fe  |Y[Ku..1.3.ZY[.>.|
00000110  7d 55 aa 74 05 b0 34 eb  23 90 ea 00 7c 00 00 b8  |}U.t..4.#...|...|
00000120  00 10 8e c0 26 81 3e fc  02 47 41 75 0d 26 83 3e  |....&.>..GAu.&.>|
00000130  fe 02 47 75 05 ea 00 03  00 10 b0 33 bb 07 00 b4  |..Gu.......3....|
00000140  0e cd 10 eb fe 56 e8 2d  07 c6 06 ea 5f 00 c6 06  |.....V.-...._...|
00000150  eb 5f 00 c6 06 db 5f 5f  52 be 23 35 bb 48 00 b8  |._....__R.#5.H..|
00000160  38 00 e8 5c f4 5a 5e b6  0a bb 10 12 e8 42 02 bf  |8..\.Z^......B..|
00000170  db 5f b7 00 e8 4c 00 53  e8 a0 04 5b 3c 0d 75 09  |._...L.S...[<.u.|
00000180  c6 05 20 c6 06 ea 5f 00  c3 3c 08 75 11 80 ff 00  |.. ..._..<.u....|
00000190  74 e5 c6 05 20 4f fe cf  c6 05 5f eb 21 90 3c 20  |t... O...._.!.< |
000001a0  72 d5 80 3e 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |r..>....<.u.....|
000001b0  00 00 00 00 00 00 00 00  cb 73 59 ce 00 00 80 01  |.........sY.....|
000001c0  01 00 07 fe ff fe 3f 00  00 00 af c7 45 04 00 fe  |......?.....E...|
000001d0  ff fe 05 fe ff fe ee c7  45 04 d3 1c 0b 05 00 00  |........E.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-25
Well, I'm not going to argue with you if you want to use GAG, so here's how you can install Grub to the boot sector of your sda5 Ubuntu partition so you should be able to boot the partition with GAG:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0,4)
grub> quit
```
Then try booting sda5 from your GAG menu, and let me know how it goes.

---

