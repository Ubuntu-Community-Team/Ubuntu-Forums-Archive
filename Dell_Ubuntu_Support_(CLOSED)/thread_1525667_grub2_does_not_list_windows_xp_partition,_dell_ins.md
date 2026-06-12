---
title: "grub2 does not list windows xp partition, dell inspiron 6000"
date: 2010-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by patelv87 on 2010-07-07
Hi all,

I am using a Dell Inspiron 6000 computer.

My computer came with Windows XP Home installed on it and I installed Ubuntu 10.04 using the 'side-by-side' partitioning option. (I tried to use the CTRL+F11 dell pc restore but I think it has stopped working since I messed with the windows partition)

Within the past few days, I recall doing a Ubuntu update and quite possibly a windows update aswell.

Now, I cannot boot into windows, grub 2 does not show the windows partition in the list.

I attempted to find a similar scenario and tried the sudo update-grub2 command in the terminal.

In case it is of any help, it is pasted below.

sudpriya@priya-laptop:~$ sudo update-grub2
[sudo] password for priya: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
done
priya@priya-laptop:~$ 

I would greatly appreciate if anyone could shed some light on this situation, I have backed up all of my data and would like to have the Windows XP Home as either the only os or side-by-side with Ubuntu.

Unfortunately, I have a legitimate windows xp key but no CD.

Thanks, :)
Vinay

---

### Post by mikewhatever on 2010-07-07
Actually, the output you posted says it's found a dell partition. Have you tried booting that? Why don't you post the output of ** sudo fdisk -l** to see what other partitions are there.

---

### Post by garvinrick4 on 2010-07-07
Usually Dell has its own recovery partition on sda1 and Windows on sda2, the 

```
sudo fdisk -l
```  (small L)

and post here like previous post asks for. 

It will let us see where the Windows install is.

---

### Post by patelv87 on 2010-07-07
Thanks for the replies!

I tried the command in the terminal and I got the info below.

priya@priya-laptop:~$ sudo fdisk -l
[sudo] password for priya: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        5910    47402976+   7  HPFS/NTFS
/dev/sda3            9338        9729     3148740   db  CP/M / CTOS / ...
/dev/sda4            5910        9337    27531265    5  Extended
/dev/sda5            5910        9190    26348544   83  Linux
/dev/sda6            9190        9337     1181696   82  Linux swap / Solaris

Partition table entries are not in disk order



---


As for the dell utility partition, I attempted to boot from there but I was only prompted with a series of tests. 

It kind of looked like this...

Express Test - will run a quick test of devices in the system. This typically can take 10-20 minutes.
Extended Test - performs a thorough check of devices in the system. This typically can take an hour or more.
Custom Test - used to test a specific device or customize the tests to be run.Exit to MS-DOS will exit the diagnostics to a command prompt.
Symptom Tree. - This option lists the most common symptoms and allows you to select tests based on those symptoms.

Thank you for the quick replies!:D

Vinay

---

### Post by techunit on 2010-07-07
HI have you try this

```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-07-07
The boot menu does not show the sda2 that is in fdisk -l or Windows install.
Run this which is a info script on your boot in a text file. When you post it to this
thread copy and paste then highlight it all then click the # sign then hit submit reply button. This will allow
us to see what is happening in your boot and fix it. At least we know it is still there.
Down load it to your desktop and use this in terminal and the file will be on your desktop.

 sudo bash ~/Desktop/boot_info_script*.sh 

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by patelv87 on 2010-07-08
> **garvinrick4 said:**
> The boot menu does not show the sda2 that is in fdisk -l or Windows install.
Run this which is a info script on your boot in a text file. When you post it to this
thread copy and paste then highlight it all then click the # sign then hit submit reply button. This will allow
us to see what is happening in your boot and fix it. At least we know it is still there.
Down load it to your desktop and use this in terminal and the file will be on your desktop.

 sudo bash ~/Desktop/boot_info_script*.sh 

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

Its nice to know that the Windows partition is still there, I've pasted the boot info script output below.

Thanks for your help! :)
Vinay

```


sudo bash ~/Desktop/boot_info_script*.sh                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        128,520    94,934,472    94,805,953   7 HPFS/NTFS
/dev/sda3         149,998,905   156,296,384     6,297,480  db CP/M / CTOS / ...
/dev/sda4          94,935,038   149,997,567    55,062,530   5 Extended
/dev/sda5          94,935,040   147,632,127    52,697,088  83 Linux
/dev/sda6         147,634,176   149,997,567     2,363,392  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D5-0901                              vfat       DellUtility                   
/dev/sda2        C244F29A44F29081                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        49f0325b-5055-41c4-8060-8154a9706f7d   ext4                                     
/dev/sda6        310b3002-160c-47a6-9ac7-bf18c4839170   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4280-A106                              vfat       WD Passport                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/C244F29A44F29081  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/WD Passport       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
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
search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=49f0325b-5055-41c4-8060-8154a9706f7d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49f0325b-5055-41c4-8060-8154a9706f7d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d5-0901
	drivemap -s (hd0) ${root}
	chainloader +1
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
UUID=49f0325b-5055-41c4-8060-8154a9706f7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=310b3002-160c-47a6-9ac7-bf18c4839170 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  50.9GB: boot/grub/core.img
  51.0GB: boot/grub/grub.cfg
  50.9GB: boot/initrd.img-2.6.32-21-generic
  51.0GB: boot/initrd.img-2.6.32-22-generic
  52.4GB: boot/initrd.img-2.6.32-23-generic
  50.8GB: boot/vmlinuz-2.6.32-21-generic
  51.0GB: boot/vmlinuz-2.6.32-22-generic
  52.3GB: boot/vmlinuz-2.6.32-23-generic
  52.4GB: initrd.img
  51.0GB: initrd.img.old
  52.3GB: vmlinuz
  51.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  51 60 70 03 ff 49 30 d2  70 10 9f 31 10 31 00 20  |Q`p..I0.p..1.1. |
00000010  1d 22 00 f1 05 88 2e 7f  58 4f 31 02 f1 49 41 02  |."......XO1..IA.|
00000020  7f 58 ff ff f1 57 08 d3  30 10 71 00 30 11 7b 58  |.X...W..0.q.0.{X|
00000030  30 f0 04 73 0b fe 08 7f  49 7f 49 7f 49 14 01 7f  |0..s....I.I.I...|
00000040  49 80 1d 80 09 fb 71 83  71 07 18 70 06 7f 0e 7f  |I.....q.q..p....|
00000050  0e 31 0c f1 08 ee 08 f0  02 7d 38 75 0e 72 30 32  |.1.......}8u.r02|
00000060  7f 58 7b 58 6c 20 10 f5  36 7b 58 20 70 10 f3 0e  |.X{Xl ..6{X p...|
00000070  68 7e 65 7f 67 7f db 73  0d 7f 58 ff 0e f3 0e 63  |h~e.g..s..X....c|
00000080  b7 f0 46 71 05 7d 58 e8  ff 1c 72 58 a8 70 0a 1f  |..Fq.}X...rX.p..|
00000090  7d 0e 31 1c f1 1c 71 8f  7f 92 03 00 a8 db 30 23  |}.1...q.......0#|
000000a0  71 58 90 30 12 71 58 78  30 0d 72 58 2e 33 b0 9f  |qX.0.qXx0.rX.3..|
000000b0  30 00 f1 16 d8 70 1e e0  b8 00 68 62 69 6e 00 30  |0....p....hbin.0|
000000c0  a1 00 08 00 10 00 12 00  88 ff ff ff 00 6e 6b 20  |.............nk |
000000d0  00 aa cd 4b 4a 10 83 17  c9 01 01 90 30 1f 2c 84  |...KJ.......0.,.|
000000e0  00 02 04 b4 18 32 a1 00  00 44 82 ff 01 30 e8 ff  |.....2...D...0..|
000000f0  a0 00 e0 00 10 aa 98 00  9e 20 00 3e 0c 04 46 1e  |......... .>..F.|
00000100  00 0e 00 4c 6f 63 61 26  00 0c 00 00 7b 31 35 30  |...Loca&....{150|
00000110  45 32 37 32 00 33 2d 30  34 44 42 2d 34 00 45 36  |E272.3-04DB-4.E6|
00000120  44 2d 38 39 38 39 00 2d  35 39 35 31 34 44 46 00  |D-8989.-59514DF.|
00000130  36 33 33 39 42 7d 44 69  02 f0 00 54 52 00 45 00  |6339B}Di...TR.E.|
00000140  47 00 80 5f 00 53 00 5a  00 a0 00 0f 7d 0d 87 20  |G.._.S.Z....}.. |
00000150  01 b7 04 63 00 1e 02 02  01 87 c8 b9 04 87 08 31  |...c...........1|
00000160  00 d7 04 1f 01 06 4e 00  04 20 66 ec a6 44 10 00  |......N.. f..D..|
00000170  87 50 72 00 6f 78 79 53  74 75 62 43 c0 6c 73 69  |.Pr.oxyStubC.lsi|
00000180  64 33 32 8d 37 81 07 08  37 00 33 80 18 a1 00 fc  |d32.7...7.3.....|
00000190  43 88 b6 bb a8 80 2e 7b  00 39 80 48 00 46 00 34  |C......{.9.H.F.4|
000001a0  00 37 00 36 00 2a 43 80  05 2d 80 01 31 80 01 34  |.7.6.*C..-..1..4|
000001b0  00 82 2d 80 0a 44 00 44  00 41 80 04 a8 39 00 fe  |..-..D.D.A...9..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 18 24 03 00 fe  |............$...|
000001d0  ff ff 05 fe ff ff 02 18  24 03 00 18 24 00 00 00  |........$...$...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by patelv87 on 2010-07-08
Yep, I just did, but it seems like the windows partition is not showing up, I've pasted the output below.

priya@priya-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
done
priya@priya-laptop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
done
priya@priya-laptop:~$ 

Thank you for your help,
Vinay

---

### Post by garvinrick4 on 2010-07-08
There seems to be something going on in sda4 which is just suppose to
be an Extended Partition to house the logical partition for Ubuntu and swap.
Make sure you always put boot into sda not sda1, sda2 or so on, always sda
Ubuntus grub2 seems to be in right place but Windows? You notice in blkid that
it shows a mount point. Does sda2 show in gparted or disk utility? Give it a label
it is there so you can mount it in a live CD. If you label it OS.

sudo mkdir /media/OS
sudo mount /dev/sda2 /media/OS

Then backup anything you want for safety purposes. 
sda4 has me confused but maybe we can put Windows boot back in place
and then overwrite it with grub2 like it was suppose to.



[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459")

Found someone named oldfred that is good at boot scripts and contacted him for opinion.

---

### Post by oldfred on 2010-07-08
You windows install in sda2 is missing boot files. Was there another install as windows does move boot files to the first install with the boot flag. You do have the boot flag on sda2, so I do not know why files are missing:
Yours:
sda2: ______

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:

from my XP:
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM  

So we need to get two files and the boot.ini back into sda2.

This is the full list of repairs that I have saved. If you want to test directly booting windows you can run the fixMBR but will then have to reinstall grub to the MBR. (may be best to confirm it works)

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

To reinstall grub2 from a liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Your install is in sda5 so you can use instructions as is:
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

