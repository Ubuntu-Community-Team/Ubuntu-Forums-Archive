---
title: "gave up waiting for root device (Error on bootup)"
date: 2011-11-26
forum: Desktop Environments
---

### Post by kaution on 2011-11-26
Hi, I've been browsing the Ubuntu for years now and even tutorials! Great community! I say that because I always do my research before asking questions.

Specs:

Ubuntu 10.04 LTR

System: Custom built 3 years ago with 4 gig of corsair ram and an amd single core processor

Whrere I have Ubuntu installed is a seagate freeagent golex 500 gig I purchased last year (And yes, I did format before installing Ubuntu). I did have a hard time geeting it going and browsing through these forums I found that my bios wasn't reading the grub menu because it was at the end of the hard drive and the hard drive was so big. I re installed Ubuntu on a smaller partition. Everything worked great for a couple days!

I hope this screen shot woks, it's how my partitions look to Gparted.

[IMG]http://homeeconomic.org/Screenshot.png[/IMG]

The problem is I get boot up errors, I can fix them with the live CD but it's becoming a pain and I should have to do that.
I learned how to fix it from this tuterial [http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/]("http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/")

 I did notice Gparted is showing to partitions at at around 440 gigs, one being extension4 and the other ntfs. I do have the drive mounted with a short cut on my desk top to access all my personal folders. It looks as if it's mounted as the ntfs and not the ext4 if that helps.

So what is the root cause of this problem so I can fix it so I don't have to keep repairing it?

---

### Post by Rubi1200 on 2011-11-26
Hi and welcome to the forums :-)

Please post the results of the boot info script as that may help us diagnose the cause of the problem.

Link at the bottom of my post with instructions.

Thanks.

---

### Post by kaution on 2011-11-26
Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,062,562    39,062,500  83 Linux
/dev/sda2          39,063,550   976,771,071   937,707,522   5 Extended
/dev/sda5          39,063,552    46,874,623     7,811,072  82 Linux swap / Solaris
/dev/sda6          46,876,672   976,771,071   929,894,400   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    15,631,244    15,631,182   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/truecrypt1 F979-9938                              vfat       
/dev/mapper/truecrypt2 9B9A-7D93                              vfat       
/dev/sda1        0b7b4983-3770-46f0-8757-13b8c84f2ad1   ext4       
/dev/sda5        43328eb5-8a20-4849-bdf2-aa0c4a9f37b4   swap       
/dev/sda6        58CC7D2C2C3F267E                       ntfs       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
truecrypt1
truecrypt2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/truecrypt1 /media/truecrypt1        vfat       (rw,uid=1000,gid=1000,umask=077)
/dev/mapper/truecrypt2 /media/truecrypt2        vfat       (rw,uid=1000,gid=1000,umask=077)
/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/58CC7D2C2C3F267E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
	linux	/boot/vmlinuz-2.6.32-35-generic-pae root=UUID=0b7b4983-3770-46f0-8757-13b8c84f2ad1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-35-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
	echo	'Loading Linux 2.6.32-35-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-35-generic-pae root=UUID=0b7b4983-3770-46f0-8757-13b8c84f2ad1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-35-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b7b4983-3770-46f0-8757-13b8c84f2ad1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=43328eb5-8a20-4849-bdf2-aa0c4a9f37b4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.739711285 = 2.941742592    boot/grub/core.img                             1
  16.300158978 = 17.502162432   boot/grub/grub.cfg                             1
   2.702346325 = 2.901622272    boot/initrd.img-2.6.32-35-generic-pae          1
   2.726428509 = 2.927480320    boot/vmlinuz-2.6.32-35-generic-pae             1
   2.702346325 = 2.901622272    initrd.img                                     1
   2.726428509 = 2.927480320    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  5e 2b 6a d6 c0 8e 5e df  b1 00 fc c7 e3 cb 2a c9  |^+j...^.......*.|
00000010  03 1f cc f0 f1 b8 27 66  7f d5 30 78 7e 19 d1 50  |......'f..0x~..P|
00000020  36 ae 9e bc 93 d4 2d 2f  b0 0a 16 5f 85 c3 3c 92  |6.....-/..._..<.|
00000030  9a f9 43 8a 14 99 e1 8a  62 a4 71 b8 44 07 71 e3  |..C.....b.q.D.q.|
00000040  02 46 f1 02 49 ef 69 c1  7d bd 9e ec f4 99 c3 04  |.F..I.i.}.......|
00000050  56 9a 92 57 08 a0 d6 49  3d 62 b2 a6 39 35 4b 03  |V..W...I=b..95K.|
00000060  04 7c be 4b 64 f3 cf 3a  e1 e1 a8 1c 8a 68 5f 34  |.|.Kd..:.....h_4|
00000070  ec 27 62 f8 b6 b0 19 ec  8d 11 ba a2 5d 3b ef 29  |.'b.........];.)|
00000080  59 dd 0c 57 13 25 fd c3  17 d6 63 af 65 d8 c9 7e  |Y..W.%....c.e..~|
00000090  14 25 13 6e b8 62 6b 12  32 13 14 cc ae d2 a2 66  |.%.n.bk.2......f|
000000a0  9c c0 96 db aa 2e 4d 21  58 a7 6f e7 10 d2 74 e4  |......M!X.o...t.|
000000b0  27 32 dc 52 d1 b0 cc cf  09 b1 17 42 c3 d3 f2 78  |'2.R.......B...x|
000000c0  35 09 93 8d b0 90 8b 50  8c d8 b4 41 3e b7 01 4b  |5......P...A>..K|
000000d0  0c b4 eb 20 e5 dc 29 30  50 12 17 e5 dc 2d 17 64  |... ..)0P....-.d|
000000e0  a8 7e d2 b2 b4 2d a5 1b  8f d0 81 68 7b 47 ae d4  |.~...-.....h{G..|
000000f0  77 ca 2b 50 ef da be dd  aa ab b8 5c 22 08 c9 14  |w.+P.......\"...|
00000100  f4 da 2d fe 54 33 1a 40  f9 be 3b 2b b7 f0 de b7  |..-.T3.@..;+....|
00000110  5b de c3 1c 4b 77 d0 63  09 d7 cb 76 0d 19 94 f7  |[...Kw.c...v....|
00000120  a7 8d 66 a2 24 ee 83 ca  71 6a c0 34 4d 69 c0 eb  |..f.$...qj.4Mi..|
00000130  4a 05 cd 02 7c d2 c5 32  09 7e 79 10 60 eb 3d 00  |J...|..2.~y.`.=.|
00000140  58 04 c9 19 ac 06 4d 07  66 53 31 d3 95 2c 95 a5  |X.....M.fS1..,..|
00000150  4c e8 77 9d 5b 77 bf 52  ba 87 98 0d 90 22 68 a2  |L.w.[w.R....."h.|
00000160  b1 8d 2c 36 40 21 d5 70  f1 a7 a4 57 a8 b6 e9 25  |..,6@!.p...W...%|
00000170  5e f4 3f ea de 7e bd e6  b5 f4 8c d8 f6 ca a3 ce  |^.?..~..........|
00000180  c3 d7 e8 b2 e2 63 f0 83  9f ef 45 d2 be 4b 61 28  |.....c....E..Ka(|
00000190  b0 76 90 c2 23 18 98 4f  55 1a fe 68 67 78 77 fc  |.v..#..OU..hgxw.|
000001a0  5e 12 6d 7d 9b a1 37 87  db 43 6f a5 36 ea 74 07  |^.m}..7..Co.6.t.|
000001b0  d0 a3 f2 24 6c f7 83 6c  8e 51 c9 23 58 1a 4f fb  |...$l..l.Q.#X.O.|
000001c0  ed 17 93 08 6c e1 8e 30  26 0a d0 19 c7 b9 e0 95  |....l..0&.......|
000001d0  cc 45 b2 e5 76 95 ed 8a  4b 88 72 00 93 ce 50 73  |.E..v...K.r...Ps|
000001e0  09 88 ad ae 0a 94 b7 ec  ea 1a e5 be 09 9f 34 21  |..............4!|
000001f0  f7 9e c0 e5 42 27 fb 46  12 69 66 06 f9 10 75 3d  |....B'.F.if...u=|
00000200
```

---

### Post by kaution on 2011-11-27
Any ideas? I really don't want to have to go to windows after using ubuntu all these years or have to buy a mac.

---

### Post by Rubi1200 on 2011-11-28
Hi and thanks for posting the results. After consulting with drs305, an experiened member and fellow moderator, I want to share the following with you.

If you are trying to mount sda6 from the desktop it could cause problems especially if trying to do so as an ext4 partition. Perhaps you think it is but the results and GParted show sda6 as being an NTFS partition.

We recommend the following steps to try and resolve this:

1. disable any method being used to automount sda6 until you can figure out what is happening.

2a. Perhaps putting an sda6 entry in fstab with an option of "noauto"  would at least prevent the error during boot. Of course, what format to  put sda6 in fstab is open to question. You can try ntfs first,  since that is what the system thinks it is.

2b. Since there currently isn't an entry in fstab, perhaps disabling the  universal automount feature (if enabled) may also help. Here's a link:
[http://www.liberiangeek.net/2010/09/...erick-meerkat/]("http://www.liberiangeek.net/2010/09/disableenable-auto-mount-ubuntu-10-0410-10-maverick-meerkat/")

2c. If you have written a script to automount the partition, disable it.

Let us know what happens please.

---

