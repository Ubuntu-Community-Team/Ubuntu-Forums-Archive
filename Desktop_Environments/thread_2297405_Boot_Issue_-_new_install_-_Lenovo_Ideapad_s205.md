---
title: "Boot Issue - new install - Lenovo Ideapad s205"
date: 2015-10-03
forum: Desktop Environments
---

### Post by neil34 on 2015-10-03
Hi there,

I installed Xubuntu yesterday & the setup seemed to go well until restarting the machine gave me the pxe-m0f error. 
I tried a few different things from reading past threads with a similar problem, like changing the boot queue, turning off legacy etc

I ran bootinfoscript as was suggested before and here are the results:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1935736. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy
mount: /dev/sdb2 already mounted or sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624   617,588,735   616,538,112 Data partition (Windows/Linux)
/dev/sda3     617,588,736   625,141,759     7,553,024 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     1,943,551     1,943,552   0 Empty
/dev/sdb2           1,935,736     1,940,279         4,544  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     1,943,495     1,943,496 Data partition (Windows/Linux)
/dev/sdb2       1,935,736     1,940,279         4,544 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A68-2FD4                              vfat       
/dev/sda2        89F8-DB72                              vfat       
/dev/sda3        72bf61d9-18a0-4597-8d0f-44a404d0925d   swap       
/dev/sdb1                                               iso9660    Xubuntu 14.04.3 LTS amd64
/dev/sdb2        B163-D4F2                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  dc 5c 1d 00 00 00 00 00  06 a6 c3 53 00 00 80 00  |.\.........S....|
000001c0  01 00 00 3f e0 b4 00 00  00 00 00 a8 1d 00 00 fe  |...?............|
000001d0  ff ff ef fe ff ff 78 89  1d 00 c0 11 00 00 00 00  |......x.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  dc 5c 1d 00 00 00 00 00  06 a6 c3 53 00 00 80 00  |.\.........S....|
000001c0  01 00 00 3f e0 b4 00 00  00 00 00 a8 1d 00 00 fe  |...?............|
000001d0  ff ff ef fe ff ff 78 89  1d 00 c0 11 00 00 00 00  |......x.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
```

I'm baffled by this and not sure how to continue. Xubuntu is working great from the USB, I'd just like to get it on the actual machine asap. 
Thanks in advance,

Neil

---

### Post by neil34 on 2015-10-03
Friend had a look at some of the issues and suggested I wipe the  existing partitions, do a clean install and also try boot repair.

Still nothing. Here is the boot repair report:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or /mnt/BootInfo/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1935736. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 already mounted or /mnt/BootInfo/sdb1 busy
mount: /dev/sdb2 already mounted or /mnt/BootInfo/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624   617,588,735   616,538,112 Data partition (Linux)
/dev/sda3     617,588,736   625,141,759     7,553,024 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     1,943,551     1,943,552   0 Empty
/dev/sdb2           1,935,736     1,940,279         4,544  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     1,943,495     1,943,496 Data partition (Windows/Linux)
/dev/sdb2       1,935,736     1,940,279         4,544 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B459-2829                              vfat       
/dev/sda2        e66b767e-94ac-4adc-940d-2824555c6968   ext4       
/dev/sda3        8ca80924-5ddc-48f9-93d5-7f9f9cae5c14   swap       
/dev/sdb1                                               iso9660    Xubuntu 14.04.3 LTS amd64
/dev/sdb2        B163-D4F2                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct  3 19:03 ata-WDC_WD3200BPVT-24ZEST0_WD-WXN1E61UWHC1 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct  3 17:33 ata-WDC_WD3200BPVT-24ZEST0_WD-WXN1E61UWHC1-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct  3 17:33 ata-WDC_WD3200BPVT-24ZEST0_WD-WXN1E61UWHC1-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct  3 17:33 ata-WDC_WD3200BPVT-24ZEST0_WD-WXN1E61UWHC1-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Oct  3 18:51 usb-SanDisk_Cruzer_Blade_20060877620F55D27D99-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct  3 17:33 usb-SanDisk_Cruzer_Blade_20060877620F55D27D99-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct  3 18:53 usb-SanDisk_Cruzer_Blade_20060877620F55D27D99-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Oct  3 19:03 wwn-0x50014ee206501ba4 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct  3 17:33 wwn-0x50014ee206501ba4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct  3 17:33 wwn-0x50014ee206501ba4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct  3 17:33 wwn-0x50014ee206501ba4-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /mnt                     ext4       (rw)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
else
  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e66b767e-94ac-4adc-940d-2824555c6968' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
	else
	  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
	fi
	linux	/boot/vmlinuz-3.19.0-30-generic root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.19.0-30-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e66b767e-94ac-4adc-940d-2824555c6968' {
	menuentry 'Ubuntu, with Linux 3.19.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-30-generic-advanced-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-30-generic ...'
		linux	/boot/vmlinuz-3.19.0-30-generic root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-30-generic-recovery-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-30-generic ...'
		linux	/boot/vmlinuz-3.19.0-30-generic root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-25-generic ...'
		linux	/boot/vmlinuz-3.19.0-25-generic root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-25-generic ...'
		linux	/boot/vmlinuz-3.19.0-25-generic root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic.efi.signed root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-e66b767e-94ac-4adc-940d-2824555c6968' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e66b767e-94ac-4adc-940d-2824555c6968
		else
		  search --no-floppy --fs-uuid --set=root e66b767e-94ac-4adc-940d-2824555c6968
		fi
		echo	'Loading Linux 3.19.0-15-generic ...'
		linux	/boot/vmlinuz-3.19.0-15-generic.efi.signed root=UUID=e66b767e-94ac-4adc-940d-2824555c6968 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-15-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root B459-2829
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e66b767e-94ac-4adc-940d-2824555c6968 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=B459-2829  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=8ca80924-5ddc-48f9-93d5-7f9f9cae5c14 none            swap    sw              0       0
UUID=B459-2829	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  dc 5c 1d 00 00 00 00 00  06 a6 c3 53 00 00 80 00  |.\.........S....|
000001c0  01 00 00 3f e0 b4 00 00  00 00 00 a8 1d 00 00 fe  |...?............|
000001d0  ff ff ef fe ff ff 78 89  1d 00 c0 11 00 00 00 00  |......x.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  dc 5c 1d 00 00 00 00 00  06 a6 c3 53 00 00 80 00  |.\.........S....|
000001c0  01 00 00 3f e0 b4 00 00  00 00 00 a8 1d 00 00 fe  |...?............|
000001d0  ff ff ef fe ff ff 78 89  1d 00 c0 11 00 00 00 00  |......x.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/21858/mounts) leaked on lvs invocation. Parent PID 17665: bash
File descriptor 63 (pipe:[1726298]) leaked on lvs invocation. Parent PID 17665: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-10-03__18h51 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
boot-repair is executed in live-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="B459-2829" TYPE="vfat"
/dev/sda2: UUID="e66b767e-94ac-4adc-940d-2824555c6968" TYPE="ext4"
/dev/sda3: UUID="8ca80924-5ddc-48f9-93d5-7f9f9cae5c14" TYPE="swap"
/dev/sdb1: LABEL="Xubuntu 14.04.3 LTS amd64" TYPE="iso9660"
/dev/sdb2: SEC_TYPE="msdos" UUID="B163-D4F2" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

dd: invalid number ‘0’
Warning: /var/log/boot-sav/log/2015-10-03__18h51boot-repair19/sdb/current_mbr.img could not be created. Please report this message to boot.repair@gmail.com

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct  3 18:48 grub.d
total 80
-rwxr-xr-x 1 root root  9424 Jun 26 11:16 00_header
-rwxr-xr-x 1 root root  6058 May 13 14:51 05_debian_theme
-rwxr-xr-x 1 root root 11608 Jun 26 11:16 10_linux
-rwxr-xr-x 1 root root 10412 Jun 26 11:16 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root   170 Oct  3 18:48 25_custom
-rwxr-xr-x 1 root root 11692 Jun 26 11:16 30_os-prober
-rwxr-xr-x 1 root root  1416 Jun 26 11:16 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 26 11:16 40_custom
-rwxr-xr-x 1 root root   216 Jun 26 11:16 41_custom
-rw-r--r-- 1 root root   483 Jun 26 11:16 README




=================== /mnt/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda2: UUID=B459-2829	 (sda1)
ls /sys/firmware/efi/vars : Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,Time-470733de-df43-448b-8b45-4eeb0df8c812,SmmS3NvsData-8983fd2d-113c-4e2b-8f47-0abfeb20a41a,SMBIOSMEMSIZE-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSLEN-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOGNUMBER-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOG000-c3eeae98-23bf-412b-ab60-efcbb48e1534,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ProtectedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PreDefinedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PbaStatusVar-0ec1a7f5-4904-40a0-8eab-4bcc4666da45,OpromDevicePath-8be4df61-93ca-11d2-aa0d-00e098032b8c,OemVariable-4fee3d67-18f4-4217-ba7b-bc538148382a,OemS3Variable-90699783-eba4-43d8-9f21-3fd2eb0d00a9,OemPlatform-e06a642a-3fe0-440a-89dc-9a6fb8c042f6,new_var,MTC-eb704011-1402-11d3-8e77-00a0c969723b,MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23,MemoryTypeInformationBackup-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,MemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,LastBootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,HDDPWD-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,dump-type0-4-1360834324-cfc8fc79-be2e-4ddc-97f0-9f98bfe298a0,dump-type0-1-1360834322-cfc8fc79-be2e-4ddc-97f0-9f98bfe298a0,DIAGSPLSHSCRN-8be4df61-93ca-11d2-aa0d-00e098032b8c,del_var,Module_Header-80e4ecbe-0672-4de0-9a12-205c7276a77e,Custom,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrderDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to boot.repair@gmail.com

=================== efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0005,0006
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0003* ATA HDD0: WDC WD3200BPVT-24ZEST0                  	ACPI(a0341d0,0)PCI(11,0)ATAPI(0,0,0)..bYVD.A...O.*..
Boot0004* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0005* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0006* PCI LAN: Realtek PXE B02 D00	BIOS(6,0,5265616c74656b20505845204230322044303000)..................@.......@...@.............................................A.....................

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt.
sdb2	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb2.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	0 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
1      1049kB  538MB  537MB   fat32                 boot
2      538MB   316GB  316GB   ext4
3      316GB   320GB  3867MB  linux-swap(v1)


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:4096:gpt:ATA WDC WD3200BPVT-2;
1:1049kB:538MB:537MB:fat32::boot;
2:538MB:316GB:316GB:ext4::;
3:316GB:320GB:3867MB:linux-swap(v1)::;

Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL    UUID
sda   disk          298.1G          WDC WD32
sda1  part vfat       512M                   B459-2829
sda2  part ext4       294G                   e66b767e-94ac-4adc-940d-2824555c6968
sda3  part swap       3.6G                   8ca80924-5ddc-48f9-93d5-7f9f9cae5c14
sdb   disk iso9660   14.9G Xubuntu 14.04.3 LTS amd64
Cruzer B
sdb1  part iso9660    949M Xubuntu 14.04.3 LTS amd64

sdb2  part vfat       2.2M                   B163-D4F2
loop0 loop squashfs   908M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt
sda3     1  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0
sdb2     1  0  0
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xubuntu)
/dev/sda2 on /mnt type ext4 (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 input kfd kmsg kvm log mapper mcelog media0 mem memory_bandwidth net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 29 28 59 b4 4e  4f 20 4e 41 4d 45 20 20  |..))(Y.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 3c 90 6d 6b 66 73 2e  66 61 74 00 02 04 01 00  |.<.mkfs.fat.....|
00000010  02 00 02 c0 11 f8 04 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 80 00 29 f2  d4 63 b1 4e 4f 20 4e 41  |......)..c.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 0e 1f  |ME    FAT12   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   1.8G  817M  960M  46% /
udev           devtmpfs  1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs     356M  1.2M  354M   1% /run
/dev/sdb       iso9660   949M  949M     0 100% /cdrom
/dev/loop0     squashfs  908M  908M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1.8G   88K  1.8G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.8G   80K  1.8G   1% /run/shm
none           tmpfs     100M   28K  100M   1% /run/user
/dev/sda2      ext4      290G  3.8G  271G   2% /mnt
/dev/sda1      vfat      511M  7.1M  504M   2% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53c3a606

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0     1943551      971776    0  Empty
/dev/sdb2         1935736     1940279        2272   ef  EFI (FAT-12/16/32)

Disk /dev/sdb1: 995 MB, 995098624 bytes
255 heads, 63 sectors/track, 120 cylinders, total 1943552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53c3a606

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0     1943551      971776    0  Empty
/dev/sdb1p2         1935736     1940279        2272   ef  EFI (FAT-12/16/32)




=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems   use-standard-efi-file rename-ms-efi


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (320GB) disk!


=================== User settings
The settings chosen by the user will purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda2, using the following options: upgrade-grub       sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems   use-standard-efi-file rename-ms-efi


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
umount: /mnt: device is busy.
(In some cases useful info about processes that use
the device is found by lsof(8) or fuser(1))

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda1
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda2
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sdb2
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
/dev/sdb2: 4 files, 1117/1125 clusters
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32
rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi.grb
rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi.grb
rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi.grb
Mount sda1 on /mnt/boot/efi
ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /Microsoft/Boot
chroot /mnt apt-get -y --force-yes update
Purge the GRUB of sda2
Install last GRUB version in /mnt/etc/apt/sources.list
chroot /mnt apt-get -y --force-yes update
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: You may want to run apt-get update to correct these problems
grub-efi-amd64-signed available

The following extra packages will be installed:
grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common
Suggested packages:
multiboot-doc grub-emu xorriso
The following packages will be upgraded:
grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
grub2-common
5 upgraded, 0 newly installed, 0 to remove and 967 not upgraded.
DEBCHECK debOK, grub-efi-amd64-signed
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo chroot "/mnt" dpkg --configure -ansudo chroot "/mnt" apt-get install -fynsudo chroot "/mnt" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct  3 18:55 grub.d
total 8
-rwxr-xr-x 1 root root 1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root  170 Oct  3 18:48 25_custom


/boot/efi detected in the fstab of sda2: UUID=B459-2829	 (sda1)
shim-signed available
linux-signed-generic available
Then type: sudo chroot "/mnt" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct  3 19:00 grub.d
drwxr-xr-x  2 root root    4096 Oct  3 18:55 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 Apr  6 20:43 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6 20:43 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6 20:43 20_linux_xen
-rwxr-xr-x 1 root root 11692 Apr  6 20:43 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6 20:43 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6 20:43 40_custom
-rwxr-xr-x 1 root root   216 Apr  6 20:43 41_custom
-rw-r--r-- 1 root root   483 Apr  6 20:43 README




=================== /mnt/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda2: UUID=B459-2829	 (sda1)
Unhide GRUB boot menu in sda2/etc/default/grub

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct  3 19:00 grub.d
drwxr-xr-x  2 root root    4096 Oct  3 18:55 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 Apr  6 20:43 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6 20:43 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6 20:43 20_linux_xen
-rwxr-xr-x 1 root root 11692 Apr  6 20:43 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6 20:43 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6 20:43 40_custom
-rwxr-xr-x 1 root root   216 Apr  6 20:43 41_custom
-rw-r--r-- 1 root root   483 Apr  6 20:43 README




=================== /mnt/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda2: UUID=B459-2829	 (sda1)

*******lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310] [1002:9802]
Subsystem: Lenovo Device [17aa:397b]
Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1,grub-install (GRUB) 2.

chroot /mnt efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0005,0006
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0003* ATA HDD0: WDC WD3200BPVT-24ZEST0                  	ACPI(a0341d0,0)PCI(11,0)ATAPI(0,0,0)..bYVD.A...O.*..
Boot0004* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0005* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0006* PCI LAN: Realtek PXE B02 D00	BIOS(6,0,5265616c74656b20505845204230322044303000)..................@.......@...@.............................................A.....................

chroot /mnt uname -r
Kernel: 3.19.0-25-generic

Reinstall the grub-efi-amd64-signed shim-signed linux-signed-generic of sda2
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /Microsoft/Boot
df /dev/sda1
cp /mnt/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
df /dev/sda1
cp /mnt/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
df /dev/sda1
cp /mnt/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot/efi/EFI/Boot/bootx64.efi (& .grb)
ls sda1/efi: /Microsoft/Boot/bootx64.efi.grb /Microsoft/Boot/bootx64.efi /Microsoft/Boot/bootmgfw.efi.grb /Microsoft/Boot/bootmgfw.efi /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /Microsoft/Boot /Boot/bootx64.efi.grb /Boot/bootx64.efi
Add /mnt/boot/efi efi entries in /mnt/etc/grub.d/25_custom
Adding custom /mnt/boot/efi/EFI/ubuntu/MokManager.efi

chroot /mnt efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0005,0006
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:	030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0003* ATA HDD0: WDC WD3200BPVT-24ZEST0                  	ACPI(a0341d0,0)PCI(11,0)ATAPI(0,0,0)..bYVD.A...O.*..
Boot0004* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0005* USB CD:	030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0006* PCI LAN: Realtek PXE B02 D00	BIOS(6,0,5265616c74656b20505845204230322044303000)..................@.......@...@.............................................A.....................

chroot /mnt update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (320GB) disk!
```

---

### Post by oldfred on 2015-10-03
Your first install did not have a Linux partition, just FAT32 & swap. 

Your second install is not showing all the efi files in the ESP - efi system partition as the first install showed. But Boot-Repair shows copying them into /EFI/Boot? Did script just not show them.

What brand model system. 
The sudo efibootmgr -v is not showing an ubuntu entry, but because Boot-Repair copied grub to bootx64.efi, it should boot from a hard drive boot entry. I do not see on for UEFI hard drive.

This should work as defaults internally are sda1.
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"

Errors from Boot-Repair seem to be mostly related to sdb. How did you create flash drive installer?

---

