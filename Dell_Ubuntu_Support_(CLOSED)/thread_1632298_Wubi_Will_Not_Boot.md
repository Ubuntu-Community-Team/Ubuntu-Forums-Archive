---
title: "Wubi Will Not Boot"
date: 2010-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheFuzz4 on 2010-11-27
I installed Ubuntu on my girlfriends laptop its a Dell Inspiron.  I had the Ubuntu installed through a Wubi install.  Its been working great for the last 5 months then today she got updates and did a restart.  Now when the laptop attempts to boot up it says
NO WU BUILDR
no wu buildr

Her laptop has no pause button on it so I can't see the full messages because it restarts and I'm attempting to get into the grub menu but that is also not working.  If anyone has any ideas on how to fix this it would be greatly appreciated as she does have some things on the WUBI virtual disk and if I can get it back that would be great. 

Thank you for your assistance with this.

---

### Post by wilee-nilee on 2010-11-27
To make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags [code ][/code ] paste all the text in between.

We have been seeing grub updates that are causing problems this script will show us the setup.

Also please identify the Windows version XP/Vista/W7 which one?

---

### Post by TheFuzz4 on 2010-11-27
Thank you very much for the help, I am currently d/ling a ubuntu iso so I can make a live usb.  Once I get this done I'll get you the results from the script.  Thank you.

---

### Post by TheFuzz4 on 2010-11-27
Oh and she's running Windows Vista

---

### Post by wilee-nilee on 2010-11-27
> **TheFuzz4 said:**
> Oh and she's running Windows Vista

Cool personaly when it comes to bootloaders and the MBR I'm partial to the MS for MS method, although Lilo works okay from Ubuntu.

So if you don't have a Vista recovery disc or install disc you can download this one, for reloading the MBR I suspect that is where we are going, the script just helps a great deal.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by bcbc on 2010-11-28
See this [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

If she upgraded from 10.04.1 to 10.10, try replacing the wubildr. If it's 10.04.1, you have to edit the grub.cfg as described to get it booting.

---

### Post by wilee-nilee on 2010-11-28
> **bcbc said:**
> See this [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

If she upgraded from 10.04.1 to 10.10, try replacing the wubildr. If it's 10.04.1, you have to edit the grub.cfg as described to get it booting.

It is always a relief to see you in on the wubi action.;)

---

### Post by bcbc on 2010-11-28
> **wilee-nilee said:**
> It is always a relief to see you in on the wubi action.;)

Wubi installs have had lots of problems lately :popcorn:

Thanks to grub #-o

---

### Post by TheFuzz4 on 2010-11-28
Here is results.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdc3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 61.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63        80,324        80,262  de Dell Utility
/dev/sdc2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sdc3    *     30,801,920   312,579,759   281,777,840   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1014 MB, 1014497280 bytes
32 heads, 61 sectors/track, 1015 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             61     1,981,279     1,981,219   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       37a716f1-4183-483e-b724-509ecefd4a57   ext3                                     
/dev/loop2       443b6d85-8eec-4ec9-9af4-d1b5bfb40ab0   ext4                                     
/dev/loop3       443b6d85-8eec-4ec9-9af4-d1b5bfb40ab0   ext4                                     
/dev/sdc1        3030-3030                              vfat       DellUtility                   
/dev/sdc2        FA6045A960456E07                       ntfs       RECOVERY                      
/dev/sdc3        CE5447E85447D1BF                       ntfs       OS                            
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2DC8-2A7D                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc3        /win                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/loop2       /vdisk                   ext4       (rw)
/dev/sdd1        /media/2DC8-2A7D         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sdc3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ce5447e85447d1bf
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ce5447e85447d1bf
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set ce5447e85447d1bf
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdc3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdc3/Wubi: Location of files loaded by Grub: =================


  21.9GB: boot/grub/grub.cfg
  12.9GB: boot/initrd.img-2.6.32-24-generic
  17.2GB: boot/initrd.img-2.6.32-25-generic
  17.6GB: boot/initrd.img-2.6.32-26-generic
  10.8GB: boot/vmlinuz-2.6.32-24-generic
  10.8GB: boot/vmlinuz-2.6.32-25-generic
  10.8GB: boot/vmlinuz-2.6.32-26-generic
  17.6GB: initrd.img
  17.2GB: initrd.img.old
  10.8GB: vmlinuz
  10.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3d 00 20 00 00 00 00 00  |........=. .....|
00000020  22 3b 1e 00 90 07 00 00  00 00 00 00 02 00 00 00  |";..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 7d 2a c8 2d 20  20 20 20 20 20 20 20 20  |..)}*.-         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 20 b7 15 00  66 ba 00 00 00 00 bb 00  |}.f. ...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

umount: /win: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

Thanks for the help

---

### Post by TheFuzz4 on 2010-11-28
Also she is still Running Lucid 10.04 because I knew there were issues with upgrading from 10.04. to 10.10.  I tried replacing the wubuilder file but I'm still getting the same error so moving onto the grub.cfg

---

### Post by TheFuzz4 on 2010-11-28
I took a look at the grub.cfg file and it looks to be the new grub 2 because it looks like no other grub I've seen before. I almost wonder if there is a problem with the windows boot loader calling the wubi.  I just need to remember now how the hell to modify the boot loader for windows.  Just a FYI vista is still loading just fine its just Ubuntu that refuses to load with the error no WU BUILDR.  I know that the files do exist in the root of the C:\ drive as well as under C:\ubuntu\winboot as well.  I will figure this out one way or another.

---

### Post by TheFuzz4 on 2010-11-28
Ok this was an interesting fix for me.  I ended up installing EasyBCD so I could actually see vistas boot file I wasn't about to go play with it in the cmd line.  Stupid Vista.  Ok so here is what I ended up doing.  I took the wubildr from the actual root of the C: drive and made a backup of the ones in the winboot folder and then replaced it with the ones from the root of the C: drive.  It still throws up the no wubildr error but then the grub menu loads up and boom into Ubuntu it went.  Now my g/f is going to backup her ubuntu and wipe her computer clean so I can actually install just Ubuntu on the laptop and be done with the dual boot.

---

### Post by bcbc on 2010-11-29
> **TheFuzz4 said:**
> Ok this was an interesting fix for me.  I ended up installing EasyBCD so I could actually see vistas boot file I wasn't about to go play with it in the cmd line.  Stupid Vista.  Ok so here is what I ended up doing.  I took the wubildr from the actual root of the C: drive and made a backup of the ones in the winboot folder and then replaced it with the ones from the root of the C: drive.  It still throws up the no wubildr error but then the grub menu loads up and boom into Ubuntu it went.  Now my g/f is going to backup her ubuntu and wipe her computer clean so I can actually install just Ubuntu on the laptop and be done with the dual boot.

That sounds like a plan... 

There's nothing bad about a brand new install, but just to float one other option, if the wubi has a lot of customization etc. and you are able to create new partitions for it, you could migrate the wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Then you can do what you want with the remaining Vista partition afterwards.

---

