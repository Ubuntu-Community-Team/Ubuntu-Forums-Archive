---
title: "Windows XP doesn't show up in Grub (Ubuntu 10.10)"
date: 2010-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SquireSuzuki on 2010-12-29
Hello,
I'm completely new to linux. The only commands I only really know how to use are cd, su and sudo. The main reason I'm using linux is to run a multiplayer server for this game called Minecraft.
Anyways, that's not important. I attempted to create a dual boot on my computer. I already had windows XP on it and then went through the installation of ubuntu 10.10. When I installed it, I selected it to be installed next to other operating systems...just as all the dual boot youtube videos tell me to. When dragging the partition-meter, however, one box said "Files" while the other read "Ubuntu". I am positive that files is where windows is located, however on the videos it did not read files, it read "Windows XP". I went ahead with the installation, but now when I start up the computer, there are 5 options in GRUB but none say Windows XP. There is ubuntu, ubuntu recovery, and other things like "dell utility", acronis backup, etc.
 I looked this up, and found that you can edit the grub file menu.lst to add the windows, but I see that this file is no longer included in ubuntu 10.10 but replaced by the file grub.cfg (in /boot/grub). I don't think I can do the same here as mentioned in [this thread]("http://wwww.ubuntuforums.org/showthread.php?t=567285"). 

Can some one help me? Thanks so much. I hate to rush you, but I have a serverload of people waiting on a linux newbie (my server was previously running on mac).

Thanks!!!

---

### Post by mikewhatever on 2010-12-29
Can you post the output of **sudo fdisk -l** to show your partition table. WindowsXP in the videos was just a partition label, could have been anything.

---

### Post by SquireSuzuki on 2010-12-29
> **mikewhatever said:**
> Can you post the output of **sudo fdisk -l** to show your partition table. WindowsXP in the videos was just a partition label, could have been anything.

XP is on sda2. Here are the results:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a6da93f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15       31509   252981458    7  HPFS/NTFS
/dev/sda3           31509       37701    49737729    5  Extended
/dev/sda4           37702       38913     9735390   db  CP/M / CTOS / ...
/dev/sda5           31509       37443    47657984   83  Linux
/dev/sda6           37443       37701     2078720   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26bc0d1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6242    50138833+   7  HPFS/NTFS
/dev/sdb2            6243       38913   262429807+   5  Extended
/dev/sdb5            6243       38913   262429776   bc  Unknown
```

---

### Post by garvinrick4 on 2010-12-29
Run this in terminal in ubuntu
```
sudo update-grub
```
See if that puts your windows install in grub-config and as a menu entry.
If not you have to run this script and post it.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by SquireSuzuki on 2010-12-29
> **garvinrick4 said:**
> Run this in terminal in ubuntu
```
sudo update-grub
```See if that puts your windows install in grub-config and as a menu entry.
If not you have to run this script and post it.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

Here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847  de Dell Utility
/dev/sda2    *        224,910   506,187,825   505,962,916   7 HPFS/NTFS
/dev/sda3         506,189,822   605,665,279    99,475,458   5 Extended
/dev/sda5         506,189,824   601,505,791    95,315,968  83 Linux
/dev/sda6         601,507,840   605,665,279     4,157,440  82 Linux swap / Solaris
/dev/sda4         605,666,565   625,137,344    19,470,780  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   100,277,729   100,277,667   7 HPFS/NTFS
/dev/sdb2         100,277,730   625,137,344   524,859,615   5 Extended
/dev/sdb5         100,277,793   625,137,344   524,859,552  bc Acronis BackUp


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-0612                              vfat       DellUtility                   
/dev/sda2        BA740169740129A9                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4                                               vfat       DellRestore                   
/dev/sda5        89ce26d4-1b5b-48df-a01a-d55cfc4977af   ext4                                     
/dev/sda6        d5876de1-f31a-4d13-8458-dc8d68f330cf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        84E4E3DCE4E3CE8C                       ntfs       New Volume                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        19E7-DCAF                              vfat       ACRONIS SZ                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=89ce26d4-1b5b-48df-a01a-d55cfc4977af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=89ce26d4-1b5b-48df-a01a-d55cfc4977af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 89ce26d4-1b5b-48df-a01a-d55cfc4977af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 07d6-0612
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Acronis Secure Zone (on /dev/sdb5)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 19e7-dcaf
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
UUID=89ce26d4-1b5b-48df-a01a-d55cfc4977af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d5876de1-f31a-4d13-8458-dc8d68f330cf none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 287.2GB: boot/grub/core.img
 261.4GB: boot/grub/grub.cfg
 260.2GB: boot/initrd.img-2.6.35-24-generic-pae
 287.2GB: boot/vmlinuz-2.6.35-24-generic-pae
 260.2GB: initrd.img
 287.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  6d 70 23 73 18 6d 73 67  4a 8c 56 03 f0 a9 cd 07  |mp#s.msgJ.V.....|
00000010  f4 06 73 31 77 03 43 00  5f 4f 55 00 54 4c 4f 4f  |..s1w.C._OU.TLOO|
00000020  4b 2e 45 58 66 45 25 a3  85 03 f8 a8 7f 03 f3 16  |K.EXfE%.........|
00000030  4d 19 f1 06 70 61 30 a7  9f 11 36 35 63 2c 00 61  |M...pa0...65c,.a|
00000040  ff 0d 40 07 01 10 a8 5f  50 80 4f 57 45 52 50 4e  |..@...._P.OWERPN|
00000050  54 0f 07 1c 36 35 90 a2  f3 0d 7d 0a 74 00 5f b2  |T...65....}.t._.|
00000060  73 30 38 62 61 2a 1c 75  0a 20 70 26 21 7f 03 00  |s08ba*.u. p&!...|
00000070  00 01 00 70 9a 57 49 20  4e 57 4f 52 44 ef 06 36  |...p.WI NWORD..6|
00000080  35 78 d0 43 59 74 0a 73  1f 77 4d 70 57 6e 30 69  |5x.CYt.s.wMpWn0i|
00000090  6e 6a 61 d9 0d 55 46 af  00 d8 d0 e8 af 74 03 75  |nja..UF......t.u|
000000a0  7d 08 f4 22 f0 57 00 4d  69 72 72 6f 72 73 45 3c  |}..".W.MirrorsE<|
000000b0  64 67 af 1f 60 b8 73 0a  f3 1b 01 00 31 78 03 54  |dg..`.s.....1x.T|
000000c0  64 47 6c 4d 96 34 70 e2  7f 75 5b f3 22 e0 61 f4  |dGlM.4p..u[.".a.|
000000d0  06 71 54 ff 06 36 69 f9  fe c9 7a 65 7a 03 fb 06  |.qT..6i...zez...|
000000e0  26 03 73 87 f5 b2 75 50  21 70 06 6d 6f 6e 73 10  |&.s...uP!p.mons.|
000000f0  c6 74 72 9c 75 63 d0 77  b0 8b bf 11 35 36 7f 5b  |.tr.uc.w....56.[|
00000100  81 f3 22 41 00 5f 6e 6f  77 7f 5b f1 23 c2 30 00  |.."A._now.[.#.0.|
00000110  39 f4 14 73 1f 77 34 f0  30 85 7f 03 5f 94 18 37  |9..s.w4.0..._..7|
00000120  76 6b 03 7f 03 03 72 26  70 03 66 69 72 65 66 6f  |vk....r&p.firefo|
00000130  66 78 59 0a 05 15 b0 b5  7f 2d 73 0a 20 cc 00 5f  |fxY......-s. .._|
00000140  7f 03 e6 37 98 bc 7b 03  f7 22 71 70 cc 6e 68 6c  |...7..{.."qp.nhl|
00000150  00 a4 0f 74 20 56 c8 ee  c6 75 03 f3 22 77 03 cd  |...t V...u.."w..|
00000160  70 11 73 03 8f 62 0f b3  11 7f 2d 71 2d 71 03 76  |p.s..b....-q-q.v|
00000170  63 70 6c 0c 75 69 f9 0d  f5 30 72 69 70 74 0f 73  |cpl.ui...0ript.s|
00000180  03 f3 d2 20 11 f4 22 0a  00 5f 4e b4 56 4d 50 a3  |... ..".._N.VMP.|
00000190  74 cb da 95 03 ce f4 55  0a 3a f2 5a 01 76 de 61  |t......U.:.Z.v.a|
000001a0  70 5f 4e 00 65 65 64 20  66 6f 72 20 04 53 70 91  |p_N.eed for .Sp.|
000001b0  00 50 72 6f 53 74 40 72  65 65 74 20 44 20 00 fe  |.ProSt@reet D ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 ae 05 00 fe  |...........h....|
000001d0  ff ff 05 fe ff ff 02 68  ae 05 00 78 3f 00 00 00  |.......h...x?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ls: reading directory sda2/: Invalid or incomplete multibyte or wide character
```

---

### Post by garvinrick4 on 2010-12-30
Lets put grub2 back into mbr and see if that will get her going.
In ubuntu:
```
sudo grub-install /dev/sda
``````
sudo update-grub
``````
grep menuentry /boot/grub/grub.cfg
```Above will show you what is in grub menu. We want to see 
Windows and ubuntu of course. If you look in boot script the os-prober
is not finding it to put into grub-config. Hopefully it will get there. It finds
acronis zone in sdb drive.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

---

### Post by SquireSuzuki on 2010-12-30
Thanks for your help, but it still does not work. I entered those 3 commands in order, and the last gave:
```
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Dell Utility Partition (on /dev/sda1)" {
menuentry "Acronis Secure Zone (on /dev/sdb5)" {

```

---

### Post by SquireSuzuki on 2010-12-30
Oh, and the second command (update) gives:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
Found Dell Utility Partition on /dev/sda1
Found Acronis Secure Zone on /dev/sdb5
done

```

---

### Post by mikewhatever on 2010-12-30
> **garvinrick4 said:**
> Lets put grub2 back into mbr and see if that will get her going.

...

But Grub is already in the MBR.

It's somewhat puzzling why the Windows installation in /dev/sda2 is not picked up.

---

### Post by SquireSuzuki on 2010-12-30
I agree.
I just remembered that a while back, I installed a windows 7 "theme" to xp. it really screwed everything up in the registry, now everything is half fake-windows-7 and half xp. i wonder if I "repaired" windows, it would show up. Do you think so?

If there was still a menu.lst file, it would be super easy to add windows (apparently).

Honestly, I would be fine with completely erasing windows, but my dad and brother wouldn't like that...

---

### Post by mikewhatever on 2010-12-30
Here is a very similar problem from two weeks ago, but apparently, no solution yet.
[http://ubuntuforums.org/showthread.php?t=1645809](http://ubuntuforums.org/showthread.php?t=1645809)

The following error seems to be the common denominator.
> ls: reading directory sda2/: Invalid or incomplete multibyte or wide character

---

### Post by garvinrick4 on 2010-12-30
OS-prober is not reading sda2 your windows install.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Above in this link is how to restore xp boot manager to boot xp.
It also has a code to run in Ubuntu live cd called lilo which will
boot windows.
You can put windows back in place and then reinstall grub2 to see if 
that does it. There is a program called testdisk that quite often works in tough windows
cases.
                       # You can repair the boot sector of Windows system partition via "fixboot" from a Windows XP CD, or "bootrect /fixboot" from a Windows Vista/7 CD. But in my experience testdisk works best in this situation. So boot into a Linux OS or Live CD. If your system uses "apt-get" and has "testdisk" in its repositories (in Ubuntu: the universe repository needs to be enabled), you can install and run testdisk via 
```
sudo apt-get install testdisk
```
```
sudo testdisk
```
First screen: Select "No Log" and press enter.
Second screen: Select the hard drive containing the Windows system partition and choose "proceed".
Third screen: "intel"
Fourth screen: "advanced",
Fifth screen: Select the Windows system partition and choose "boot"
Sixth screen: "BackupBS"
Seventh screen: type "Y" to confirm

then press "q" a few times to quit testdisk, reboot and see whether you can boot into Windows.
Then go to linux and run update-grub

---

### Post by SquireSuzuki on 2010-12-30
> **garvinrick4 said:**
> 
Sixth screen: "BackupBS"



It does not have the option BackupBS. It only has the options List, Org.BS (with the description "Copy Boot sector over backup sector), Rebuild BS (with the description "Rebuild Boot Sector") and Dump ("dump boot sector and backup boot sector").

Which one do I choose?

---

### Post by garvinrick4 on 2010-12-30
Sorry took so long:
rebuild BS
then:
write
then:
q a few times to quite
then:
reboot

---

