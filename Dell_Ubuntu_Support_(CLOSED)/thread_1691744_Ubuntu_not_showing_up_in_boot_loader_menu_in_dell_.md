---
title: "Ubuntu not showing up in boot loader menu in dell inspiron 14r"
date: 2011-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jith87 on 2011-02-20
hi
I own a Dell inspiron 14R with windows7 installed in it. I wish to have a dual boot. He i ve installed ubunutu(without using WUBI). Once i restart after installation, the boot loader menu asks to repair windows without listing Ubuntu. I ve left with no other option but to repair Windows which removes the partition in which I ve installed Ubunutu from windows. 
Can someone help me in modifying the boot loader from windows so that I can use a dual boot option which will allow me to use Win7 as well as Ubunutu.
Thanks

---

### Post by Rubi1200 on 2011-02-20
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Broderben on 2011-09-14
Hej

I have the same problem and my Result.TXT looks like this:

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60672 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   113,185,919   112,979,072   7 NTFS / exFAT / HPFS
/dev/sda3         113,186,814   156,301,311    43,114,498   5 Extended
/dev/sda5         154,224,640   156,301,311     2,076,672  82 Linux swap / Solaris
/dev/sda6         113,186,816   152,145,919    38,959,104  83 Linux
/dev/sda7         152,147,968   154,224,639     2,076,672  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7983 MB, 7983421952 bytes
255 heads, 63 sectors/track, 970 cylinders, total 15592621 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,583,049    15,582,987   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   846B-92CC                              vfat       SD
/dev/sda1        78D69456D694168A                       ntfs       System Reserved
/dev/sda2        66D29E4BD29E1EFD                       ntfs       
/dev/sda5        ada18419-e17e-4b13-9ffb-f0e2b0cd5d10   swap       
/dev/sda6        8aaa215f-4f46-4854-9fc7-7ed768c7aa55   ext4       
/dev/sda7        06a43459-9b73-4ccc-8980-7f6a8f72a283   swap       
/dev/sdb1        1714-245C                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/SD                vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8aaa215f-4f46-4854-9fc7-7ed768c7aa55 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8aaa215f-4f46-4854-9fc7-7ed768c7aa55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8aaa215f-4f46-4854-9fc7-7ed768c7aa55
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 78D69456D694168A
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8aaa215f-4f46-4854-9fc7-7ed768c7aa55 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ada18419-e17e-4b13-9ffb-f0e2b0cd5d10 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=06a43459-9b73-4ccc-8980-7f6a8f72a283 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.474742889 = 67.081744384   boot/grub/core.img                             1
  62.526824951 = 67.137667072   boot/grub/grub.cfg                             1
  55.007057190 = 59.063377920   boot/initrd.img-2.6.38-8-generic               2
  62.850891113 = 67.485630464   boot/vmlinuz-2.6.38-8-generic                  1
  55.007057190 = 59.063377920   initrd.img                                     2
  62.850891113 = 67.485630464   vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by psrdotcom on 2011-09-14
While booting try this
Hold the shift button while booting.. It may display the Operating Systems list to select

---

### Post by garvinrick4 on 2011-09-14
@Broderben, next time it is polite to start your own thread and post results of boot script, you are new so we learn.
do as below Windows first and Ubuntu second. If you do not have a Windows disk we can use another way.

Do the EDIT in red FIRST please then run these commands.
Use your live cd (install cd using try ubuntu)
open a terminal and copy and paste these one at a time.
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --boot-directory=/mnt/boot /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu and:
```
sudo update-grub
```Done: Will now have both as menuentry.

[COLOR=Red]Edit:
You know looking at your Windows install you do not have any boot files in your install.
Do you have your Windows 7 disk. Here is the link to first get your Windows boot files
fixed in your windows install, then run commands above to put grub2 into place so as
to boot both Windows and Ubuntu. 
Only a couple of commands takes no time at all. If you get in a jam just ask.
[/COLOR][Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by garvinrick4 on 2011-09-14
@Broderben
 It has been an hour for a 15 minute process so I am going say you must be up and running and it is 3:50 am here so I am hitting the hay. Enjoy your Ubuntu.
Anything we can do start a thead. Very good of you to post boot_info_script at get go.

---

### Post by Broderben on 2011-09-14
It worked!!! Thanks a lot :D

---

### Post by garvinrick4 on 2011-09-14
> **Broderben said:**
> It worked!!! Thanks a lot :D
You are welcome.

---

### Post by saqibahmed515 on 2012-03-17
Here is my result.txt file. I am unable to boot both windows and ubuntu.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 4591096 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdb1 for its 
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

/dev/sda1               2,048    62,916,607    62,914,560  83 Linux
/dev/sda2    *     62,916,608   125,831,167    62,914,560   7 NTFS / exFAT / HPFS
/dev/sda3         125,831,168   299,808,767   173,977,600   7 NTFS / exFAT / HPFS
/dev/sda4         299,812,862   312,580,095    12,767,234   5 Extended
/dev/sda5         299,812,864   312,580,095    12,767,232  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    15,240,575    15,232,512   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b141249f-573a-4e23-8502-0546ebbed86f   ext4       
/dev/sda2        1505F20842357C17                       ntfs       
/dev/sda3        70BE57932C2115CB                       ntfs       
/dev/sda5        14e0797f-ac32-40c3-9c71-8241813fe0a5   swap       
/dev/sdb1        7225-7CBC                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/70BE57932C2115CB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=b141249f-573a-4e23-8502-0546ebbed86f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=b141249f-573a-4e23-8502-0546ebbed86f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=b141249f-573a-4e23-8502-0546ebbed86f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=b141249f-573a-4e23-8502-0546ebbed86f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b141249f-573a-4e23-8502-0546ebbed86f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 1505F20842357C17
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b141249f-573a-4e23-8502-0546ebbed86f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=14e0797f-ac32-40c3-9c71-8241813fe0a5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic-pae           1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  c0 85 ff 75 9b 85 d2 89  d7 89 d6 75 7d b8 40 0e  |...u.......u}.@.|
00000010  7d c0 e8 49 7d 44 00 8b  55 f0 8b 82 58 01 00 00  |}..I}D..U...X...|
00000020  8d 58 f8 8b 53 08 0f 18  02 90 8b 7d f0 81 c7 58  |.X..S......}...X|
00000030  01 00 00 39 f8 74 38 8b  45 f0 89 75 f0 83 c0 0c  |...9.t8.E..u....|
00000040  89 c6 8d b6 00 00 00 00  8b 43 14 89 f1 8b 55 ec  |.........C....U.|
00000050  8b 80 84 00 00 00 e8 65  22 0f 00 8b 43 08 8d 58  |.......e"...C..X|
00000060  f8 8b 53 08 0f 18 02 90  39 f8 75 dc 8b 75 f0 b8  |..S.....9.u..u..|
00000070  40 0e 7d c0 e8 87 7a 44  00 8b 45 ec 31 d2 e8 1d  |@.}...zD..E.1...|
00000080  31 1d 00 e9 89 fe ff ff  89 d7 8b 45 f0 e8 ae 3e  |1..........E...>|
00000090  fe ff 8b 55 f0 8b 82 84  00 00 00 e8 00 20 1d 00  |...U......... ..|
000000a0  8b 45 ec 89 fe e8 f6 1f  1d 00 89 f0 83 c4 18 5b  |.E.............[|
000000b0  5e 5f 5d c3 8d 74 26 00  bf f4 ff ff ff eb cb 8b  |^_]..t&.........|
000000c0  3d f0 32 80 c0 85 ff 0f  84 b9 fe ff ff 8b 07 89  |=.2.............|
000000d0  45 e8 8b 47 04 83 c7 08  ba 62 fb 17 c0 c7 44 24  |E..G.....b....D$|
000000e0  08 d0 80 00 00 89 d9 89  74 24 04 c7 04 24 c0 00  |........t$...$..|
000000f0  00 00 ff 55 e8 8b 17 85  d2 89 55 e8 75 d4 e9 83  |...U......U.u...|
00000100  fe ff ff 8d b6 00 00 00  00 8d bc 27 00 00 00 00  |...........'....|
00000110  55 89 e5 57 56 53 81 ec  98 00 00 00 0f 1f 44 00  |U..WVS........D.|
00000120  00 83 fa 33 89 c3 89 55  bc 89 4d b4 c7 45 ec 00  |...3...U..M..E..|
00000130  00 00 00 76 73 81 fa 00  00 00 04 76 13 bb f4 ff  |...vs......v....|
00000140  ff ff 81 c4 98 00 00 00  89 d8 5b 5e 5f 5d c3 90  |..........[^_]..|
00000150  89 d0 e8 29 e5 07 00 85  c0 89 45 b8 74 df 8b 4d  |...)......E.t..M|
00000160  bc 89 da bb f2 ff ff ff  e8 d3 a5 1d 00 85 c0 75  |...............u|
00000170  20 8b 75 b8 bf f2 7f 71  c0 b9 04 00 00 00 f3 a6  | .u....q........|
00000180  75 0a 8b 45 b8 66 83 78  10 01 74 34 bb f8 ff ff  |u..E.f.x..t4....|
00000190  ff 8b 45 b8 e8 17 d4 07  00 89 d8 81 c4 98 00 00  |..E.............|
000001a0  00 5b 5e 5f 5d c3 66 90  bb f8 ff ff ff 81 c4 98  |.[^_].f.........|
000001b0  00 00 00 89 d8 5b 5e 5f  5d c3 8d b6 00 00 00 fe  |.....[^_].......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by wildmanne39 on 2013-02-09
Old thread closed.

---

