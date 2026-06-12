---
title: "New to linux, steam game installation issue, insufficiant disk space"
date: 2019-07-28
forum: Gaming &amp; Leisure
---

### Post by no-win10 on 2019-07-28
So I have been stumbling my way through my first Linux / ubuntu install. I managed to get steam installed and also Good old game galaxy, but I have a problem with both of them.
They both tell me that there is insufficient disk space. I have a 2 terabyte firecuda hard drive that has nothing but ubuntu on it. I know there is plenty of drive space. So I went hunting. . . .

I found that upon installation ubuntu made two partitions on my hard drive one labelled ubuntu, 1.1gb available of a total 8.4, and one labelled 2.0 tb volume and this one says 2tb available of 2tb. 

So when I tried to create a new file path into this bigger 2tb partition when trying to install a steam game it told me I did not have the required permission to create a new folder. 
In the properties menu of this when I try to change the permission so I can create a new folder it says I am not the owner and can not change it. The owner is root.

I am not sure what to do, I am completely new to linux.

---

### Post by mastablasta on 2019-07-29
you need administrator password to change the ownership.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

you can change permissions in nautilus file manager, but you have to run it as administrator. 

```
sudo -H nautilus
```

but i would say that your installation is strange and i am not sure what you intended to do. 

if you wanted to create a / root file system (kind of like c:\ in windows) where the OS would be and separate /home (kind of like My Documents) then this is what you should do when setting up during manual install. if you have only 8 GB for os, that will not be enough.

we have no idea what you did at OS install. so create a boot info summary and post the results in code (the # icon in advanced answer) tags:
boot info: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

also installing Steam in Ubuntu is easy. you just select it in software center and click install.

---

### Post by no-win10 on 2019-07-29
When I installed ubunut all I did was follow the on screen prompts, kind  of like windows install. I didn't intend to do anything except for  install the os. I didn't know it was doing anything odd.

ok here is the boot info summary, Hope I did it right.

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32832 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 3,907,028,991 3,907,026,944  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 29.3 GiB, 31482445824 bytes, 61489152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    61,489,151    61,487,104   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        05a901fb-87c8-41e3-81fa-b26191bb13b7   ext4       
/dev/sdb1        DA93-FC23                              vfat       UBUNTU 18_0

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 29 07:36 ata-ST2000DX002-2DV164_Z4Z741PS -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 07:36 ata-ST2000DX002-2DV164_Z4Z741PS-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jul 29 07:36 usb-SanDisk_Cruzer_Dial_4C531001470620111370-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 29 07:36 usb-SanDisk_Cruzer_Dial_4C531001470620111370-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jul 29 07:36 wwn-0x5000c500937db472 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 07:36 wwn-0x5000c500937db472-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7 ext4       (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
else
  search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
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
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-05a901fb-87c8-41e3-81fa-b26191bb13b7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
    else
      search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
    fi
        linux    /boot/vmlinuz-4.18.0-15-generic root=UUID=05a901fb-87c8-41e3-81fa-b26191bb13b7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.18.0-15-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-05a901fb-87c8-41e3-81fa-b26191bb13b7' {
    menuentry 'Ubuntu, with Linux 4.18.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-advanced-05a901fb-87c8-41e3-81fa-b26191bb13b7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
        else
          search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
        fi
        echo    'Loading Linux 4.18.0-15-generic ...'
            linux    /boot/vmlinuz-4.18.0-15-generic root=UUID=05a901fb-87c8-41e3-81fa-b26191bb13b7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-recovery-05a901fb-87c8-41e3-81fa-b26191bb13b7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
        else
          search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
        fi
        echo    'Loading Linux 4.18.0-15-generic ...'
            linux    /boot/vmlinuz-4.18.0-15-generic root=UUID=05a901fb-87c8-41e3-81fa-b26191bb13b7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-15-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
    else
      search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  05a901fb-87c8-41e3-81fa-b26191bb13b7
    else
      search --no-floppy --fs-uuid --set=root 05a901fb-87c8-41e3-81fa-b26191bb13b7
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=05a901fb-87c8-41e3-81fa-b26191bb13b7 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1856.131763458 = 1993.006305280 boot/grub/grub.cfg                             2
1048.135814667 = 1125.427261440 boot/grub/i386-pc/core.img                     1
   4.235347748 = 4.547670016    boot/vmlinuz-4.18.0-15-generic                 2
   4.235347748 = 4.547670016    vmlinuz                                        2
1857.309696198 = 1994.271100928 boot/initrd.img-4.18.0-15-generic              2
1857.309696198 = 1994.271100928 initrd.img                                     2
1857.309696198 = 1994.271100928 initrd.img.old                                 2

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

set timeout=5
menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/13730/mountinfo) leaked on lvs invocation. Parent PID 21094: bash
File descriptor 63 (pipe:[1482392]) leaked on lvs invocation. Parent PID 21094: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 20190729_0736 ===================
boot-info version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-info is executed in live-session (Ubuntu 18.04.2 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda1:Ubuntu 18.04.2 LTS (18.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="05a901fb-87c8-41e3-81fa-b26191bb13b7" TYPE="ext4" PARTUUID="3eb44ff9-01"
/dev/sdb1: LABEL="UBUNTU 18_0" UUID="DA93-FC23" TYPE="vfat" PARTUUID="00c3eeb1-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


=================== /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Feb  9 19:15 grub.d
total 80
-rwxr-xr-x 1 root root 10046 Feb  7 18:20 00_header
-rwxr-xr-x 1 root root  6258 Feb  4 14:10 05_debian_theme
-rwxr-xr-x 1 root root 12693 Feb  7 18:20 10_linux
-rwxr-xr-x 1 root root 11298 Feb  7 18:20 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Feb  7 18:20 30_os-prober
-rwxr-xr-x 1 root root  1418 Feb  7 18:20 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Feb  7 18:20 40_custom
-rwxr-xr-x 1 root root   216 Feb  7 18:20 41_custom
-rw-r--r-- 1 root root   483 Feb  7 18:20 README




=================== /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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



/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001,0000
Boot0000* Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.S.T.2.0.0.0.D.X.0.0.2.-.2.D.V.1.6.4....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.7.Z.1.4.S.P........BO..NO........q.S.a.n.D.i.s.k....................A.............................>..Gd-.;.A..MQ..L.4.C.5.3.1.0.0.1.4.7.0.6.2.0.1.1.1.3.7.0........BO
Boot0002* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(21,0)/HD(1,MBR,0xc3eeb1,0x800,0x3aa3800)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
No EFI in dmseg.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:4096:msdos:ATA ST2000DX002-2DV1:;
1:1049kB:2000GB:2000GB:ext4::boot;

BYT;
/dev/sdb:31.5GB:scsi:512:512:msdos:SanDisk Cruzer Dial:;
1:1049kB:31.5GB:31.5GB:fat32::boot, lba;

=================== lsblk:
KNAME  TYPE FSTYPE     SIZE LABEL
loop0  loop squashfs   1.8G
loop1  loop squashfs    91M
loop2  loop squashfs  34.6M
loop3  loop squashfs 140.7M
loop4  loop squashfs   2.3M
loop5  loop squashfs    13M
loop6  loop squashfs  14.5M
loop7  loop squashfs   3.7M
loop8  loop squashfs  54.4M
loop9  loop squashfs 341.5M
loop11 loop squashfs    56K
loop12 loop squashfs    74M
loop13 loop squashfs 218.6M
sda    disk            1.8T
sda1   part ext4       1.8T
sdb    disk           29.3G
sdb1   part vfat      29.3G UBUNTU 18_0

KNAME  ROTA RO RM STATE   MOUNTPOINT
loop0     1  1  0         /rofs
loop1     1  1  0         /snap/core/6350
loop2     1  1  0         /snap/gtk-common-themes/818
loop3     1  1  0         /snap/gnome-3-26-1604/74
loop4     1  1  0         /snap/gnome-calculator/260
loop5     1  1  0         /snap/gnome-characters/139
loop6     1  1  0         /snap/gnome-logs/45
loop7     1  1  0         /snap/gnome-system-monitor/57
loop8     1  1  0         /snap/core18/1066
loop9     1  1  0         /snap/gog-galaxy-wine/127
loop11    1  1  0         /snap/cncra/59
loop12    1  1  0         /snap/wine-platform-3-stable/6
loop13    1  1  0         /snap/wine-platform-runtime/23
sda       1  0  0 running
sda1      1  0  0         /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7
sdb       1  0  1 running
sdb1      1  0  1         /cdrom


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8161020k,nr_inodes=2040255,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1643292k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=19799)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1643288k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_818.snap on /snap/gtk-common-themes/818 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_74.snap on /snap/gnome-3-26-1604/74 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_260.snap on /snap/gnome-calculator/260 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_139.snap on /snap/gnome-characters/139 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_45.snap on /snap/gnome-logs/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_57.snap on /snap/gnome-system-monitor/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1066.snap on /snap/core18/1066 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gog-galaxy-wine_127.snap on /snap/gog-galaxy-wine/127 type squashfs (ro,nodev,relatime,x-gdu.hide)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=1643292k,mode=755)
nsfs on /run/snapd/ns/gog-galaxy-wine.mnt type nsfs (rw)
nsfs on /run/snapd/ns/gnome-system-monitor.mnt type nsfs (rw)
/var/lib/snapd/snaps/cncra_59.snap on /snap/cncra/59 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/wine-platform-3-stable_6.snap on /snap/wine-platform-3-stable/6 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/wine-platform-runtime_23.snap on /snap/wine-platform-runtime/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
nsfs on /run/snapd/ns/cncra.mnt type nsfs (rw)
/dev/sda1 on /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7 type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse gpiochip0 gpiochip1 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kfd kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp pps0 psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sev sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  1.9M  1.6G   1% /run
/dev/sdb1      vfat       30G  1.9G   28G   7% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   7.9G  6.9G  1.1G  87% /
tmpfs          tmpfs     7.9G  112M  7.8G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.9G  426M  7.5G   6% /tmp
tmpfs          tmpfs     1.6G   96K  1.6G   1% /run/user/999
/dev/loop1     squashfs   91M   91M     0 100% /snap/core/6350
/dev/loop2     squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop3     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop4     squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop5     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop6     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop7     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop8     squashfs   55M   55M     0 100% /snap/core18/1066
/dev/loop9     squashfs  342M  342M     0 100% /snap/gog-galaxy-wine/127
/dev/loop11    squashfs  128K  128K     0 100% /snap/cncra/59
/dev/loop12    squashfs   74M   74M     0 100% /snap/wine-platform-3-stable/6
/dev/loop13    squashfs  219M  219M     0 100% /snap/wine-platform-runtime/23
/dev/sda1      ext4      1.8T  6.6G  1.7T   1% /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7

=================== fdisk -l:
Disk /dev/loop0: 1.8 GiB, 1905045504 bytes, 3720792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x3eb44ff9

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1  *     2048 3907028991 3907026944  1.8T 83 Linux


Disk /dev/sdb: 29.3 GiB, 31482445824 bytes, 61489152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00c3eeb1

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 61489151 61487104 29.3G  c W95 FAT32 (LBA)


Disk /dev/loop8: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 341.5 MiB, 358055936 bytes, 699328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 56 KiB, 57344 bytes, 112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 74 MiB, 77565952 bytes, 151496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 218.6 MiB, 229195776 bytes, 447648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?


=================== Final advice in case of suggested repair


The boot files of [Ubuntu 18.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot-Repair]. (https://help.ubuntu.com/community/BootPartition)


=================== User settings
The settings chosen by the user will not act on the boot.




```

---

### Post by mastablasta on 2019-07-29
so you have 2 disks. one is a USB key and the other one is a hard disk. hard disk is mounted as media, which suggest you haven't installed to the hard disk. or am i wrong? or you just booted into live session when you created the report?

```
/dev/sda1        05a901fb-87c8-41e3-81fa-b26191bb13b7   ext4       
/dev/sdb1        DA93-FC23                              vfat       UBUNTU 18_0
```

it does show 6.6. GB used on the 2 TB drive.
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&quot]Filesystem     Type      Size  Used Avail Use% Mounted on
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]/dev/sda1      ext4      1.8T  6.6G  1.7T   1% /media/ubuntu/05a901fb-87c8-41e3-81fa-b26191bb13b7[/FONT][/COLOR]
```

is that the OS? is anything  recorded on sda1?

you can see parittions displayed in a nicer way in gparted. as i understand you have one hard disk and that is where you want Ubuntu as well as home folder. 
this is the installation procedure: [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

your sda disk in gparted should looks something similar to this: [https://linuxhint.com/wp-content/uploads/2018/12/8-23.png](https://linuxhint.com/wp-content/uploads/2018/12/8-23.png)

but you will have 2 TB size. so it will be efi partition and / (root)


sda = first disk (or disk "a")
sda1 = first disk, first partition
sda2 = first disk, second partition ...

sdb = second disk (or disk "b")
sdb1 =second disk, first partition
sdb2 =secodn disk, second partition...

---

### Post by oldfred on 2019-07-29
It also looks like you have a newer UEFI hardware system, but have installed in the older BIOS/MBR configuration.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Default install is now one / (root) partition unless you choose to use Something Else and create your own partition(s). If UEFI it also creates an ESP - efi system partition.

But it seems like  you must have rebooted back into the live installer and then you do not have room to install into it.

Since new UEFI system, you have to have UEFI Secure Boot off, and CSM/Legacy/BIOS boot mode on in UEFI settings to boot in the old BIOS boot mode.

May be better to reinstall in UEFI boot mode with gpt partitioning.
More info on UEFI in link in my signature below.

---

### Post by no-win10 on 2019-07-30
So I just decided to reinstall ubuntu. This fixed my problems. Some must have happened during the first install. I am not sure what that was but everything seems to work fine now.
I only have one drive and when some thing needs permission it asks me for my password now.

So this first time I installed ubuntu there were three option : 1) delete current os and install ubuntu
                                                                                       2) delete the whole drive and install ubuntu
                                                                                       3) some other custome options

The firs time I installed I chose option 1, this time around I went with option 2. This seemed to work fine. Here is another boot info summary of this new install. Everything seem to be working fine so I assume this all looks fine.

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/BOOT/fbx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2             1,050,624 3,907,028,991 3,905,978,368 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop15                                             squashfs   
/dev/loop16                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        915D-5C33                              vfat       
/dev/sda2        e5d501ae-1937-4f6f-b6fa-a2a9421b2186   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 30 09:11 ata-ST2000DX002-2DV164_Z4Z741PS -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 30 09:11 ata-ST2000DX002-2DV164_Z4Z741PS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 30 09:11 ata-ST2000DX002-2DV164_Z4Z741PS-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Jul 30 09:11 wwn-0x5000c500937db472 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 30 09:11 wwn-0x5000c500937db472-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 30 09:11 wwn-0x5000c500937db472-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro)


========================== sda1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid e5d501ae-1937-4f6f-b6fa-a2a9421b2186 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
else
  search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
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
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
    else
      search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
    fi
        linux    /boot/vmlinuz-4.18.0-25-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.18.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
    menuentry 'Ubuntu, with Linux 4.18.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-25-generic-advanced-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        else
          search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        fi
        echo    'Loading Linux 4.18.0-25-generic ...'
            linux    /boot/vmlinuz-4.18.0-25-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-25-generic-recovery-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        else
          search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        fi
        echo    'Loading Linux 4.18.0-25-generic ...'
            linux    /boot/vmlinuz-4.18.0-25-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-advanced-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        else
          search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        fi
        echo    'Loading Linux 4.18.0-15-generic ...'
            linux    /boot/vmlinuz-4.18.0-15-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-recovery-e5d501ae-1937-4f6f-b6fa-a2a9421b2186' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        else
          search --no-floppy --fs-uuid --set=root e5d501ae-1937-4f6f-b6fa-a2a9421b2186
        fi
        echo    'Loading Linux 4.18.0-15-generic ...'
            linux    /boot/vmlinuz-4.18.0-15-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.18.0-15-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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
UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=915D-5C33  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1520.659164429 = 1632.795344896 boot/grub/grub.cfg                             3
   4.719722748 = 5.067763712    boot/vmlinuz-4.18.0-15-generic                 2
   5.485500336 = 5.890011136    boot/vmlinuz-4.18.0-25-generic                 1
   4.719722748 = 5.067763712    vmlinuz                                        2
 101.352535248 = 108.826456064  boot/initrd.img-4.18.0-15-generic              2
 101.594722748 = 109.086502912  boot/initrd.img-4.18.0-25-generic              2
 101.352535248 = 108.826456064  initrd.img                                     2
 101.352535248 = 108.826456064  initrd.img.old                                 2


ADDITIONAL INFORMATION :
=================== log of boot-info 20190730_0911 ===================
boot-info version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-info is executed in installed-session (Ubuntu 18.04.2 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.18.0-25-generic root=UUID=e5d501ae-1937-4f6f-b6fa-a2a9421b2186 ro quiet splash vt.handoff=1

=================== os-prober:
/dev/sda2:The OS now in use - Ubuntu 18.04.2 LTS CurrentSession:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="915D-5C33" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="473434d6-6082-4659-a793-457484352035"
/dev/sda2: UUID="e5d501ae-1937-4f6f-b6fa-a2a9421b2186" TYPE="ext4" PARTUUID="3eacc339-2e0e-44d9-8281-362c718738be"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 29 08:43 grub.d
total 80
-rwxr-xr-x 1 root root 10046 Feb  7 18:20 00_header
-rwxr-xr-x 1 root root  6258 Feb  4 14:10 05_debian_theme
-rwxr-xr-x 1 root root 12693 Feb  7 18:20 10_linux
-rwxr-xr-x 1 root root 11298 Feb  7 18:20 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Feb  7 18:20 30_os-prober
-rwxr-xr-x 1 root root  1418 Feb  7 18:20 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Feb  7 18:20 40_custom
-rwxr-xr-x 1 root root   216 Feb  7 18:20 41_custom
-rw-r--r-- 1 root root   483 Feb  7 18:20 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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



/boot/efi detected in the fstab of sda2: UUID=915D-5C33   (sda1)
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbx64.efi
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0001,0000
Boot0000* Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.S.T.2.0.0.0.D.X.0.0.2.-.2.D.V.1.6.4....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.7.Z.1.4.S.P........BO
Boot0003* ubuntu    HD(1,GPT,473434d6-6082-4659-a793-457484352035,0x800,0x100000)/File(EFIUBUNTUSHIMX64.EFI)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /boot/efi.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:4096:gpt:ATA ST2000DX002-2DV1:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:2000GB:2000GB:ext4::;

=================== lsblk:
KNAME  TYPE FSTYPE     SIZE LABEL
loop0  loop squashfs   2.3M
loop1  loop squashfs  54.4M
loop2  loop squashfs    13M
loop3  loop squashfs  14.5M
loop4  loop squashfs  34.6M
loop5  loop squashfs    91M
loop6  loop squashfs   3.7M
loop7  loop squashfs 140.7M
loop8  loop squashfs 140.7M
loop9  loop squashfs 341.5M
loop10 loop squashfs 149.9M
loop11 loop squashfs  1008K
loop12 loop squashfs  14.8M
loop13 loop squashfs   3.7M
loop14 loop squashfs     4M
loop15 loop squashfs  88.5M
loop16 loop squashfs  42.8M
sda    disk            1.8T
sda1   part vfat       512M
sda2   part ext4       1.8T

KNAME  ROTA RO RM STATE   MOUNTPOINT
loop0     1  1  0         /snap/gnome-calculator/260
loop1     1  1  0         /snap/core18/1066
loop2     1  1  0         /snap/gnome-characters/139
loop3     1  1  0         /snap/gnome-logs/45
loop4     1  1  0         /snap/gtk-common-themes/818
loop5     1  1  0         /snap/core/6350
loop6     1  1  0         /snap/gnome-system-monitor/57
loop7     1  1  0         /snap/gnome-3-26-1604/74
loop8     1  1  0         /snap/gnome-3-26-1604/90
loop9     1  1  0         /snap/gog-galaxy-wine/127
loop10    1  1  0         /snap/gnome-3-28-1804/67
loop11    1  1  0         /snap/gnome-logs/61
loop12    1  1  0         /snap/gnome-characters/296
loop13    1  1  0         /snap/gnome-system-monitor/100
loop14    1  1  0         /snap/gnome-calculator/406
loop15    1  1  0         /snap/core/7270
loop16    1  1  0         /snap/gtk-common-themes/1313
sda       1  0  0 running
sda1      1  0  0         /boot/efi
sda2      1  0  0         /


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8151132k,nr_inodes=2037783,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1643288k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=639)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
/var/lib/snapd/snaps/gnome-logs_45.snap on /snap/gnome-logs/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_74.snap on /snap/gnome-3-26-1604/74 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_260.snap on /snap/gnome-calculator/260 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_57.snap on /snap/gnome-system-monitor/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1066.snap on /snap/core18/1066 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_139.snap on /snap/gnome-characters/139 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_818.snap on /snap/gtk-common-themes/818 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_90.snap on /snap/gnome-3-26-1604/90 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gog-galaxy-wine_127.snap on /snap/gog-galaxy-wine/127 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_67.snap on /snap/gnome-3-28-1804/67 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_61.snap on /snap/gnome-logs/61 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_296.snap on /snap/gnome-characters/296 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_100.snap on /snap/gnome-system-monitor/100 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_406.snap on /snap/gnome-calculator/406 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_7270.snap on /snap/core/7270 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1313.snap on /snap/gtk-common-themes/1313 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/121 type tmpfs (rw,nosuid,nodev,relatime,size=1643284k,mode=700,uid=121,gid=125)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1643284k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse gpiochip0 gpiochip1 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kfd kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp pps0 psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sev sg0 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 00 04 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 33 5c 5d 91 4e  4f 20 4e 41 4d 45 20 20  |..)3].NO NAME  |
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  2.1M  1.6G   1% /run
/dev/sda2      ext4      1.8T  111G  1.6T   7% /
tmpfs          tmpfs     7.9G   36M  7.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/loop3     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop7     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop0     squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop6     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop1     squashfs   55M   55M     0 100% /snap/core18/1066
/dev/loop2     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop4     squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop5     squashfs   91M   91M     0 100% /snap/core/6350
/dev/loop8     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/90
/dev/loop9     squashfs  342M  342M     0 100% /snap/gog-galaxy-wine/127
/dev/loop10    squashfs  150M  150M     0 100% /snap/gnome-3-28-1804/67
/dev/loop11    squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/61
/dev/loop12    squashfs   15M   15M     0 100% /snap/gnome-characters/296
/dev/loop13    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/100
/dev/loop14    squashfs  4.2M  4.2M     0 100% /snap/gnome-calculator/406
/dev/loop15    squashfs   89M   89M     0 100% /snap/core/7270
/dev/loop16    squashfs   43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/sda1      vfat      511M  6.1M  505M   2% /boot/efi
tmpfs          tmpfs     1.6G   16K  1.6G   1% /run/user/121
tmpfs          tmpfs     1.6G   20K  1.6G   1% /run/user/1000

=================== fdisk -l:
Disk /dev/loop0: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AC4863A1-788C-4CF9-91ED-8A9C4577A4EF

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 3907028991 3905978368  1.8T Linux filesystem


Disk /dev/loop8: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 341.5 MiB, 358055936 bytes, 699328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!


=================== User settings
The settings chosen by the user will not act on the boot.



 
``` 

So thank you all for your help. I appreciate it.

---

### Post by oldfred on 2019-07-30
Your install looks fine.

I do prefer to have smaller / (root) partition and large /home and/or data partition.
Installer still defaults to one partition as / as back when drives were much smaller or dual booting a smaller / was ok and avoided issues where one partition may fill up, but other has lots of room. But now with very large TB sized drives, it takes a lot of music or videos to fill a drive.

If new users/home is a better alternative as that automatically gives you ownership & permissions & sets automount via entry in fstab. 
More advanced users may add data partition(s), but then have to manually add mount in fstab & set ownership & permissions to make it usable.

---

### Post by mastablasta on 2019-07-31
looks ok now.

> **no-win10 said:**
> 
I only have one drive and when some thing needs permission it asks me for my password now.


yes, that's one of the security features. it asks for password only when any system files are changed or added. so in theory malware would need to know your password to access the system. 

happy gaming. Linux is really good OS if all works as it should. even for gaming. i am going through old games library getting the old games to run in Play on linux/Wine. old PC (15 years), so i am limited in what i can play. but source games work good so i got some on steam sale, some others on steam work as well (e.g. a story about my uncle). and i loaded a couple of windows platinum/gold games as well such as Hearts of Iron 2, Halo, Oblivion, Torchlight, Farcry, Unreal, UT2004... tried a few native opensource ones such as RedEclipse, Tuxkart, Xonotic, World of Padman, SmokinGuns, Battle for Wesnoth... i also re-played Morrowind using the opensource OpenMW engine and finished the 3 main quests and still have plenty of side quest to do.

---

