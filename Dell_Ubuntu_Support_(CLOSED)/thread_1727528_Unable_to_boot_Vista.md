---
title: "Unable to boot Vista"
date: 2011-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Teegoo on 2011-04-12
Hey, I've been encountering a bit of a problem. When I select Vista from my grub 2 boot menu, it just goes to Dell Bios, and then to grub again. Is there any way to fix this?

---

### Post by sanguinoso on 2011-04-12
Is it the Dell bios or is it the Dell Recovery Console? Do you know how to verify that the entry in grub is pointing to the correct hard drive partition? You can get a command line in grub by hitting ctrl-C and then type ls to display your partitions.

---

### Post by Teegoo on 2011-04-12
My drive partitions are as follows:

```
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 463124184 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```

And it is indeed Dell BIOS. It boots before grub. When I select Linux, it boots fine, but when I select Vista (labeled as "windows recovery environment" or something in Grub), it just goes back to Dell BIOS and then to grub again.

---

### Post by Teegoo on 2011-04-13
I could really use some help here. I have absolutely no idea how to fix it, and I need to access my programs on Vista...

---

### Post by sanguinoso on 2011-04-15
When you're in grub, select vista and hit the 'e' key. This will show you what partition it is trying to boot for vista. It sounds like 'sda1' is selected when it should be 'sda3' or 'sda2'. If that doesn't work there is a suspicious error on 'sda2' I found a post [http://ubuntuforums.org/showthread.php?t=1484965](http://ubuntuforums.org/showthread.php?t=1484965) that has a solution for that problem.

---

### Post by Teegoo on 2011-04-17
Well, I hit "e" in he Grub 2 menu with vista selected, but I saw nothing in the following screen about which partition it is pointing to. However, in the initial menu, it says (/dev/sda3) beside it. However, it makes more sense that it would be pointing to sda1 because that's obviously where my BIOS is. sda3 is my vista OS partition. How do I change where it's pointing?

---

### Post by garvinrick4 on 2011-04-17
Show us your whole boot script you have grub installed in sda2 also, should only be in sda
Download this script to YOUR DESKTOP and then run the code I gave you
and it will put a RESULTS.txt on your desktop, post it here.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Teegoo on 2011-04-17
Here's the whole thing:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 463124184 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda3    *     20,561,920   445,804,288   425,242,369   7 HPFS/NTFS
/dev/sda4         445,804,542   488,394,751    42,590,210   f W95 Ext d (LBA)
/dev/sda5         483,155,968   488,394,751     5,238,784  dd Dell Media Direct
/dev/sda6         445,804,544   481,505,279    35,700,736  83 Linux
/dev/sda7         481,507,328   483,153,919     1,646,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0615                              vfat       DellUtility                   
/dev/sda2        AAB6D921B6D8EEB7                       ntfs       RECOVERY                      
/dev/sda3        2C6EDB496EDB0B0A                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        72CA-0838                              vfat       MEDIADIRECT                   
/dev/sda6        8cfc5c1b-130e-4a53-ac60-58b8e083b19a   ext4                                     
/dev/sda7        ced3dd1d-980a-49b9-9fd9-9df0dae25d60   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2c6edb496edb0b0a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72ca-0838
	drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ced3dd1d-980a-49b9-9fd9-9df0dae25d60 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 237.1GB: boot/grub/core.img
 233.2GB: boot/grub/grub.cfg
 230.0GB: boot/initrd.img-2.6.35-22-generic
 230.0GB: boot/initrd.img-2.6.35-28-generic
 237.4GB: boot/vmlinuz-2.6.35-22-generic
 237.4GB: boot/vmlinuz-2.6.35-28-generic
 230.0GB: initrd.img
 230.0GB: initrd.img.old
 237.4GB: vmlinuz
 237.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  bb aa b1 bb ab b1 bc ab  b2 bc ac b3 bd ad b3 be  |................|
00000010  ae b4 bf af b5 c1 b1 b7  c3 b2 b8 c4 b2 b8 c4 b2  |................|
00000020  b8 c5 b3 b8 c6 b4 b9 c8  b5 ba c9 b5 bc ca b5 bf  |................|
00000030  cd b6 c0 ce b7 c1 cf b8  c2 d0 ba c3 d1 bb c3 d2  |................|
00000040  bc c4 d2 be c5 d3 bf c7  d5 c1 c8 d6 c2 c8 d7 c3  |................|
00000050  c9 d8 c4 ca d9 c5 ca d9  c6 ca d9 c6 cc da c6 cf  |................|
00000060  da c7 d1 db ca d2 de cc  d3 e0 ce d4 e1 d0 d5 e2  |................|
00000070  d1 d4 e2 d2 d5 e4 d4 d7  e6 d6 d9 e8 d6 db ea d7  |................|
00000080  dc eb d7 dc eb d6 dc ec  d4 db ec d4 dd ec d4 e1  |................|
00000090  ed d6 e3 ef d7 e5 f0 d8  e5 f2 d8 e5 f2 d9 e6 f3  |................|
000000a0  da e7 f5 db e8 f6 dc e8  f6 dc e9 f7 dd e9 f9 dd  |................|
000000b0  ea fa de ea fa de eb fb  df eb fb e0 ec fb e2 ec  |................|
000000c0  fb e3 ed fb e3 ee fc e3  ee fc e3 ef fd e3 ef fd  |................|
000000d0  e4 f0 fd e4 f0 fd e5 f1  fd e6 f2 fd e7 f3 fd e7  |................|
000000e0  f3 fd e8 f3 fd e9 f3 fd  ea f3 fd ea f4 fd e9 f5  |................|
000000f0  fd e9 f6 fd ea f6 fd ea  f6 fd ea f6 fd eb f7 fd  |................|
00000100  eb f7 fd ec f8 fd ed f9  fd ed f9 fd ed f9 fd ed  |................|
00000110  f9 fd ee fa fd ee fa fd  ee fa fd ee fa fd ee fa  |................|
00000120  fd ee fa fd ee fb fd ed  fc fd ec fc fd ec fc fd  |................|
00000130  eb fd fd ea fd fd ea fd  fd ea fd fd eb fc fd ed  |................|
00000140  fc fd ee fc fd ee fc fd  ef fb fd ee fb fd ed fc  |................|
00000150  fd ec fc fd ec fc fd ec  fc fd ec fc fd ec fc fd  |................|
00000160  ec fc fd ec fc fd eb fb  fd eb fb fd eb fb fd eb  |................|
00000170  fb fd eb fb fd eb fb fd  eb fb fd ec fc fd ed fc  |................|
00000180  fd ee fd fd ee fd fd ee  fd fd ee fd fd ee fd fd  |................|
00000190  ee fd fd ee fd fd ee fd  fd ee fd fd ee fd fd ee  |................|
000001a0  fd fd ee fd fd ee fd fd  ee fd fd ed fd fd ec fd  |................|
000001b0  fd eb fd fd ec fd fd ec  fd fd ed fd fd ee 00 fe  |................|
000001c0  ff ff dd fe ff ff 02 f0  39 02 00 f0 4f 00 00 fe  |........9...O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c0 20 02 00 00  |............ ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by garvinrick4 on 2011-04-17
Take your Vista recovery Disk and:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
Then using your Ubuntu install CD choose Try Ubuntu and:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
These two links are fairly simple to use just copy and paste commands if need be.
#Get your windows vista to boot first and then reinstall grub2 second in other words.
Grub always go's into sda not sda1 or sda2 or sda3 just sda

---

### Post by sanguinoso on 2011-04-19
Is it working now? Mark the thread as solved if so.

---

### Post by oldfred on 2011-04-19
he needs the fixboot command in a windows disk or use testdisk to remove the grub install to the windows partition. Windows has to have its code in any windows NTFS/FAT partition.

sda2: ______
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda2[/COLOR] and 
                       looks at sector 463124184 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

sda3 which is flagged as the boot partition in windows looks ok, so it may boot that partition. But sda2 needs repair.

---

