---
title: "installing 10.04 and higher with windows 7"
date: 2010-09-20
forum: Desktop Environments
---

### Post by AM_SOS on 2010-09-20
hi all,
i am posting after quite some time.
i currently use a toshiba A200 with 2.0 core duo processor, and an I 945 chipset. since the laptop is quite old now, i am planning to buy another toshiba.
since i want an ultraportable, i have narrowed down on the nice satellite T235 or the much acclaimed portege R700.
now these laptops are being shipped with windows 7 OS.
i am wondering if anyone has installed a dual boot option of 10.04 in any of these computers ?
i had tried quite some time ago to do a dual boot in a compaq. however, there was some problem with the boot loader and i although ubuntu installed nicely, i was simply unable to get the system to boot up !
so is there a compatibility issue with 10.04 and later versions on the one hand and and windown 7 on the other ?
thanks!

---

### Post by SeijiSensei on 2010-09-21
I just recently installed Ubuntu over Windows 7 on a couple of machines without any problems.  The most difficult part of any installation over an existing operating system and boot loader is repartitioning the drive and insuring that grub is installed in the master boot record.  As I recall, I could manage both of those during the Ubuntu installation.

If you're worried about whether Windows will survive the experience, I'd suggest booting the LiveCD and running gparted before installation.  You'll be able to optimize and resize your NTFS partition prior to running the Ubuntu installer.  Later, when you run the installer, you can repartition the non-Windows free space as you wish.

---

### Post by AM_SOS on 2010-09-21
hey thanks,
see i have been using XP and ubuntu for quite some time now. and never had any issues with either OS. ubuntu is really non-intrusive and i access the windows drives from within ubuntu and write a lot of data.
earlier i would simply boot from the live CD, select the option of installing ubuntu with XP, and use thee slider to select my partition size. simple and straight!
once i tried something similar with win 7 and things went all wrong. i think resizing the windows partitions was a problem - i cant remember now.
so, can you or someone provide the link to some kind of step by step tutorial for installing 10.04 with win 7, with special reference to the boot loader problems as well as the resizing of windows partitions ?
thanks !

---

### Post by Ben_neB on 2010-09-21
Here's a pretty good step-by-step for 10.04 dual-booted on a system that already had Windows 7 on it:

[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)

---

### Post by wilee-nilee on 2010-09-21
> **AM_SOS said:**
> hey thanks,
see i have been using XP and ubuntu for quite some time now. and never had any issues with either OS. ubuntu is really non-intrusive and i access the windows drives from within ubuntu and write a lot of data.
earlier i would simply boot from the live CD, select the option of installing ubuntu with XP, and use thee slider to select my partition size. simple and straight!
once i tried something similar with win 7 and things went all wrong. i think resizing the windows partitions was a problem - i cant remember now.
so, can you or someone provide the link to some kind of step by step tutorial for installing 10.04 with win 7, with special reference to the boot loader problems as well as the resizing of windows partitions ?
thanks !

Actually there is a little wrong here. You want to use the disk manager in windows to shrink it's partitions. Then reboot and make sure that it is running okay. You can use gparted as suggested but if you don't turn off the round to cylinders you may bork W7. Always reboot after repartitioning a Windows setup to make sure it works, before installing another OS.

Then you will have a open unallocated space to install how you like.

Using the slider and letting it run is asking for problems. A picture of gparted is helpful, make sure this is clicked off it says on in the picture though. 
[ATTACH]170191[/ATTACH]

If you ever have to reinstall W7 always preformat the partitions with gparted if your dual booting so the Linux doesn't go unallocated, it is a possibility, with out pre-formatting W7

---

### Post by Ben_neB on 2010-09-21
> **wilee-nilee said:**
>  You can use gparted as suggested but if you don't turn off the round to cylinders you may bork W7.
Actually, I've used gparted to do it literally dozens of times with no problems. Ubuntu's pretty good about doing it right. (And it's a lot quicker at it than Windows is, usually.) In fact, I just did that with a Vista/10.04 dual boot system last Thursday.

---

### Post by wilee-nilee on 2010-09-21
> **Ben_neB said:**
> Actually, I've used gparted to do it literally dozens of times with no problems. Ubuntu's pretty good about doing it right. (And it's a lot quicker at it than Windows is, usually.) In fact, I just did that with a Vista/10.04 dual boot system last Thursday.

Yes it is but from the people who know this stuff turn off the round to cylinders when resizing W7. I didn't say don't use it, I just am giving the known correct way in this situation.

---

### Post by Ben_neB on 2010-09-21
> **wilee-nilee said:**
> Yes it is but from the people who know this stuff turn off the round to cylinders when resizing W7.
Is that something that has changed in Win7? Because I work in a linux-centric computer repair shop, and we have done a TON of dual boots and never turned off "round to cylinders" and we have never screwed up a windows install by using gparted.

---

### Post by wilee-nilee on 2010-09-21
> **Ben_neB said:**
> Is that something that has changed in Win7? Because I work in a linux-centric computer repair shop, and we have done a TON of dual boots and never turned off "round to cylinders" and we have never screwed up a windows install by using gparted.

Somewhere on This amazing site Herman talks about this I am trying to find it. But yes this is a W7 issue, gparted on XP no problems, not sure with Vista.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Ben_neB on 2010-09-21
> **wilee-nilee said:**
> But yes this is a W7 issue, gparted on XP no problems, not sure with Vista.
Thanks for the link. That's good to know, it will probably save us a few headaches at work. :)

---

### Post by wilee-nilee on 2010-09-21
> **Ben_neB said:**
> Thanks for the link. That's good to know, it will probably save us a few headaches at work. :)

You know it. I have also had Ubuntu go unallocated with 2 reinstalls of W7 and letting it build the partitions. In a pre-formatted ntfs in gparted the boot goes in the OS. If you let it do it's dirty work itself W7 makes 2 partitions a 200MB boot and the OS, this has caused me two installs. But I have everything backed up, so it was a learning experience I just laughed when it happened.

---

### Post by AM_SOS on 2010-09-22
hey thanks people !
guess this is pretty much it and i shouldn't have any problems now in installing the dual boot now.

---

### Post by apverma13 on 2010-09-23
I have installed ubuntu 10.04LTS along with windows 7. but during  startup when i select window 7's entry in grub my computer restarts.

i have tried update-grub but nothing changes.


```
                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #8 for /boot/grub.

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6  starts 
                       at sector 1615. But according to the info from  fdisk, 
                       sda6 starts at sector 61450240.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda7:  _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,894   156,280,319   156,071,426   f W95 Ext d  (LBA)
/dev/sda5          20,482,938    61,448,624    40,965,687   b W95 FAT32
/dev/sda6          61,450,240   102,412,287    40,962,048   7 HPFS/NTFS
/dev/sda7         102,414,438   156,280,319    53,865,882   b W95 FAT32
/dev/sda8             208,896    20,482,047    20,273,152  83 Linux


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE       LABEL                          

/dev/sda1        9468456A68454C64                       ntfs        System Reserved               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        A0C9-1144                              vfat        MOVIES                        
/dev/sda6        58E04887E0486D76                       ntfs                                      
/dev/sda7        0CB3-B441                              vfat        SOFTWARES                     
/dev/sda8        12c1f332-3bd9-4768-adf0-50dde0df15fc   ext4                                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4        (rw,errors=remount-ro)
/dev/sda7        /media/SOFTWARES         vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda8/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set  12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set  12c1f332-3bd9-4768-adf0-50dde0df15fc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set  12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set  12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9468456a68454c64
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0

=================== sda8: Location of files loaded by Grub:  ===================


   7.1GB: boot/grub/core.img
   7.1GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-21-generic
   7.9GB: initrd.img
   7.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown BootLoader  on sda2

00000000  31 a2 35 85 f6 bc 50 88  fa 7f 50 db 4a 10 83 a6   |1.5...P...P.J...|
00000010  24 ea 02 65 7c 7c 7d 1e  2d 2f da db cc 3c b3 17   |$..e||}.-/...<..|
00000020  39 1c 9a 4e 43 96 ac 8a  f6 48 7d e9 30 c8 9a e0   |9..NC....H}.0...|
00000030  4d 27 d1 60 93 11 c9 18  78 4f 30 66 a6 49 70 d3   |M'.`....xO0f.Ip.|
00000040  c4 40 6e 59 bb 9e ba 5a  f0 13 be ae 8b 4d d9 38   |.@nY...Z.....M.8|
00000050  47 13 45 a1 b0 6b 79 13  f1 a5 85 58 ca 86 07 51   |G.E..ky....X...Q|
00000060  77 7d 9b 27 0b b2 ed 1a  e0 c1 fc 15 f1 8e ef 15   |w}.'............|
00000070  8c c3 48 44 ab 27 26 6c  bd 6a 9e 91 22 67 f9 34   |..HD.'&l.j.."g.4|
00000080  42 a3 25 ed e7 d5 f5 0d  ad 80 e0 c7 36 c6 cf 60   |B.%.........6..`|
00000090  c5 3e 4b dd be c1 8d c7  d6 f4 45 7c ae 1a 14 dc   |.>K.......E|....|
000000a0  41 f4 05 d9 70 63 a3 e3  1c f1 9f 75 35 f7 43 d9   |A...pc.....u5.C.|
000000b0  b7 7d 20 1b 75 1a 7a 34  b1 a5 ae e3 0d 7d 87 d7  |.}  .u.z4.....}..|
000000c0  2b fd 3f 7b af d4 53 11  96 1c 42 37 56 9e 9c 5f   |+.?{..S...B7V.._|
000000d0  65 31 0e 16 3e 55 9f d6  21 3d 6b 72 52 40 53 06   |e1..>U..!=krR@S.|
000000e0  5e 9c c6 d1 04 82 5c 91  89 97 af 81 20 d2 cd 77   |^.....\..... ..w|
000000f0  33 21 71 3d 8d 6d 8c 15  6f 2d 9a 79 bb 94 92 50   |3!q=.m..o-.y...P|
00000100  8f 2f 9e 77 22 d1 9e 5b  fa 59 ed 92 d4 2e ec 9b   |./.w"..[.Y......|
00000110  88 bc 9e 08 e8 d5 e8 c2  5d 6e 76 c6 77 cb 9c b7   |........]nv.w...|
00000120  ac 11 6f a3 34 47 9d 80  ca af fb 4a e9 d7 c3 ce   |..o.4G.....J....|
00000130  e1 09 55 7c a0 77 72 8a  82 2e 1c 73 39 8d 29 26   |..U|.wr....s9.)&|
00000140  dd a1 51 8e 08 f8 31 be  95 fe 07 41 ad 58 56 1f   |..Q...1....A.XV.|
00000150  59 1f 8a de 04 71 d5 ff  50 c3 8a 91 f3 60 b7 74   |Y....q..P....`.t|
00000160  23 e5 e9 76 a6 5b b7 49  4a 18 10 07 f7 6c 8f 3e   |#..v.[.IJ....l.>|
00000170  65 3d 2b 74 84 66 08 65  41 83 6f 4a 51 65 c4 e9   |e=+t.f.eA.oJQe..|
00000180  cf 65 ec 99 df e5 93 c3  a8 f6 c4 f0 ac 9d 46 f6   |.e............F.|
00000190  4a 74 db eb 43 a0 2a dd  07 8d 3d d9 91 06 2c 68   |Jt..C.*...=...,h|
000001a0  53 cc 2f ba cb 34 5c 96  c7 97 ef d4 23 16 af c3   |S./..4\.....#...|
000001b0  4b e6 5a d9 26 92 4e 6c  6b 46 6b 63 eb 85 00 df   |K.Z.&.NlkFkc....|
000001c0  d3 ff 0b df d3 ff 7c 5b  35 01 37 16 71 02 00 df   |......|[5.7.q...|
000001d0  d3 ff 05 df d3 ff b3 71  a6 03 4f 0e 71 02 00 00   |.......q..O.q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa   |..............U.|
00000200


```

help me out please

---

### Post by Phil92804 on 2010-09-23
I can only share my limited experience.  I am using a 6 year old Sony Vaio, Centrino Duo, 2 GB and 80 GB Hard drive.  I run Windows 7 for work on it (wish I had more memory and disc space!). I was very wary about installing Ubuntu and ran it from a USB drive for weeks.  I was concerned about disc space and dual booting. 

Then, following the basic instructions on the Ubuntu site and installing from the USB drive, Ubuntu segmented a small amount of disc space (12 GB) for its use and flawlessly created the dual boot procedure.  I have not had a problem.

It worked!

---

### Post by LinuxPhreak on 2010-09-23
For the complete newbie that may come across this thread. Here is the exact process of dual booting. All of the above is correct but here is step by step. 


[LIST=1]
[*]Burn Ubuntu ISO Image at lowest speed onto a disk
[*]Backup all important data
[*]Defragment Windows Installation
[*]Restart computer boot from CD (You may need to configure BIOS to do this)
[*]When asked if you want to install on entire disk or resize Windows choose to resize Windows
[*]Finnish Install
[*]When done you should be greeted with the GRUB menu
[/LIST]

You can use gParted to resize Windows. It is still recomended that you defragment you Windows before resizing using GParted. 

Alternate methods for Dual Booting are as follows. 
WUBI (Very safe way to install Ubuntu to Dual Boot. No disk is required)
Instlux (Used to be for Ubuntu & SUSE and is primarily for SUSE now. Source code is availible on source forge, works much the same way as WUBI)
UNetBootin (Primarily used to install a Live CD onto Flash Drive for Windows users. Their is a version in Ubuntu repos also. With it you can also do a Frugal Install of Ubuntu)
BEeN GRUBed (A tool to install Ubuntu and other Linux OSes without the need for CD's, unlike the above programs BEeN GRUBed doesn't do loop mount install. It litterly partitions the hard Hard Drive. It is recomended for people with more experience, however if a novice is having trouble changing BIOS settings they can use BEeN GRUBed to boot the CD)

---

