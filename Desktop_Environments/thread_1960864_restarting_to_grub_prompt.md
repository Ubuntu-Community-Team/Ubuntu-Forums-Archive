---
title: "restarting to grub prompt"
date: 2012-04-18
forum: Desktop Environments
---

### Post by mIXpRo on 2012-04-18
hi,
i had ubuntu 12.04 installed on my system , then on another partition at the same hard drive i installed windows 7 , and of course it overrode the grub2 , so i tried reinstalling the grub2 by booting from livecd 
and when  i used the command :

```

sudo mount /dev/sda4 /mnt 
sudo grub-install --boot-directory=/mnt  /dev/sda 

```after rebooting i got the grub prompt 
```

grup>

```how can i fix this , 
this is the output of : boot info script 
which i ran from the live cd 
> 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr /grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1467320 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   163,914,134   163,707,287   7 NTFS / exFAT / HPFS
/dev/sda3         308,479,998   312,580,095     4,100,098   5 Extended
/dev/sda5         308,480,000   312,580,095     4,100,096  82 Linux swap / Solaris
/dev/sda4         163,915,776   308,477,951   144,562,176  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   975,400,959   975,398,912   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62    15,620,279    15,620,218   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA9042F49042B743                       ntfs       System Reserved
/dev/sda2        F676CFEF76CFAEA5                       ntfs       
/dev/sda4        29c9ffa6-0d77-4920-89de-a51a1b89ab4f   ext4       
/dev/sda5        846f83cf-97ab-4758-bbad-29d39b9f634d   swap       
/dev/sdb1        3C42935F42931CA8                       ntfs       My Book
/dev/sdc1        4A19-AEF6                              vfat       MYLINUXLIVE
/dev/sr1                                                udf        WD SmartWare

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr1         /media/WD SmartWare      udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1

=========================== sda4/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux    /boot/vmlinuz-3.2.0-22-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-22-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    echo    'Loading Linux 3.2.0-22-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-22-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-22-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux    /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-21-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    echo    'Loading Linux 3.2.0-21-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-21-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-21-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux    /boot/vmlinuz-3.2.0-20-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-20-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    echo    'Loading Linux 3.2.0-20-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-20-generic-pae root=UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-20-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 29c9ffa6-0d77-4920-89de-a51a1b89ab4f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root FA9042F49042B743
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
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=29c9ffa6-0d77-4920-89de-a51a1b89ab4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=846f83cf-97ab-4758-bbad-29d39b9f634d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-20-generic-pae           2
               =                boot/initrd.img-3.2.0-21-generic-pae           3
               =                boot/initrd.img-3.2.0-22-generic-pae           3
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/vmlinuz-3.2.0-20-generic-pae              1
               =                boot/vmlinuz-3.2.0-21-generic-pae              2
               =                boot/vmlinuz-3.2.0-22-generic-pae              1
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                grub/core.img                                  1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  6b 00 00 00 50 33 75 0a  6b 00 00 00 6c 00 00 00  |k...P3u.k...l...|
00000010  28 c4 04 0a 6c 00 00 00  6d 00 00 00 e0 46 bc 09  |(...l...m....F..|
00000020  6d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |m...............|
00000030  6f 00 00 00 58 bf 38 0a  6f 00 00 00 00 00 00 00  |o...X.8.o.......|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 72 00 00 00  e0 e3 4a 0a 72 00 00 00  |....r.....J.r...|
00000060  73 00 00 00 88 ba ff 0b  73 00 00 00 00 00 00 00  |s.......s.......|
00000070  00 00 00 00 00 00 00 00  75 00 00 00 c8 96 ac 0b  |........u.......|
00000080  75 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |u...............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000b0  00 00 00 00 7a 00 00 00  00 a0 67 0b 7a 00 00 00  |....z.....g.z...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 19 00 00 00  |................|
000000e0  78 6d 6c 6e 73 3a 73 76  67 00 63 69 74 79 00 35  |xmlns:svg.city.5|
000000f0  18 00 00 00 21 00 00 00  01 00 00 00 00 00 00 00  |....!...........|
00000100  01 00 00 00 a0 7f a0 0b  a0 7f a0 0b a0 7f a0 0b  |................|
00000110  33 61 34 2d 19 00 00 00  4f 70 65 6e 20 5f 50 61  |3a4-....Open _Pa|
00000120  72 65 6e 74 00 6d e4 0b  00 00 00 00 31 00 00 00  |rent.m......1...|
00000130  02 00 00 00 00 00 00 00  74 02 00 00 c0 41 65 0b  |........t....Ae.|
00000140  c0 41 65 0b c0 41 65 0b  75 02 00 00 c0 c7 d4 09  |.Ae..Ae.u.......|
00000150  c0 c7 d4 09 c0 c7 d4 09  00 00 00 00 61 02 00 00  |............a...|
00000160  c8 44 b0 0a c8 f3 62 4d  00 00 00 00 c8 f3 62 4d  |.D....bM......bM|
00000170  00 00 00 00 08 00 00 00  00 00 00 00 32 00 00 00  |............2...|
00000180  00 00 00 00 50 53 b4 0a  30 45 b0 0a e0 99 d7 0b  |....PS..0E......|
00000190  28 99 d7 0b 00 00 00 00  01 00 00 00 00 00 00 00  |(...............|
000001a0  00 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3e 00 00 00  |............>...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected



---

### Post by kc1di on 2012-04-18
Go back to the live cd redo the grub install and this time before rebooting
issue the command 
```
sudo update-grub
```
this will generate the grub configuration file. 

Cheers

---

### Post by mIXpRo on 2012-04-18
thanks for the quick replay,but 
i get this :> 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


---

### Post by kc1di on 2012-04-18
try unmounting sda and try again

---

### Post by kc1di on 2012-04-18
You may want to download and run boot repair. 
It works pretty well.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by mIXpRo on 2012-04-18
i tried :
```

sudo umount /dev/sda

```

and this :
```

sudo umount /mnt

```

but for no good

---

### Post by mIXpRo on 2012-04-18
@kc1di
really thanks , a lot boot repair did it .

---

### Post by kc1di on 2012-04-18
> **mIXpRo said:**
> @kc1di
really thanks , a lot boot repair did it .

your welcome 
Enjoy ;)

---

