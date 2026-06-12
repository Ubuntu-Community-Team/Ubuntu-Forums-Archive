---
title: "Boot loader issues dual booting xp/maverick"
date: 2011-01-11
forum: Desktop Environments
---

### Post by lmc2179 on 2011-01-11
Hey,

I have a 250 GB hard drive split in half with two partitions. I installed XP on one, then Ubuntu 10.10 on the other half. I believe during the install XP and Ubuntu further split each of the two partitions.

However, when I boot it goes straight to XP. I've tried "sudo grub" to get to the bootloader options, but I get a "Command not found error". Any ideas?

meierfra's boot script results in this:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   142,303,226   142,096,379   7 HPFS/NTFS
/dev/sda3         283,596,800   488,394,751   204,797,952   6 FAT16
/dev/sda4         142,303,230   283,596,799   141,293,570   5 Extended
/dev/sda5         142,303,232   277,745,663   135,442,432  83 Linux
/dev/sda6         277,747,712   283,596,799     5,849,088  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   3733-6331                              vfat                                     
/dev/sda1        E0A8B497A8B46E22                       ntfs       System Reserved               
/dev/sda2        D6B006C9B006B053                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c51e1ad3-ced4-4819-82d6-ab5d8d07fc80   ext4                                     
/dev/sda6        5f9049b2-9bd1-4d7f-8c48-d3c089ba0632   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DEC2A84EC2A82CA9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c51e1ad3-ced4-4819-82d6-ab5d8d07fc80 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c51e1ad3-ced4-4819-82d6-ab5d8d07fc80 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set c51e1ad3-ced4-4819-82d6-ab5d8d07fc80
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e0a8b497a8b46e22
    chainloader +1
}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c51e1ad3-ced4-4819-82d6-ab5d8d07fc80 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5f9049b2-9bd1-4d7f-8c48-d3c089ba0632 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  94.4GB: boot/grub/core.img
  83.7GB: boot/grub/grub.cfg
  77.4GB: boot/initrd.img-2.6.35-22-generic
  94.4GB: boot/vmlinuz-2.6.35-22-generic
  77.4GB: initrd.img
  94.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  fe ef ff ff de af 77 57  8f bd 3a f7 bb bd ef ff  |......wW..:.....|
00000010  f7 bd d7 f5 9b 16 77 bf  ff f7 1f dd dd ff ff f7  |......w.........|
00000020  7f bb ff ff ff f7 30 31  77 62 80 01 00 00 ff fb  |......01wb......|
00000030  94 64 3b 8e 04 c8 4b 51  93 58 4a f2 2e 45 8b 0d  |.d;...KQ.XJ..E..|
00000040  3c 45 4c d3 05 39 48 4c  e5 6b c0 be 96 ed 74 92  |<EL..9HL.k....t.|
00000050  89 33 ca ae 59 ff ff e5  64 e7 b9 0f e1 56 be 25  |.3..Y...d....V.%|
00000060  0d a8 3e e4 e2 29 0f 5b  ff fb 61 80 c8 5c 34 d8  |..>..).[..a..\4.|
00000070  58 df aa a1 0d c8 40 00  00 00 a0 00 6e 25 ce 84  |X.....@.....n%..|
00000080  74 02 18 9f 61 42 d5 aa  21 e1 5d 00 da 77 9f 21  |t...aB..!.]..w.!|
00000090  ef fa 2b db ff ff ff ff  e2 21 43 8a 30 54 ca 2c  |..+......!C.0T.,|
000000a0  c1 28 81 f4 f6 10 36 15  e4 8a e7 fc 70 13 3c 18  |.(....6.....p.<.|
000000b0  53 73 0c 3d fe 4d a4 fa  aa 30 b9 a4 93 aa 14 94  |Ss.=.M...0......|
000000c0  eb a5 7b 88 89 44 c8 06  09 12 51 45 82 fa 1b 9a  |..{..D....QE....|
000000d0  24 08 00 91 10 4c 90 54  64 87 4e b5 1b 31 8b 53  |$....L.Td.N..1.S|
000000e0  60 36 c3 62 ca 97 6c 8e  86 92 1f d5 79 64 3b 7a  |`6.b..l.....yd;z|
000000f0  04 b6 74 91 14 7d ed 0f  03 a0 3c 8d e8 a0 1b 02  |..t..}....<.....|
00000100  21 d5 8f 9e 2a 45 55 15  71 d4 a3 87 39 66 c1 79  |!...*EU.q...9f.y|
00000110  99 38 e5 6a bf 8b 98 fa  bf eb a6 59 2e 4d f8 47  |.8.j.......Y.M.G|
00000120  fe 37 51 e3 05 a1 5b a7  72 e8 ea 38 88 b9 73 61  |.7Q...[.r..8..sa|
00000130  e9 7a 4b 0d f6 c8 c0 6c  9c 65 25 b8 9a 00 00 00  |.zK....l.e%.....|
00000140  b8 00 11 37 44 c2 20 c0  30 a2 6e 20 91 54 44 5e  |...7D. .0.n .TD^|
00000150  a0 8d 7a f1 77 ff a1 ff  ff ff c8 a5 3d 08 ce 20  |..z.w.......=.. |
00000160  8e 42 a0 b7 ea 88 ec 30  36 98 00 00 b4 5e 22 6c  |.B.....06....^"l|
00000170  19 68 b7 0d 24 71 93 ec  28 a2 62 1a 60 4d bf 4c  |.h..$q..(.b.`M.L|
00000180  9e da f5 35 c2 58 69 76  0e 0d 06 ce ba 0c b0 58  |...5.Xiv.......X|
00000190  ac 4d 75 35 84 05 02 29  91 0d 4b f0 29 96 81 04  |.Mu5...)..K.)...|
000001a0  27 e4 37 04 92 9e 1a 34  54 00 08 70 44 2e 30 31  |'.7....4T..pD.01|
000001b0  77 62 80 01 00 00 ff fb  94 64 22 0e 34 bf 00 fe  |wb.......d".4...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 12 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b0  12 08 00 48 59 00 00 00  |...........HY...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```Thanks for the help.

---

