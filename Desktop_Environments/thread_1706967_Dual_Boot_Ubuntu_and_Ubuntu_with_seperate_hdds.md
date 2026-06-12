---
title: "Dual Boot Ubuntu and Ubuntu with seperate hdds"
date: 2011-03-14
forum: Desktop Environments
---

### Post by gongdiddle on 2011-03-14
I recently performed a fresh 10.04 install on a new hard drive I installed in my tower alongside the old. Fresh install works great and I can access all the data on my older drive, but when I try to boot from the old drive through the BIOS boot menu, I get a grub menu, and any of my choices (I've tried 3 of about 6 kernal listings) load the new install, with it's new machine name at the login screen.

Can anyone tell me how I might be able to boot to the old OS on the old drive?

For the most part I'm set with being able to access the data, but I would like to perform some .sql exports with phpmyadmin. So I'd also be interested if there is a way to point my new install's phpmyadmin to the mysql data on the old drive.

Thank you for any consideration.

---

### Post by oldfred on 2011-03-14
Grub from the new install probably installed to the MBR of the old drive. Did you do a sudo update-grub. It should also find the old install and let you boot it.

I prefer to keep the boot loader of each drive's install in that drive's MBR. If using IDE/PATA you may only be able to boot from the primary master (sda), but with SATA you can boot any drive.

To see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by gongdiddle on 2011-03-15
You may be right, and I would certainly "prefer to keep the boot loader of each drive's install in that drive's MBR" as well, but I'm still not sure how to confirm that in the future. I spose I could have disconnected the other drive before install?

I ran sudo update-grub and it listed the drive, but I still cannot boot to it. Then I performed that nifty script you linked and as far as I can tell, it confirms your diagnosis. Can't say I know how to proceed though, sounds like I may have overwritten some or all of the previouse MBR? The output of the script was pretty long, but I'll post it following as advised. Please let me know if you find any recourse.

Thank you

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,906,104,319 1,906,102,272  83 Linux
/dev/sda2       1,906,106,366 1,953,523,711    47,417,346   5 Extended
/dev/sda5       1,906,106,368 1,953,523,711    47,417,344  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,859,609,599 3,859,605,504 Linux or Data
/dev/sdb3   3,859,609,600 3,907,028,991    47,419,392 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3664677d-ede9-40dd-8e44-a659af1578f7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f286a20f-7e17-447d-b130-3a08a2212a96   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf   ext4                                     
/dev/sdb3        c01a4734-f408-4646-9771-33a4180c389c   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
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
search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
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

=============================== sda1/etc/fstab: ===============================

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
UUID=f286a20f-7e17-447d-b130-3a08a2212a96 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 968.6GB: boot/grub/core.img
 818.7GB: boot/grub/grub.cfg
 968.6GB: boot/initrd.img-2.6.32-21-generic
 968.7GB: boot/initrd.img-2.6.32-22-generic
 968.7GB: boot/initrd.img-2.6.32-23-generic
 968.8GB: boot/initrd.img-2.6.32-24-generic
 968.8GB: boot/initrd.img-2.6.32-25-generic
 968.8GB: boot/initrd.img-2.6.32-26-generic
 968.8GB: boot/initrd.img-2.6.32-29-generic
 968.6GB: boot/vmlinuz-2.6.32-21-generic
 256.0GB: boot/vmlinuz-2.6.32-22-generic
 712.5GB: boot/vmlinuz-2.6.32-23-generic
 968.8GB: boot/vmlinuz-2.6.32-24-generic
 771.6GB: boot/vmlinuz-2.6.32-25-generic
 968.8GB: boot/vmlinuz-2.6.32-26-generic
 968.8GB: boot/vmlinuz-2.6.32-29-generic
 968.8GB: initrd.img
 968.8GB: initrd.img.old
 968.8GB: vmlinuz
 968.8GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3664677d-ede9-40dd-8e44-a659af1578f7
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3664677d-ede9-40dd-8e44-a659af1578f7 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=0da2dbd6-aee4-4239-a7c1-3f0c3c68f3bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=c01a4734-f408-4646-9771-33a4180c389c none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 257.8GB: boot/grub/core.img
 257.8GB: boot/grub/grub.cfg
 257.8GB: boot/initrd.img-2.6.32-28-generic
 257.9GB: boot/initrd.img-2.6.32-29-generic
 257.8GB: boot/vmlinuz-2.6.32-28-generic
 257.8GB: boot/vmlinuz-2.6.32-29-generic
 257.9GB: initrd.img
 257.8GB: initrd.img.old
 257.8GB: vmlinuz
 257.8GB: vmlinuz.old
```

---

### Post by oldfred on 2011-03-15
Either the script or grub report the incorrect (same drive) info when it is not. Your grub in sda has to be booting sdb2.

I would install grub to sdb. If BIOS lets you choose boot drive then try booting from sdb, it not at least if you ever unplug sda, then you can boot from sdb.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

If BIOS lets you boot from sdb:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by gongdiddle on 2011-03-17
Well I'm a little lost but here's what I figure. I can succesfully boot to sdb no problem, and I believe my grub in sda is booting to sdb. I'm trying to boot to the old install on sda through the BIOS (is that the proper protocol? do other people use software like grub to choose in dual boot system?), but it seems that boot process was overwritten when I installed to sdb, and as such choosing that drive (sda) in the BIOS eventually boots to the 'new' OS on sdb. I ran the commands you listed previously and it looked like they properly installed grub to sdb, but I am still unable to boot to the 'old' OS on sda. Perhaps I should perform a live cd boot and run similiar commands to reinstall/configure grub on sda? I'm in a bit over my head and I apreciate all your help, apologies if I've misunderstood the process or misrepresented the problem.

I've put the terminal out put from the sequence of commands below.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000186c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      118650   953051136   83  Linux
/dev/sda2          118650      121602    23708673    5  Extended
/dev/sda5          118650      121602    23708672   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT
telmehuse@hal200:~$ man fdisk
telmehuse@hal200:~$ sudo grub-install /dev/sdb
[sudo] password for telmehuse: 
Installation finished. No error reported.
telmehuse@hal200:~$ sudo dpkg-reconfigure grub-pc
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda1
done
telmehuse@hal200:~$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA3890395
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10
```

---

### Post by srs5694 on 2011-03-17
I normally use one GRUB installation to select OSes on multiple hard disks. This is (IMHO) much simpler than using the BIOS to select the boot drive. Following this model, you could add GRUB entries for your /dev/sda installation to the GRUB files on /dev/sdb. If the update-grub utility doesn't detect your /dev/sda installation, then you can create manual entries by editing /etc/grub.d/40-custom and then running update-grub again. (If your /dev/sda installation uses GRUB2, chances are you can just cut-and-paste its entries from its /boot/grub/grub.cfg file to /etc/grub.d/40-custom on the other installation. Note those references is each relative to *its own* root!)

Also and FWIW, you've got one Master Boot Record (MBR) disk and one GUID Partition Table (GPT) disk. There's nothing wrong with this (I've got a couple of systems like that myself), but you should be aware of it. The fdisk utility was meant to work on MBR (and some other more obscure) disks, not on GPT disks. That's why it presents that warning and shows only one disk-spanning partition on your /dev/sdb. To view or work on your /dev/sdb partitions, you should use a GPT-aware utility, such as GPT fdisk (gdisk), GNU Parted, or GParted.

---

### Post by oldfred on 2011-03-17
It says it found the install from your post.

```

Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda1
```

srs5694 is very knowledgeable gpt disks, I am surprised he did not add that with gpt & grub2 you should add another tiny grub_bios partition.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

---

### Post by srs5694 on 2011-03-17
> **oldfred said:**
> It says it found the install from your post.

```

Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda1
```srs5694 is very knowledgeable gpt disks, I am surprised he did not add that with gpt & grub2 you should add another tiny grub_bios partition.

I didn't mention it because he's already got one, according to the Boot Info Script output.

---

### Post by oldfred on 2011-03-17
@srs5694 you are correct. Somehow I missed that. But that is why I like to have many eyes reviewing the boot script as it puts out so much info is sometimes is easy to miss something.

I am not sure sure if it was 10.04 or 9.10 where you had to add a parameter to get mixed gpt & msdos partitions to work. Newest version of Ubuntu recognizes both without issue. Update -it was Lucid -10.04.

You may need to add this parameter to /etc/default/grub in your gpt install.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by gongdiddle on 2011-03-29
Thanks for the heads up srs5694, I've learned a bit about the difference of GPT and MBR now, and I spose I'll try to keep all my drives GPT from here on out. Seems like the paradigm is shifting currently, any thoughts?

I've also been reading up on grub2, and it's a bit passed me. I like the idea of grub menu vs BIOS and it does seem a bit more elegant, but I get the impression that using grub in that capacity requires boot information for multiple drives be located on one, and I would rather the boot info be kept on the same drive as the OS. I guess kind of arbitrarilly, I'm no expert.

I mentioned I have access to all the data of the old drive so I don't really need to boot into it, though I had wanted to so I could perform a big sql dump and subsequent import through phpmyadmin. I found the mysql data located at /var/lib/mysql. I used gksudo nautilus to move this data to the new drive and switched back to the CLI to change the ownership and group of the files to mysql. I don't have good luck with recursive file permissions from the GUI. Looks like my tables are go.

Thanks for the consideration, in the future I think I'll be sure to unplug old drives during the live CD installs to avoid future grub mixups, I can't seem to fix this problem after the fact.

---

### Post by srs5694 on 2011-03-29
> **gongdiddle said:**
> Thanks for the heads up srs5694, I've learned a bit about the difference of GPT and MBR now, and I spose I'll try to keep all my drives GPT from here on out. Seems like the paradigm is shifting currently, any thoughts?

There is a shift underway from MBR to GPT. As usual, Apple is ahead of the curve on this one, but indications are that things will begin to shift more significantly for new commodity PCs this year and next.

FWIW, I've written about this before. See [my article on GPT on IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) and my ["What's a GPT?" page](http://www.rodsbooks.com/gdisk/whatsgpt.html) (part of my GPT fdisk documentation).

> I've also been reading up on grub2, and it's a bit passed me. I like the idea of grub menu vs BIOS and it does seem a bit more elegant, but I get the impression that using grub in that capacity requires boot information for multiple drives be located on one, and I would rather the boot info be kept on the same drive as the OS. I guess kind of arbitrarilly, I'm no expert.

The trouble is that the BIOS is inflexible in its boot options. When the PC was designed, little thought was given to the possibility of having multiple OSes available, and we're still living with that lack of vision. Thus, you must either use the awkward "press F12 to select the boot drive" (or similar) workaround at boot time (which just selects which physical disk to boot, not which OS on that disk) or you must have a boot loader (stored on one disk and one partition on the disk) with knowledge of all the OSes.

It's possible to keep the boot loader on its own partition, independent of any OS. It will still reside on one physical disk, though. (It's not clear whether by "multiple drives" you mean multiple physical disks or multiple partitions.) With the upcoming shift from BIOS to EFI, things will change, too. EFI includes its own boot loader, but it still requires boot information to be stored on the disk. The difference is that this boot information typically goes in a partition dedicated to the EFI rather than to any one OS. There's a GRUB 2 version for EFI, as well as some other EFI boot loaders that work after the EFI's own rudimentary boot loader.

---

### Post by gongdiddle on 2011-03-30
Wow, in hindsight "any thoughts" is laughable. Those articles were incredibly thorough. It was nice to learn a bit more about the grub/grub2/efi relationship as well. Unfortunatly, thats all new to me. Indeed, I didn't read up on grub2 until it was mentioned previously in this post, but I look forward to learning about future developments with a bit more context to draw upon. Thanks for sharing.

Time for me to put 'Dark City' on the box it's been a while and that is an amazing piece.

---

