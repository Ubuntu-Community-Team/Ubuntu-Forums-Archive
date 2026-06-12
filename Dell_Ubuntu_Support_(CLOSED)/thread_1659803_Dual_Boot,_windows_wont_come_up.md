---
title: "Dual Boot, windows wont come up"
date: 2011-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denton Larson on 2011-01-04
Hi Everybody

I hope you are well with 2011

I have a problem with my dual boot machine. The machine is a Dimension 4700 it has Windows XP and Ubuntu 10.04 LTS and it worked fine until this morning.
I tried to boot in to windows to get my scanner to work and this is what I saw.

error: no such device: 3e70ff7c70df397b.
error: invalid signature.
press any key to continue...

I got in to windows via the network tab in Places but it asked for a password and there isn't one.

I am at a loss as to what to do.
Anybody have a suggestion as to what to do?

Denton Larson

---

### Post by Denton Larson on 2011-01-05
Bump

---

### Post by Twicks on 2011-01-05
You have to restore Windows Master Boot Record.
[http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html](http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html)

---

### Post by wilee-nilee on 2011-01-05
> **Twicks said:**
> You have to restore Windows Master Boot Record.
[http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html](http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html)

Bad advice without knowing more, especially when a dual boot has been mentioned.

OP do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by Denton Larson on 2011-01-06
> **wilee-nilee said:**
> Bad advice without knowing more, especially when a dual boot has been mentioned.

OP do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Here is what I have

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   498,016,175   498,016,113   7 HPFS/NTFS
/dev/sda2         498,016,254   976,773,119   478,756,866   5 Extended
/dev/sda5         498,016,256   969,254,911   471,238,656  83 Linux
/dev/sda6         969,256,960   976,773,119     7,516,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.1 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders, total 19640880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         48,195    19,631,429    19,583,235   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   123,379,199   123,379,137   7 HPFS/NTFS
/dev/sdc2         123,379,200   156,296,384    32,917,185   5 Extended
/dev/sdc5         123,379,263   154,818,404    31,439,142  83 Linux
/dev/sdc6         154,818,468   156,296,384     1,477,917  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        10fd32ee-234c-4717-b282-420e6cd922e7   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a5f33bd9-2426-461c-9a86-17bb9bbd2762   ext4                                     
/dev/sda6        0860de46-153e-4ee3-a252-c257d3612141   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        820C30C90C30BA4D                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D0889C76889C5D32                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        d300eec1-1ab1-4f0b-be67-65fe2314527f   ext4                                     
/dev/sdc6        9fade630-88f4-4e91-a113-a2fe33054725   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc5        /media/d300eec1-1ab1-4f0b-be67-65fe2314527f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/D0889C76889C5D32  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/820C30C90C30BA4D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=a5f33bd9-2426-461c-9a86-17bb9bbd2762 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=a5f33bd9-2426-461c-9a86-17bb9bbd2762 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=a5f33bd9-2426-461c-9a86-17bb9bbd2762 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=a5f33bd9-2426-461c-9a86-17bb9bbd2762 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a5f33bd9-2426-461c-9a86-17bb9bbd2762
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e70df7c70df397b
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (on /dev/sdd5)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro quiet splash
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode) (on /dev/sdd5)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro single
	initrd /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=a5f33bd9-2426-461c-9a86-17bb9bbd2762 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0860de46-153e-4ee3-a252-c257d3612141 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 310.9GB: boot/grub/core.img
 411.3GB: boot/grub/grub.cfg
 311.1GB: boot/initrd.img-2.6.32-26-generic
 311.0GB: boot/initrd.img-2.6.32-27-generic
 311.1GB: boot/vmlinuz-2.6.32-26-generic
 311.1GB: boot/vmlinuz-2.6.32-27-generic
 311.0GB: initrd.img
 311.1GB: initrd.img.old
 311.1GB: vmlinuz
 311.1GB: vmlinuz.old

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root=(hd2,5)
search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
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
set root=(hd2,5)
search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	echo	Loading Linux 2.6.32-14-generic ...
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set d300eec1-1ab1-4f0b-be67-65fe2314527f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro quiet splash
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/vmlinuz-2.6.24-16-generic root=UUID=052dece9-8425-4e00-b92a-acb4eb204729 ro single
	initrd /boot/initrd.img-2.6.24-16-generic
}
menuentry "Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 052dece9-8425-4e00-b92a-acb4eb204729
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro quiet splash
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-14-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro single
	initrd /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-13-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro quiet splash
	initrd /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 99ad5dce-3363-49d2-bfcf-d46784bc966d
	linux /boot/vmlinuz-2.6.32-13-generic root=UUID=99ad5dce-3363-49d2-bfcf-d46784bc966d ro single
	initrd /boot/initrd.img-2.6.32-13-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=d300eec1-1ab1-4f0b-be67-65fe2314527f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=9fade630-88f4-4e91-a113-a2fe33054725 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  65.6GB: boot/grub/core.img
  77.1GB: boot/grub/grub.cfg
  64.0GB: boot/initrd.img-2.6.32-14-generic
  65.6GB: boot/vmlinuz-2.6.32-14-generic
  64.0GB: initrd.img
  65.6GB: vmlinuz

```
Denton Larson

---

### Post by wilee-nilee on 2011-01-06
You are missing stuff to say the least, but sometimes the script doesn't read everything. Do you have a XP cd?

---

### Post by Denton Larson on 2011-01-06
Yes I have a windows XP cd on hand

---

### Post by wilee-nilee on 2011-01-06
> **Denton Larson said:**
> Yes I have a windows XP cd on hand

Good to know, the problem besides some stuff missing, like the regular boot files for XP, the script shows sda1 as a ext3 and a ntfs partition.

**sda1:** _________________________________________________________________________

    File system:      ** ext3**
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

**/dev/sda1**    *             63   498,016,175   498,016,113   7 **HPFS/NTFS**

There is this in the grub.cfg in the sda5 boot as well
BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on **/dev/sda1**)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e70df7c70df397b
	drivemap -s (hd0) ${root}
	chainloader +1

I think you will need some more experienced help here.

Do you have backups of the important information in case you have to just reinstall, I ask this so that just more information is available. Basically you have a fairly haphazard setup here, consequently leading to the problems, may be fixable may be not. Do you have the activation key for a new install of XP?

What your going to have to do here is identify what you have installed and where it is with partition information.

You have XP listed in sdc1 as well, and two versions of Lucid.

---

### Post by Denton Larson on 2011-01-07
Hoh boy, I might have to reformat my hard drive that is a bummer!

thanks for looking

Denton

---

