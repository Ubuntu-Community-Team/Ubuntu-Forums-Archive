---
title: "Grub problem"
date: 2009-02-06
forum: General Help
---

### Post by geum on 2009-02-06
Cannot access Opensolaris 2008.11 from the boot menu option,selecting Ubuntu 8.10 is ok.
Ubuntu is on sda
Opensolaris is on sdb.

Results from boot_info_script,txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.95 is installed in the boot sector of sdb1 and 
                       looks at sector 16115 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb32eb32e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,468,944   153,468,882  83 Linux
/dev/sda2         153,468,945   160,071,659     6,602,715   5 Extended
/dev/sda5         153,469,008   160,071,659     6,602,652  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   160,071,659   160,055,595  bf Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0eceb855-eeed-4267-a190-c3184c7d923d" TYPE="ext3" 
/dev/sda5: UUID="22b8a747-82fa-48b0-a004-77a06783bd35" TYPE="swap" 
/dev/sdb5: TYPE="zfs" 

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
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/derek/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=derek)

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
#hiddenmenu
# Hides the menu by default (press ESC to see the menu)

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
# kopt=root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro

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

title		Ubuntu 8.10, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Opensolaris
root            (hd1,0)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0eceb855-eeed-4267-a190-c3184c7d923d /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=22b8a747-82fa-48b0-a004-77a06783bd35 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda1: Location of files loaded by Grub: ===================


  64.1GB: boot/grub/menu.lst
  64.0GB: boot/grub/stage2
  64.0GB: boot/initrd.img-2.6.20-16-generic
  64.0GB: boot/initrd.img-2.6.22-14-generic
  64.0GB: boot/initrd.img-2.6.22-14-generic.bak
  64.1GB: boot/initrd.img-2.6.24-18-generic
  64.0GB: boot/initrd.img-2.6.24-18-generic.bak
  64.0GB: boot/initrd.img-2.6.27-11-generic
  64.1GB: boot/initrd.img-2.6.27-7-generic
  64.1GB: boot/initrd.img-2.6.27-9-generic
  64.0GB: boot/vmlinuz-2.6.20-16-generic
  64.1GB: boot/vmlinuz-2.6.22-14-generic
  64.0GB: boot/vmlinuz-2.6.24-18-generic
  64.1GB: boot/vmlinuz-2.6.27-11-generic
  64.1GB: boot/vmlinuz-2.6.27-7-generic
  64.0GB: boot/vmlinuz-2.6.27-9-generic
  64.0GB: initrd.img
  64.1GB: initrd.img.old
  64.1GB: vmlinuz
  64.0GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 04 4d 33 2e 30 fa fc  be 00 7c bf 00 06 8c c8  |..M3.0....|.....|
00000010  8e d0 89 f4 8e c0 8e d8  51 b9 00 01 f3 a5 59 e9  |........Q.....Y.|
00000020  00 8a fb b4 02 cd 16 24  03 3c 03 75 05 c6 06 61  |.......$.<.u...a|
00000030  07 01 bb be 07 b9 04 00  80 3f 80 74 0e 83 c3 10  |.........?.t....|
00000040  e2 f6 bd 75 07 b9 13 00  e9 e6 00 b4 00 cd 13 53  |...u...........S|
00000050  b4 41 bb aa 55 b9 00 00  cd 13 72 3f 81 fb 55 aa  |.A..U.....r?..U.|
00000060  75 39 f7 c1 01 00 74 33  bd a4 07 b9 03 00 e8 c8  |u9....t3........|
00000070  00 5b 53 b9 05 00 66 6a  00 66 ff 77 08 66 ff 36  |.[S...fj.f.w.f.6|
00000080  5c 07 6a 01 6a 10 b4 42  89 e6 cd 13 9f 83 c4 10  |\.j.j..B........|
00000090  9e 73 7b b4 00 cd 13 e2  dd eb 6b bd a7 07 b9 03  |.s{.......k.....|
000000a0  00 e8 95 00 5b 53 8a 16  60 07 b4 08 cd 13 73 08  |....[S..`.....s.|
000000b0  bd 62 07 b9 13 00 eb 79  88 c8 24 3f a2 59 07 fe  |.b.....y..$?.Y..|
000000c0  c6 f6 e6 a3 5a 07 8b 47  08 8b 57 0a f7 36 5a 07  |....Z..G..W..6Z.|
000000d0  89 c3 89 d0 f6 36 59 07  fe c4 30 c9 88 fd c1 e9  |.....6Y...0.....|
000000e0  02 80 e1 c0 08 e1 88 dd  88 c6 8a 16 60 07 c4 1e  |............`...|
000000f0  5c 07 be 05 00 b8 01 02  cd 13 73 12 b4 00 cd 13  |\.........s.....|
00000100  4e 83 fe 00 75 ef bd 88  07 b9 0e 00 eb 23 bb 00  |N...u........#..|
00000110  7c 81 bf fe 01 55 aa 74  08 bd 96 07 b9 0b 00 eb  ||....U.t........|
00000120  10 8a 16 60 07 5e 66 ff  16 5c 07 bd a1 07 b9 03  |...`.^f..\......|
00000130  00 bb 4f 00 e8 0c 00 cd  18 80 3e 61 07 00 74 18  |..O.......>a..t.|
00000140  bb 1f 00 60 b8 01 13 ba  00 17 cd 10 b0 07 b9 01  |...`............|
00000150  00 cd 10 b4 00 cd 16 61  c3 00 00 00 00 7c 00 00  |.......a.....|..|
00000160  80 00 43 61 6e 27 74 20  72 65 61 64 20 67 65 6f  |..Can't read geo|
00000170  6d 65 74 72 79 4e 6f 20  61 63 74 69 76 65 20 70  |metryNo active p|
00000180  61 72 74 69 74 69 6f 6e  43 61 6e 27 74 20 72 65  |artitionCan't re|
00000190  61 64 20 50 42 52 42 61  64 20 50 42 52 20 73 69  |ad PBRBad PBR si|
000001a0  67 21 21 21 4c 42 41 43  48 53 00 00 00 00 00 00  |g!!!LBACHS......|
000001b0  00 00 00 00 00 00 00 00  90 90 90 90 90 80 80 00  |................|
000001c0  01 01 bf fe ff ff c1 3e  00 00 2b 41 8a 09 00 00  |.......>..+A....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.txt: line 1043: [: =: unary operator expected
```

Sorry to ask another grub question,but I could'nt find anything relevant on booting Ubuntu with Opensolaris.

---

### Post by 73ckn797 on 2009-02-06
Try changing the Solaris drive to (hd1,4) in the grub menu.

---

### Post by geum on 2009-02-06
73ckn797
Thanks for that,tried it and got,error message 22 :no such partition.

---

### Post by caljohnsmith on 2009-02-06
[QUOTE=geum]Cannot access Opensolaris 2008.11 from the boot menu option[/QUOTE]
Could you be more specific? When you use the original OpenSolaris Grub entry you show in post #1, what exactly happens? In the meantime, how about trying:
```
title OpenSolaris
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
And let me know what happens.

---

### Post by geum on 2009-02-06
caljohnsmith
```

title OpenSolaris
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Tried method above,selecting OpenSolaris from boot menu screen,gives me a black screen with:  starting up
                      grub loading stage 2
in the top left of the screen nothing else at all,exact same message before I posted.

---

### Post by caljohnsmith on 2009-02-06
At this point it sounds like you have a problem with OpenSolaris and not Grub. If you boot your OpenSolaris CD, can you mount and access your OpenSolaris partition OK? I'm not sure what tools the OpenSolaris CD has, but if you can, I would recommend running some sort of "fsck" on your OpenSolaris partition. Let me know what that turns up.

---

### Post by 73ckn797 on 2009-02-06
You might want to play around with the (hd1,4) numbers. Possibly change the last number to 3 or 2 and see what happens.

---

