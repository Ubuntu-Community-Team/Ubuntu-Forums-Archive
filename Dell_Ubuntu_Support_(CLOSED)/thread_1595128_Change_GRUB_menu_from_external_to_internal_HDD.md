---
title: "Change GRUB menu from external to internal HDD"
date: 2010-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mccbala on 2010-10-12
Hi...

Am a complete NOOB to linux as well ubuntu.. Here is a small history about my entry in ubuntu... Few days ago, I tried to install lucid lynx in my Dell Studio 1555 laptop.. I already have Windows xp installed in my laptop.. When I tried to install lucid lynx, the setup was just unable to read my partition table and displayed my whole 500GB HDD as unallocated!!! Though I was able to mount my partitions and read/write data thro live cd, Gparted and LL setup couldn't find partitons (so sad :( ).. It is a western digital HDD.. I don't know if it makes any diff but then I tried installing LL (lucid lynx) in my external seagate freeagent go portable hard drive and the partitions were displayed and LL gave me options to resize my partitons blah.. blah.. and i installed.. end of history...sorry if it was tooo long.. :P Why I am telling the history is that, I wasn't able to find the reason for this weird behavior of my internal hdd.. If any other member has faced this and has a solution.. pleeeeez lemme know..

Now since the LL is installed in external hdd abt which i don have any complaints, I have one problem though.. The GRUB menu has got itself into external hdd (obviously) and won't be displayed unless i connect it (obvvviously)... I want to change this GRUB menu into my internal hdd so that even if i don't connect the hdd, i shud be able to boot into windows (which is installed in internal HDD).. Of course, am aware that i need to connect the external HDD to boot into LL.. So what I wanna know is how to transfer my GRUB menu into internal HDD.. Please give me a reasonably explained NOOB's tutorial so that am able to do it.. 

And sorry about the essay, bear with my "in-detail" mode.. :)

---

### Post by oldfred on 2010-10-12
You cannot directly boot windows with grub in the MBR unless you have a partition with grub installed. So you have to have the external installed for grub in the MBR to find the rest of grub in the LL install. Also the grub menu is on external. 

Does not your system directly boot windows if you do not have the external plugged in?

---

### Post by mccbala on 2010-10-13
Well... I was able to boot into windows without the external hdd.. This means that I'll have the old grub in my internal hdd rite? tweaking won't that do any good? and no.. am not able to boot into any OS without external hdd.. It displays, "device not found" and stops.. help me guyz.. if its not for visual studio, i won't be using windows at all.. i've just fallen madly in love with lucid lynx... lucid is my cupid.. :D

---

### Post by oldfred on 2010-10-13
So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by mccbala on 2010-10-13
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       419430399 sectors, but according to the info from 
                       fdisk, it has 419437691 sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       452481023 sectors, but according to the info from 
                       fdisk, it has 452483119 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: unknown filesystem type ''
$MFTMirr does not match $MFT (record 6).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 6).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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

/dev/sda1          20,980,890   104,856,254    83,875,365   1 FAT12
/dev/sda2         104,859,648   524,297,339   419,437,692   7 HPFS/NTFS
/dev/sda3         524,290,048   976,773,167   452,483,120   7 HPFS/NTFS
/dev/sda4    *         16,065    20,980,889    20,964,825   f W95 Ext d (LBA)
/dev/sda5              16,128    20,980,889    20,964,762   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   188,011,275   188,011,213   7 HPFS/NTFS
/dev/sdb2         209,712,510   419,425,019   209,712,510   7 HPFS/NTFS
/dev/sdb3         419,425,020   625,137,344   205,712,325   7 HPFS/NTFS
/dev/sdb4         188,012,542   209,711,103    21,698,562   5 Extended
/dev/sdb5         188,012,544   208,695,295    20,682,752  83 Linux
/dev/sdb6         208,697,344   209,711,103     1,013,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        FE0272DB0272987B                       ntfs       STORAGE1                      
/dev/sda3        B09A79FE9A79C180                       ntfs       STORAGE2                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7A7029CE702991C5                       ntfs       WINDOWS                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2CC3DB6CC3DA597                       ntfs       Balaji01                      
/dev/sdb2        B218F72A18F6EBEB                       ntfs       Balaji02                      
/dev/sdb3        3408833B0882FADE                       ntfs       Balaji03                      
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        8242ba7a-04e7-47b1-b0b2-e243b5357a6d   ext4                                     
/dev/sdb6        a4af6d34-0145-4232-90db-5167c121fb9d   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/Balaji02          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/Balaji03          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8242ba7a-04e7-47b1-b0b2-e243b5357a6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8242ba7a-04e7-47b1-b0b2-e243b5357a6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8242ba7a-04e7-47b1-b0b2-e243b5357a6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8242ba7a-04e7-47b1-b0b2-e243b5357a6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8242ba7a-04e7-47b1-b0b2-e243b5357a6d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fe0272db0272987b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8242ba7a-04e7-47b1-b0b2-e243b5357a6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a4af6d34-0145-4232-90db-5167c121fb9d none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  98.6GB: boot/grub/core.img
 100.9GB: boot/grub/grub.cfg
  99.7GB: boot/initrd.img-2.6.32-21-generic
 100.0GB: boot/initrd.img-2.6.32-25-generic
  99.5GB: boot/vmlinuz-2.6.32-21-generic
  99.8GB: boot/vmlinuz-2.6.32-25-generic
 100.0GB: initrd.img
  99.7GB: initrd.img.old
  99.8GB: vmlinuz
  99.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
00000010  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 9a 24 40 01  |.............$@.|
00000020  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sdb4

00000000  06 7b 28 7f 9b 88 52 ff  ba 26 6a c5 2c ca cd 25  |.{(...R..&j.,..%|
00000010  96 15 c2 88 fb d1 54 5e  cd af f7 bf 53 2f d2 92  |......T^....S/..|
00000020  03 ef 38 7a 9d b9 48 1b  b6 d6 b1 c6 d3 fd 7a d9  |..8z..H.......z.|
00000030  6b b8 0e 9f c6 7e db d6  68 15 65 13 53 97 ef 9a  |k....~..h.e.S...|
00000040  6b 99 2e 40 e1 e7 8f 28  d3 46 62 05 10 10 70 47  |k..@...(.Fb...pG|
00000050  67 22 29 98 56 8a cc 55  56 d3 26 b2 92 ec 96 d0  |g").V..UV.&.....|
00000060  59 a6 82 71 ec e3 0b 8f  4b de c0 00 00 00 0a 3d  |Y..q....K......=|
00000070  34 42 db e0 26 a0 be 8e  14 e7 7a b2 7d 9f ff ff  |4B..&.....z.}...|
00000080  e8 e4 00 00 00 01 00 d5  34 12 26 50 94 cd f4 29  |........4.&P...)|
00000090  c9 69 ff fb 90 64 bb 00  04 eb 5f d8 eb 09 35 c2  |.i...d...._...5.|
000000a0  18 22 1b 19 08 02 70 13  15 71 5b 4c b0 b7 68 5b  |."....p..q[L..h[|
000000b0  88 6b 60 50 09 c0 63 ea  17 dc 98 2d d2 ca ec 40  |.k`P..c....-...@|
000000c0  64 ca 8f 5e dd e4 b2 4b  f5 5e c4 67 12 5e 7f b9  |d..^...K.^.g.^..|
000000d0  d6 b5 1d 58 23 84 76 87  95 c9 df 46 ec 46 44 88  |...X#.v....F.FD.|
000000e0  75 ad 24 34 e8 f0 81 0e  b8 ad 59 84 32 66 5a 6f  |u.$4......Y.2fZo|
000000f0  3f 36 2c a7 3b 72 4f 38  e6 7d d2 0c f5 66 d3 7c  |?6,.;rO8.}...f.||
00000100  2e e9 6b 6a 4d c5 80 89  95 a0 85 40 0b 07 87 3c  |..kjM......@...<|
00000110  f2 a7 36 b6 29 8e 73 95  35 40 f5 b5 b5 54 9a 74  |..6.).s.5@...T.t|
00000120  a3 ba cd 61 e7 99 c3 a2  8f f6 5a 87 e6 ef 9c 9e  |...a......Z.....|
00000130  5e 53 8b c2 3b 83 9a 0d  c2 e4 71 eb 07 46 67 ae  |^S..;.....q..Fg.|
00000140  91 94 6f 40 88 82 7b 94  6a 86 7c 9a f4 f2 df ff  |..o@..{.j.|.....|
00000150  fe 9c c0 00 00 00 20 5e  06 00 50 36 ca e3 5b 79  |...... ^..P6..[y|
00000160  07 01 3e c6 a4 c9 20 d0  c0 13 39 de f8 08 2d b0  |..>... ...9...-.|
00000170  39 13 c6 ff ca ef 54 ae  28 1c 40 32 33 6a 43 3b  |9.....T.(.@23jC;|
00000180  8b f9 2b 01 04 51 19 45  ea 19 9c ed 50 2a da 59  |..+..Q.E....P*.Y|
00000190  9e f3 0c e9 19 5e fb cd  ef ee a8 72 cc e7 75 fa  |.....^.....r..u.|
000001a0  ee 03 7a 4e 26 8a 8e e2  ce 7a be 57 e6 4c 9e 5a  |..zN&....z.W.L.Z|
000001b0  fb b0 a2 b2 4d e1 d0 2b  74 ab 7f bc f5 33 00 fe  |....M..+t....3..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 3b 01 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 98  3b 01 00 80 0f 00 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-10-13
You have grub in sda but the install is in sdb5. (ignore the same drive mention in the sda entry as that is a bug in grub or the script). And you boot windows from sdb but it looks like your windows is in sda2. I would install the windows boot loader to sda to boot sda2 9if that is your correct windows) and install grub2 to sdb to boot Ubuntu in sdb5.

You also have a MFT error in sdb1. Use windows to run chkdsk on sdb1 and if that does not work:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

If you boot Ubuntu, then you can easily install grub2 from there, otherwise you have to use liveCD.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by mccbala on 2010-10-13
Dude... Thanks... I've done as you've instructed here... Have set both my internal and external hdd in grub-pc reconfiguration.. Gonna restart my system.. Hope I come back and report that it was successful here.. Thanks man!

---

### Post by mccbala on 2010-10-13
Well... No change... Am still facing the same problem... Even after selecting both HDD as boot hdd in grub-pc

---

### Post by oldfred on 2010-10-13
Did you run chkdsk on sdb1 to see if that solved the problem with the MFT or run testdisk to solve that.

Did you set sdb the 320GB drive as first to boot, so grub loads. The set sda the 500GB drive second and without the external drive does windows not boot directly. 

If not rerun boot info script to see that everything was installed correctly.

---

