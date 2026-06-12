---
title: "Fixing/Replacing bootloader files"
date: 2011-05-26
forum: Desktop Environments
---

### Post by JadeMoonlight on 2011-05-26
[FONT="Arial"]
Hello everyone,

I apologize in advance for the lengthy post. Any help you can offer is greatly appreciated. I am also happy to provide additional information.

To my best knowledge, I am having problems with either my boot list (/boot/grub/grub.cfg) or my Master Boot Record. It is possible that something else in this area is causing the problem, however.

Configuration overview:
Machine:	Sony Vaio VGN-NS140E laptop
Systems: 	Dual-booting Vista and Ubuntu
Partitions:	Vista Recovery (NTFS)
		Vista OS 
		Data Files (for sharing between Vista and Ubuntu partitions)
		Extended with:
			Ubuntu 10.04.2 LTS
			Ubuntu 11.04
			Swap
Vista is 32-bit
Ubuntu is 64-bit
				
Below is some information on how I believe I created this problem and an overview of steps I took while trying to fix the problem.

Several days ago, I ran GParted off of an Ubuntu Natty Narwhal (11.04) LiveUSB to remove an older, broken linux partition containing either the Maverick Meerkat (10.10) or the Lucid Lynx (10.04) release. That partition had been my original linux partition for this machine. For reference, the partition originally had Intrepid Ibex (8.10) installed. I was unable to load it properly after downgrading from Maverick Meerkat to Lucid Lynx. Maverick had some glaring functionality issues with my laptop model.

I needed to remove the partition in a Live session because it was located within an extended partition alongside my currently used Ubuntu partition.

After deleting this partition and rebooting the laptop, it was either the Grub Loader menu or a grub-rescue prompt that appeared. I'm pretty sure that it was the [FONT="Courier New"]grub-rescue[/FONT] prompt at this point. Unable to move forward from this prompt, I turned off the computer and re-inserted my USB drive to boot into a Live session again. Booting into a Live session worked successfully.

At this point I was able to browse the web for possible solutions. I read somewhere that I should run [FONT="Courier New"]sudo update-grub[/FONT] from the terminal. After doing this and rebooting the computer, I was taken to the Grub Loader menu. Unfortunately, all of the entries I tried to boot from brought me to the grub-rescue prompt. There were 3 error lines above the prompt, but I don't remember all of them at the moment. I know that one of them did say "[FONT="Courier New"]Error: You need to load the kernel first.[/FONT]"

At the time, I was hoping this could be a fairly easy fix. I had the idea to simply create a new Ubuntu partition where the old one had been. I installed Natty Narwhal to a new partition within my extended partition. When I restarted my computer after the install had been completed, I did not have the results I'd expected or hoped for. The [FONT="Courier New"]grub-rescue[/FONT] prompt still came up when I attempted to boot into any of the entries listed in the Grub Loader. Also, the new install I had created was not available in the list.

I tried to get information from various commands in either the grub or grub-rescue prompt. Somehow, I was able to determine the kernel name I needed and edited the boot command (the screen accessed when you press 'e' on the Grub Loader) to include it. This was no help at the time.

I again restarted the computer and booted into a Live session. I re-installed Natty Narwhal on top of the install I just created, thinking that there may have been a problem with it. After restarting the computer, I was still having the same problems as with the first installation attempt. I ran another Live session.

By looking at other user's Boot Info Script RESULTS.txt files on this forum and following some links, I was able to gain a better understanding of the Grub boot command. With this information and some more experimentation in the [FONT="Courier New"]grub-rescue[/FONT] prompt, I was able to determine the UUID of my Natty Narwhal partition, edit the boot command mentioned two paragraphs ago, and boot into Ubuntu with only one error. 

In this new Ubuntu installation, I ran [FONT="Courier New"]sudo update-grub[/FONT] in the terminal. The command returned entries that matched with those I saw in GParted, but I still had the same problems and incorrect entries when I restarted the computer.

While it is possible that I could determine all of the necessary start-up boot commands to manually enter each of my bootable partitions, this is really rather inconvenient. I want to know how I can permanently fix the Grub or other necessary files so that my bootloader can take back responsibility for this task. It would also be nice to get back into my Lucid Lynx partition because Natty is a bit buggier than I'm okay with. Fixing my problems with Natty is a topic for another post, however.

I am attaching RESULTS.txt from Boot Info Script. Please let me know if you need any other reports of this nature.[/FONT]

```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
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

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 461407720 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    18,782,207    18,780,160  27 Hidden NTFS (Recovery Environment)
/dev/sda2          18,782,208   123,639,807   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda3         166,385,205   292,206,284   125,821,080   7 NTFS / exFAT / HPFS
/dev/sda4         292,206,590   488,392,064   196,185,475   5 Extended
/dev/sda5         482,094,648   488,392,064     6,297,417  82 Linux swap / Solaris
/dev/sda6    *    292,206,592   377,237,503    85,030,912  83 Linux
/dev/sda7         377,239,552   482,093,055   104,853,504  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F8EE666BEE6621DC                       ntfs       Recovery
/dev/sda2        C452D9DD52D9D470                       ntfs       Vista OS
/dev/sda3        80FA0C3BFA0C2FC8                       ntfs       Data Files
/dev/sda5        1453748c-adaf-4e18-b468-41e847d0705e   swap       
/dev/sda6        62f3010c-d5c0-4aad-ad78-a23494d36f85   ext4       
/dev/sda7        35c96824-9b36-4def-b0cb-34841506a146   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /mnt/DataFiles           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /mnt/LucidLynx           ext4       (rw,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8ee666bee6621dc
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c452d9dd52d9d470
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.27-11-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu, with Linux 2.6.27-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7d90875a-a89f-4c4f-9226-cbdc3cd2a84c
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7d90875a-a89f-4c4f-9226-cbdc3cd2a84c ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
# / was on /dev/sda7 during installation
UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=60f1f2c9-1431-41cc-8368-2c6f05e8d0a1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 143.695178986 = 154.291523584  boot/grub/core.img                             1
 168.584175110 = 181.015879680  boot/grub/grub.cfg                             2
 143.603382111 = 154.192957440  boot/grub/stage2                               1
 143.735404968 = 154.334715904  boot/initrd.img-2.6.32-24-generic              1
 144.097145081 = 154.723131392  boot/initrd.img-2.6.32-28-generic              1
 144.184417725 = 154.816839680  boot/initrd.img-2.6.32-29-generic              1
 168.872993469 = 181.325996032  boot/initrd.img-2.6.32-30-generic              2
 140.596412659 = 150.964248576  boot/initrd.img-2.6.32-31-generic              2
 143.717079163 = 154.315038720  boot/vmlinuz-2.6.32-24-generic                 1
 143.722866058 = 154.321252352  boot/vmlinuz-2.6.32-28-generic                 1
 144.037956238 = 154.659577856  boot/vmlinuz-2.6.32-29-generic                 1
 144.276241302 = 154.915434496  boot/vmlinuz-2.6.32-30-generic                 1
 143.877803802 = 154.487615488  boot/vmlinuz-2.6.32-31-generic                 1
 140.596412659 = 150.964248576  initrd.img                                     2
 168.872993469 = 181.325996032  initrd.img.old                                 2
 143.877803802 = 154.487615488  vmlinuz                                        1
 144.276241302 = 154.915434496  vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
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
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=35c96824-9b36-4def-b0cb-34841506a146 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=35c96824-9b36-4def-b0cb-34841506a146 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 35c96824-9b36-4def-b0cb-34841506a146
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root F8EE666BEE6621DC
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root C452D9DD52D9D470
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro quiet splash
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 62f3010c-d5c0-4aad-ad78-a23494d36f85
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=62f3010c-d5c0-4aad-ad78-a23494d36f85 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=35c96824-9b36-4def-b0cb-34841506a146 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1453748c-adaf-4e18-b468-41e847d0705e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 220.016372681 = 236.240781312  boot/grub/core.img                             1
 206.115001678 = 221.314297856  boot/grub/grub.cfg                             1
 181.136260986 = 194.493579264  boot/initrd.img-2.6.38-8-generic               2
 220.014652252 = 236.238934016  boot/vmlinuz-2.6.38-8-generic                  1
 181.136260986 = 194.493579264  initrd.img                                     2
 220.014652252 = 236.238934016  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  6b 04 72 6f d8 a6 45 7f  c2 10 c4 2a 01 88 68 0a  |k.ro..E....*..h.|
00000010  68 a0 8d 5d 64 c3 35 32  26 d4 56 eb 1d 39 9b cd  |h..]d.52&.V..9..|
00000020  63 fd 99 ac 98 47 34 98  46 11 a5 81 92 99 2b 0d  |c....G4.F.....+.|
00000030  cd 78 16 50 b1 09 15 86  54 e0 70 66 b1 65 67 e5  |.x.P....T.pf.eg.|
00000040  8f fe cc 3d 22 04 4b 1c  23 7c c7 19 23 c6 3e 1b  |...=".K.#|..#.>.|
00000050  43 1a c7 46 b8 d6 12 81  8d 0c 5d e9 2f 8f 10 61  |C..F......]./..a|
00000060  a4 36 ba 4e 11 48 8a 46  d3 63 0a 35 86 87 d4 c6  |.6.N.H.F.c.5....|
00000070  d8 db 69 85 19 1d 29 cf  10 ba 9b cf 05 63 a1 ff  |..i...)......c..|
00000080  00 23 b8 44 48 91 eb fc  00 8e e1 11 22 47 ab f2  |.#.DH......."G..|
00000090  bb c6 ad 7a 3e 02 00 47  ab 2a b4 ad 7b ea cd 5a  |...z>..G.*..{..Z|
000000a0  5f 8b 37 1f 25 2e 55 4b  f4 39 db 41 e6 ef c9 e3  |_.7.%.UK.9.A....|
000000b0  e0 52 f5 2b fe f6 39 cb  38 3d d5 d6 66 39 57 9b  |.R.+..9.8=..f9W.|
000000c0  7d be 59 71 8d d6 21 a4  66 2b 92 d8 54 7c 89 6c  |}.Yq..!.f+..T|.l|
000000d0  69 4b 86 f8 55 d0 3b ea  c6 4d 4c 63 1a bb 3a 8d  |iK..U.;..MLc..:.|
000000e0  df b2 33 0e 69 65 f6 0e  3e 63 df 58 98 cb 19 25  |..3.ie..>c.X...%|
000000f0  48 89 56 e5 6f 68 2c 17  95 18 71 79 88 c6 58 af  |H.V.oh,...qy..X.|
00000100  00 38 ac ab 2d 86 36 48  d2 88 0d 48 cb 16 ec 81  |.8..-.6H...H....|
00000110  a0 eb 02 05 82 62 a8 26  12 3b 58 68 54 60 26 04  |.....b.&.;XhT`&.|
00000120  61 0d 2c 4c be 0e a2 40  a4 27 40 68 d8 43 2a e1  |a.,L...@.'@h.C*.|
00000130  a5 06 aa 12 62 ab 09 65  20 ca 40 35 5e f2 b4 8f  |....b..e .@5^...|
00000140  4b 07 d1 20 61 87 f7 8c  cf 0e a6 ce 27 8a 47 70  |K.. a.......'.Gp|
00000150  4c 34 9d 0d d1 9e 43 5c  32 40 7e f0 d3 a7 59 0c  |L4....C\2@~...Y.|
00000160  11 51 50 8b 57 51 02 22  b9 b4 64 c9 81 6a 64 c3  |.QP.WQ."..d..jd.|
00000170  53 2a 02 9a 29 93 26 c0  de 21 fe 3a 24 44 1a 90  |S*..).&..!.:$D..|
00000180  32 a0 1d 1a 12 68 22 27  29 7e 4a 1d 1c 03 ce b8  |2....h"')~J.....|
00000190  49 a7 04 76 91 10 bc b8  05 30 0d a6 84 22 09 11  |I..v.....0..."..|
000001a0  05 62 26 06 58 50 e4 70  91 08 e0 44 04 26 52 8d  |.b&.XP.p...D.&R.|
000001b0  49 b8 21 a5 91 40 44 22  82 80 f2 3c 88 92 00 fe  |I.!..@D"...<....|
000001c0  ff ff 82 fe ff ff 3a 76  51 0b 49 17 60 00 00 fe  |......:vQ.I.`...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 78 11 05 00 00  |...........x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by JadeMoonlight on 2011-05-26
Reposted in General Help forum at [http://ubuntuforums.org/showthread.php?t=1767679]("http://ubuntuforums.org/showthread.php?t=1767679")

---

