---
title: "Grub Can't Detect Win7 Boot Partition"
date: 2010-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mamad_fexar on 2010-12-16
Hi guys, I installed 10.10 with Win7 on my Dell 5010 and everything was OK.
But after 2 week grub can't detect my Win7 Boot partition (100MB Boot partition).

When i try to mount manually in ubuntu show this error:

```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

This is my fdisk result:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb480a2e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2550    20377600    7  HPFS/NTFS
/dev/sda3            2550       37686   282225665    5  Extended
/dev/sda4           37686       38914     9863168   83  Linux
/dev/sda5            2550       20787   146483200    7  HPFS/NTFS
/dev/sda6           20787       37200   131834880    7  HPFS/NTFS
/dev/sda7           37200       37686     3905536   82  Linux swap / Solaris

```

---

### Post by oldfred on 2010-12-16
So we can see the details:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by mamad_fexar on 2010-12-16
Thanx for your help,

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 40964096.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    40,962,047    40,755,200   7 HPFS/NTFS
/dev/sda3          40,964,094   605,415,423   564,451,330   5 Extended
/dev/sda5          40,964,096   333,930,495   292,966,400   7 HPFS/NTFS
/dev/sda6         333,932,544   597,602,303   263,669,760   7 HPFS/NTFS
/dev/sda7         597,604,352   605,415,423     7,811,072  82 Linux swap / Solaris
/dev/sda4         605,415,424   625,141,759    19,726,336  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        0E7672D47672BBD1                       ntfs       Windows7                      
/dev/sda3: PTTYPE="dos" 
/dev/sda4        85ca961d-8d34-40ac-9d66-a87a62973f53   ext4                                     
/dev/sda5        30D08261D0822D62                       ntfs       Program Files                 
/dev/sda6        E01E8D3A1E8D0B2C                       ntfs       Documents                     
/dev/sda7        52b0a8d9-84c6-456e-b6c8-aa3d8c807967   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Documents         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=85ca961d-8d34-40ac-9d66-a87a62973f53 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=85ca961d-8d34-40ac-9d66-a87a62973f53 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=85ca961d-8d34-40ac-9d66-a87a62973f53 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=85ca961d-8d34-40ac-9d66-a87a62973f53 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 85ca961d-8d34-40ac-9d66-a87a62973f53
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=85ca961d-8d34-40ac-9d66-a87a62973f53 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=52b0a8d9-84c6-456e-b6c8-aa3d8c807967 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 316.8GB: boot/grub/core.img
 317.2GB: boot/grub/grub.cfg
 317.1GB: boot/initrd.img-2.6.20
 311.7GB: boot/initrd.img-2.6.35-22-generic
 317.1GB: boot/initrd.img-2.6.35-23
 314.9GB: boot/initrd.img-2.6.35-23-generic
 317.0GB: boot/vmlinuz-2.6.35-22-generic
 317.1GB: boot/vmlinuz-2.6.35-23-generic
 314.9GB: initrd.img
 311.7GB: initrd.img.old
 317.1GB: vmlinuz
 317.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  3c 64 65 76 69 63 65 20  44 45 56 4e 4f 3d 22 30  |<device DEVNO="0|
00000010  78 30 38 30 32 22 20 54  49 4d 45 3d 22 31 32 39  |x0802" TIME="129|
00000020  32 35 34 30 30 31 31 22  20 4c 41 42 45 4c 3d 22  |2540011" LABEL="|
00000030  57 69 6e 64 6f 77 73 37  22 20 55 55 49 44 3d 22  |Windows7" UUID="|
00000040  30 45 37 36 37 32 44 34  37 36 37 32 42 42 44 31  |0E7672D47672BBD1|
00000050  22 20 54 59 50 45 3d 22  6e 74 66 73 22 3e 2f 64  |" TYPE="ntfs">/d|
00000060  65 76 2f 73 64 61 32 3c  2f 64 65 76 69 63 65 3e  |ev/sda2</device>|
00000070  0a 3c 64 65 76 69 63 65  20 44 45 56 4e 4f 3d 22  |.<device DEVNO="|
00000080  30 78 30 38 30 34 22 20  54 49 4d 45 3d 22 31 32  |0x0804" TIME="12|
00000090  39 32 35 34 30 30 31 31  22 20 55 55 49 44 3d 22  |92540011" UUID="|
000000a0  38 35 63 61 39 36 31 64  2d 38 64 33 34 2d 34 30  |85ca961d-8d34-40|
000000b0  61 63 2d 39 64 36 36 2d  61 38 37 61 36 32 39 37  |ac-9d66-a87a6297|
000000c0  33 66 35 33 22 20 54 59  50 45 3d 22 65 78 74 34  |3f53" TYPE="ext4|
000000d0  22 3e 2f 64 65 76 2f 73  64 61 34 3c 2f 64 65 76  |">/dev/sda4</dev|
000000e0  69 63 65 3e 0a 3c 64 65  76 69 63 65 20 44 45 56  |ice>.<device DEV|
000000f0  4e 4f 3d 22 30 78 30 38  30 35 22 20 54 49 4d 45  |NO="0x0805" TIME|
00000100  3d 22 31 32 39 32 35 34  30 30 31 31 22 20 4c 41  |="1292540011" LA|
00000110  42 45 4c 3d 22 50 72 6f  67 72 61 6d 20 46 69 6c  |BEL="Program Fil|
00000120  65 73 22 20 55 55 49 44  3d 22 33 30 44 30 38 32  |es" UUID="30D082|
00000130  36 31 44 30 38 32 32 44  36 32 22 20 54 59 50 45  |61D0822D62" TYPE|
00000140  3d 22 6e 74 66 73 22 3e  2f 64 65 76 2f 73 64 61  |="ntfs">/dev/sda|
00000150  35 3c 2f 64 65 76 69 63  65 3e 0a 3c 64 65 76 69  |5</device>.<devi|
00000160  63 65 20 44 45 56 4e 4f  3d 22 30 78 30 38 30 36  |ce DEVNO="0x0806|
00000170  22 20 54 49 4d 45 3d 22  31 32 39 32 35 34 30 30  |" TIME="12925400|
00000180  31 31 22 20 4c 41 42 45  4c 3d 22 44 6f 63 75 6d  |11" LABEL="Docum|
00000190  65 6e 74 73 22 20 55 55  49 44 3d 22 45 30 31 45  |ents" UUID="E01E|
000001a0  38 44 33 41 31 45 38 44  30 42 32 43 22 20 54 59  |8D3A1E8D0B2C" TY|
000001b0  50 45 3d 22 6e 74 66 73  22 3e 2f 64 65 76 2f 73  |PE="ntfs">/dev/s|
000001c0  64 61 36 3c 2f 64 65 76  69 63 65 3e 0a 3c 64 65  |da6</device>.<de|
000001d0  76 69 63 65 20 44 45 56  4e 4f 3d 22 30 78 30 38  |vice DEVNO="0x08|
000001e0  30 37 22 20 54 49 4d 45  3d 22 31 32 39 32 35 34  |07" TIME="129254|
000001f0  30 30 31 31 22 20 55 55  49 44 3d 22 35 32 62 30  |0011" UUID="52b0|
00000200

Unknown BootLoader  on sda3

00000000  eb 88 f1 ba 15 ae 8a 48  8e 43 7f 71 ba f1 de ff  |.......H.C.q....|
00000010  93 ba ff 8a 66 ec 3d e1  7f ff b0 36 78 88 1d 12  |....f.=....6x...|
00000020  8a 47 f4 ba 07 a4 8b 12  78 95 1b ea b4 a9 5f 7b  |.G......x....._{|
00000030  f4 71 4c 54 14 24 09 54  bf a4 2e 63 83 b1 15 ef  |.qLT.$.T...c....|
00000040  8e 97 ba 1a ff d7 bd 31  ad f0 f3 a7 42 46 55 f8  |.......1....BFU.|
00000050  64 11 ae 20 65 ca c5 a1  42 bc 6b f0 a9 8a 76 4f  |d.. e...B.k...vO|
00000060  17 8c fc 39 ad e3 40 a6  1f ad ff 84 44 98 bb 23  |...9..@.....D..#|
00000070  b9 20 68 f6 22 a7 aa e3  02 cb 1c 17 ec f3 79 58  |. h.".........yX|
00000080  1f be 24 10 33 ee ca b7  3a 96 10 8c 8d aa a2 c5  |..$.3...:.......|
00000090  ff 24 59 81 70 59 55 1c  15 32 c5 7e 3f 58 96 4d  |.$Y.pYU..2.~?X.M|
000000a0  46 aa 5d 09 af aa 4f 8a  ec 3a 1f fe 8b 96 19 83  |F.]...O..:......|
000000b0  e5 8b 27 61 f2 af 4e e2  7a 29 53 31 2d 7f 26 45  |..'a..N.z)S1-.&E|
000000c0  a6 4e e5 84 ad c5 8d 30  31 29 91 8e 68 11 24 dc  |.N.....01)..h.$.|
000000d0  02 be f4 76 5c 51 c8 75  76 49 0c 44 c0 88 dc 37  |...v\Q.uvI.D...7|
000000e0  c2 e6 6e 53 05 65 e4 ba  78 59 c9 b1 15 97 3b a3  |..nS.e..xY....;.|
000000f0  22 52 0d 0e 31 86 f8 45  e8 ca 9e c4 71 0b 70 dc  |"R..1..E....q.p.|
00000100  bc 02 5e 45 8b da 3e f1  f6 fb 9c 3e 71 5d 84 16  |..^E..>....>q]..|
00000110  2a 1d 5c d8 5c df 18 a9  c7 52 8a dd c8 b3 0d 8b  |*.\.\....R......|
00000120  6b c5 60 0b 46 ac 23 76  fd 8a c5 c2 bd 77 62 a9  |k.`.F.#v.....wb.|
00000130  4b 9a f5 1e e8 ee e2 b3  72 af a2 48 4a 3c b1 bf  |K.......r..HJ<..|
00000140  a3 78 a7 8e 61 c0 3d bf  57 4e 1f c0 eb 54 c4 b4  |.x..a.=.WN...T..|
00000150  0e 9f 24 64 9f e3 5f 74  fb 8d b9 38 00 4b 93 5d  |..$d.._t...8.K.]|
00000160  51 49 f5 44 98 64 49 52  aa 68 1d fc 15 28 26 b1  |QI.D.dIR.h...(&.|
00000170  9a 0d b7 83 e3 c7 6b af  8c f2 49 d1 83 97 fe 25  |......k...I....%|
00000180  f7 9f f1 e9 73 ce eb ee  73 ee e4 82 79 ae 6c 59  |....s...s...y.lY|
00000190  73 6e d9 22 5c 19 67 f2  62 f2 2b e7 fa 2f c4 09  |sn."\.g.b.+../..|
000001a0  e4 e6 90 ff 1a 48 28 4c  06 0c 02 1f 11 53 48 81  |.....H(L.....SH.|
000001b0  52 c6 b5 fe 12 2f d8 ad  21 c9 0c a9 31 53 00 fe  |R..../..!...1S..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 50 76 11 00 fe  |...........Pv...|
000001d0  ff ff 05 fe ff ff 02 50  76 11 00 50 b7 0f 00 00  |.......Pv..P....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-12-16
I see some problems oldfred is on line I suspect, so lets see their response. In the mean time if you don't have a recovery or install disc download this one it will probably be used to fix the setup. Looks like vista to me.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by oldfred on 2010-12-16
Well fdisk is seeing sda1 as NTFS, but the partition boot sector does not have the NTFS signature.

This should recover it from the backup.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not then you will need the windows repair CD wilee-nilee has suggested to repair it. Chkdsk and/or fixboot type commands would be first on my list.

---

### Post by mamad_fexar on 2010-12-16
Very thanx for your speedy help, I try it.;)


Boot partition Recover with testdisk, it worked!:P

---

### Post by oldfred on 2010-12-16
Glad it worked. :)

As long as you keep windows installed I would also have the windows repair CD available. Just like having a Ubuntu's live CD (or USB flash drive) to make repairs.

---

