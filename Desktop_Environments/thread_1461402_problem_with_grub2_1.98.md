---
title: "problem with grub2 1.98"
date: 2010-04-24
forum: Desktop Environments
---

### Post by mankidavu on 2010-04-24
I'm having a peculiar problem when trying to update to latest grub2.

System:-
Ubuntu 9.10

System takes too much time in the grub (with the default install) ,due to the bug listed at:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
So I tried to update my grub to latest.


Once I update, the grub loads faster but it doesn't boot from any entry,as the last character is missing in each grub command options.
For eg: 

initrd        /boot/initrd.img-2.6.31-21-generic

In the above line, "c" of generic is missing.Same with windows entry also.

Instead of "Chainloader +1" , it shows upto "Chainloader +"

I can get into the command line and manually boot, after editing the line properly and doing a ctrl+x. (or by loading them one by one).


I tried all update grub options.Uninsall to old grub and upgrade and other tweaks.
Tried removing the grub.cfg file and generating it fresh.
All in vain.


I'm posting my boot info,so that if any of you can assist me to resolve this.
At present I'm using grub-pc 1.97 beta4 with the slow loading issue.



```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /grldr /ntldr 
                       /NTDETECT.COM /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf19bf19b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     6,152,894     6,152,832   b W95 FAT32
/dev/sda2           6,152,895    78,236,549    72,083,655   f W95 Ext d (LBA)
/dev/sda5           6,152,958    42,202,754    36,049,797   b W95 FAT32
/dev/sda6          42,202,818    52,628,939    10,426,122   b W95 FAT32
/dev/sda7          52,629,003    68,501,159    15,872,157   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcda954fd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   161,099,819   161,099,757   7 HPFS/NTFS
/dev/sdb2         161,099,820   225,600,794    64,500,975   5 Extended
/dev/sdb5         161,099,883   202,065,569    40,965,687   7 HPFS/NTFS
/dev/sdb6         202,065,633   221,600,609    19,534,977  83 Linux
/dev/sdb7         221,600,673   225,600,794     4,000,122  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3D40-19FE                              vfat                                     
/dev/sda5        1AEB-3862                              vfat                                     
/dev/sda6        1AF0-3763                              vfat                                     
/dev/sda7        1AF4-1925                              vfat                                     
/dev/sdb1        6C7CF0197CEFDC38                       ntfs       New Volume                    
/dev/sdb5        CCDCFE1EDCFE028E                       ntfs                                     
/dev/sdb6        2f94dbf9-c9f8-483e-9085-b0ee36585ead   ext4                                     
/dev/sdb7        781725df-4094-4d4f-ac00-d97b4ac635a6   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ = "Unidentified operating system on drive C."

=========================== sdb6/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2f94dbf9-c9f8-483e-9085-b0ee36585ead

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

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro quiet splash
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        2f94dbf9-c9f8-483e-9085-b0ee36585ead
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 2f94dbf9-c9f8-483e-9085-b0ee36585ead
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3d40-19fe
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=2f94dbf9-c9f8-483e-9085-b0ee36585ead /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=781725df-4094-4d4f-ac00-d97b4ac635a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 103.8GB: boot/grub/core.img
 104.2GB: boot/grub/grub.cfg
 104.2GB: boot/grub/menu.lst
 104.4GB: boot/grub/stage2
 104.3GB: boot/initrd.img-2.6.31-14-generic
 105.6GB: boot/initrd.img-2.6.31-20-generic
 106.9GB: boot/initrd.img-2.6.31-21-generic
 105.8GB: boot/vmlinuz-2.6.31-14-generic
 106.2GB: boot/vmlinuz-2.6.31-20-generic
 105.7GB: boot/vmlinuz-2.6.31-21-generic
 106.9GB: initrd.img
 105.6GB: initrd.img.old
 105.7GB: vmlinuz
 106.2GB: vmlinuz.old

```

---

### Post by byStanderone on 2010-04-24
...am not sure if a sudo update-grub would correct your problem, but here is a thread, hope it helps:[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Charlotte18 on 2010-04-24
Recently, I had a problem with grub2 and followed these instructions which repaired the problem:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by mankidavu on 2010-04-25
Thanks for the replies.

I've tried the sudo update-grub and sudo *dpkg*-[I]reconfigure grub-pc commands.

There is absolutely no issues when we generate new grub.cfg or when we look the configuration files from ubuntu.

Only upon boot time, the grub menu have this "last character missing" issue.

Anyway,I'll wait till new updates of grub2. The one I tried was an experimental update from below PPA.
[https://launchpad.net/~fzielcke/+archive/grub-ppa](https://launchpad.net/~fzielcke/+archive/grub-ppa)
[I]

There is a work around for the slow grub loading issue, by changing the boot order in BIOS and updating grub on your corresponding boot drive.

But in that work around,somehow my windows 7 is not booting. (the entries looks fine.)
Otherwise grub loads fine and ubuntu boots perfectly.
[/I][/I]

---

### Post by mankidavu on 2010-05-15
Just an update.

This issue is gone in the new grub available with ubuntu 10

---

