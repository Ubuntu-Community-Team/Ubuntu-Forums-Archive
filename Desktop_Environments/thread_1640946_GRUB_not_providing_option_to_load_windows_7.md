---
title: "GRUB not providing option to load windows 7"
date: 2010-12-08
forum: Desktop Environments
---

### Post by kamalrajonnet on 2010-12-08
Hi,

In my ubuntu 10.10 wubi installation, I used to get the option for windows 7. Last week, i added some updates through update manager. After that the windows 7 option is missing. How do i resolve it?

- Kamalraj

---

### Post by bobcollard on 2010-12-08
> **kamalrajonnet said:**
> Hi,

In my ubuntu 10.10 wubi installation, I used to get the option for windows 7. Last week, i added some updates through update manager. After that the windows 7 option is missing. How do i resolve it?

- Kamalraj
```
sudo update-grub
```

---

### Post by oldfred on 2010-12-08
There have been some wubi issues lately:

how to fix those Wubi installation breakages without going crazy Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by Krytarik on 2010-12-08
There is also obviously an issue with GRUB2 and Windows 7, at one installation it wouldn't start even after I manually added a menu-entry (moved Win7 to another partition before) even after experimenting with some options, GRUB2 didn't recognize Win7 at update-grub. After downgrading to GRUB (version 1) Win7 is booting successful, however maybe you have to add a menu-entry manually, try update-grub first.

---

### Post by kamalrajonnet on 2010-12-09
Tried sudo update-grub. It found Windows 7. But while booting windows 7 is not coming.

---

### Post by bobcollard on 2010-12-09
> **kamalrajonnet said:**
> Tried sudo update-grub. It found Windows 7. But while booting windows 7 is not coming.
I assume you did reboot after that?

---

### Post by oldfred on 2010-12-09
So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Krytarik on 2010-12-09
> **kamalrajonnet said:**
> Tried sudo update-grub. It found Windows 7. But while booting windows 7 is not coming.

I've tried the Boot-Info-Script-thing also, but it didn't help at all.

Are you with GRUB2 or GRUB now?

Try adding the menu-entry manually, with GRUB put it directly in menu.lst after "END DEBIAN AUTOMAGIC KERNELS LIST" (also in /boot/grub I believe),
```
title        Windows 7 Home Premium
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```with GRUB2 put it in /etc/grub.d/40_custom and do "sudo update-grub" again:
```
menuentry "Windows 7 Home Premium" {
root        (hd0,0)
savedefault
makeactive
chainloader    +1
}
```The "root"-variable depends on the location of your Windows-partition, "hd0,0" means: first drive, first partition.

---

### Post by oldfred on 2010-12-09
Krytarik entry for grub legacy will work for sda1, but not for grub2 as partition number and style have changed.

Either of these should work, but the one with[COLOR=DarkRed] UUID[/COLOR] has to have your UUID. To see UUIDs:
sudo blkid

gksudo gedit /etc/grub.d/40_custom
```
menuentry "WinXP" {
    set root=(hd0,1)
    insmod chain
    chainloader +1 
}
```
sudo update-grub

/etc/grub.d/40_custom
```
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb5)" {
    insmod ntfs
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set [COLOR=DarkRed]4a6077fc6077ed57[/COLOR]
    drivemap -s (hd1) ${root}
    chainloader +1
}
```

You have to set your own drive & partitions. Boot script would let use give you an exact entry:

---

### Post by Krytarik on 2010-12-09
Oohps, forgot about that, sorry!
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> The first partition for GRUB 2 is **1**, not **0**. Devices still start the count at **0**.

---

### Post by kamalrajonnet on 2010-12-10
> **bobcollard said:**
> I assume you did reboot after that?

Yes I did reboot :)

---

### Post by kamalrajonnet on 2010-12-11
> **Krytarik said:**
> There is also obviously an issue with GRUB2 and Windows 7, at one installation it wouldn't start even after I manually added a menu-entry (moved Win7 to another partition before) even after experimenting with some options, GRUB2 didn't recognize Win7 at update-grub. After downgrading to GRUB (version 1) Win7 is booting successful, however maybe you have to add a menu-entry manually, try update-grub first.

My GRUB Version has shown as 1.98-1ubuntu6.

---

### Post by oldfred on 2010-12-11
Your list from update-grub showed windows. The grub boot menu has a box that shows what you can boot. Once you get a lot of lines you have to scroll down the see the ones at the bottom. Windows will be at the bottom.

You can houseclean older kernels. You have to keep current kernel and should keep one older one just in case.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Krytarik on 2010-12-11
> **kamalrajonnet said:**
> My GRUB Version has shown as 1.98-1ubuntu6.
So as mine, actually 1.98-1ubuntu9. But that's definitely GRUB2. They, for whatever reason, keep numbering the version under the actual version-title, it's kinda weird. The last version of GRUB (version 1) is numbered 0.97-29ubuntu60, it's called "grub" in the archive, whereas GRUB2 consists of "grub-pc" and "grub-common".

---

### Post by kamalrajonnet on 2010-12-11
> **oldfred said:**
> So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 296660197 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5/Wubi 
                       and looks at sector 21424016 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
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

/dev/sda1               2,048    31,264,767    31,262,720  27 Hidden HPFS/NTFS
/dev/sda2    *     31,264,768    31,469,567       204,800   7 HPFS/NTFS
/dev/sda3          31,469,568   200,073,509   168,603,942   7 HPFS/NTFS
/dev/sda4         200,073,510   625,137,344   425,063,835   f W95 Ext d (LBA)
/dev/sda5         200,073,573   369,302,219   169,228,647   7 HPFS/NTFS
/dev/sda6         369,302,283   495,107,234   125,804,952   7 HPFS/NTFS
/dev/sda7         495,107,298   625,137,344   130,030,047   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       6b609cd6-e776-401e-8468-46dc61b49609   ext4                                     
/dev/sda1        2A88FD0288FCCCF7                       ntfs       Recovery                      
/dev/sda2        5456CF0456CEE5B8                       ntfs       System Reserved               
/dev/sda3        01CB2888844B1ED0                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CB288886037D30                       ntfs       Drive for Windows Server      
/dev/sda6        01CB288888FD3530                       ntfs       Personal                      
/dev/sda7        01CB28888BE16960                       ntfs       Rajinish                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda6        /media/Personal          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 01cb288886037d30
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 01cb288886037d30
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cb288886037d30
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2a88fd0288fcccf7
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 5456cf0456cee5b8
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

============================= sda5/Wubi/etc/fstab: =============================

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

================= sda5/Wubi: Location of files loaded by Grub: =================


  10.9GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.32-25-generic
   4.3GB: boot/initrd.img-2.6.35-22-generic
   5.2GB: boot/initrd.img-2.6.35-23-generic
  11.1GB: boot/vmlinuz-2.6.32-25-generic
  11.2GB: boot/vmlinuz-2.6.35-22-generic
  11.2GB: boot/vmlinuz-2.6.35-23-generic
   5.2GB: initrd.img
   4.3GB: initrd.img.old
  11.2GB: vmlinuz
  11.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  e9 15 ea 15 eb 15 ec 15  ed 15 ee 15 ef 15 f0 15  |................|
00000010  f1 15 f2 15 f3 15 f4 15  f5 15 f6 15 f7 15 f8 15  |................|
00000020  f9 15 fa 15 fb 15 fc 15  fd 15 fe 15 ff 15 00 16  |................|
00000030  01 16 02 16 03 16 04 16  05 16 06 16 07 16 08 16  |................|
00000040  09 16 0a 16 0b 16 0c 16  0d 16 0e 16 0f 16 10 16  |................|
00000050  11 16 12 16 13 16 14 16  15 16 16 16 17 16 18 16  |................|
00000060  19 16 1a 16 1b 16 1c 16  1d 16 1e 16 1f 16 20 16  |.............. .|
00000070  21 16 22 16 23 16 24 16  25 16 26 16 27 16 28 16  |!.".#.$.%.&.'.(.|
00000080  29 16 2a 16 2b 16 2c 16  2d 16 2e 16 2f 16 30 16  |).*.+.,.-.../.0.|
00000090  31 16 32 16 33 16 34 16  35 16 36 16 37 16 38 16  |1.2.3.4.5.6.7.8.|
000000a0  39 16 3a 16 3b 16 3c 16  3d 16 3e 16 3f 16 40 16  |9.:.;.<.=.>.?.@.|
000000b0  41 16 42 16 43 16 44 16  45 16 46 16 47 16 48 16  |A.B.C.D.E.F.G.H.|
000000c0  49 16 4a 16 4b 16 4c 16  4d 16 4e 16 4f 16 50 16  |I.J.K.L.M.N.O.P.|
000000d0  51 16 52 16 53 16 54 16  55 16 56 16 57 16 58 16  |Q.R.S.T.U.V.W.X.|
000000e0  59 16 5a 16 5b 16 5c 16  5d 16 5e 16 5f 16 60 16  |Y.Z.[.\.].^._.`.|
000000f0  61 16 62 16 63 16 64 16  65 16 66 16 67 16 68 16  |a.b.c.d.e.f.g.h.|
00000100  69 16 6a 16 6b 16 6c 16  6d 16 6e 16 6f 16 70 16  |i.j.k.l.m.n.o.p.|
00000110  71 16 72 16 73 16 74 16  75 16 76 16 77 16 78 16  |q.r.s.t.u.v.w.x.|
00000120  79 16 7a 16 7b 16 7c 16  7d 16 7e 16 7f 16 80 16  |y.z.{.|.}.~.....|
00000130  81 16 82 16 83 16 84 16  85 16 86 16 87 16 88 16  |................|
00000140  89 16 8a 16 8b 16 8c 16  8d 16 8e 16 8f 16 90 16  |................|
00000150  91 16 92 16 93 16 94 16  95 16 96 16 97 16 98 16  |................|
00000160  99 16 9a 16 9b 16 9c 16  9d 16 9e 16 9f 16 a0 16  |................|
00000170  a1 16 a2 16 a3 16 a4 16  a5 16 a6 16 a7 16 a8 16  |................|
00000180  a9 16 aa 16 ab 16 ac 16  ad 16 ae 16 af 16 b0 16  |................|
00000190  b1 16 b2 16 b3 16 b4 16  b5 16 b6 16 b7 16 b8 16  |................|
000001a0  b9 16 ba 16 bb 16 bc 16  bd 16 be 16 bf 16 c0 16  |................|
000001b0  c1 16 c2 16 c3 16 c4 16  c5 16 c6 16 c7 16 00 fe  |................|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 67 39 16 0a 00 fe  |......?...g9....|
000001d0  ff ff 05 fe ff ff a6 39  16 0a d7 a1 7f 07 00 00  |.......9........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-12-11
You have just wubi. You should not be installing grub2 at all. It has a grub2 boot as part of wubi but it is not installed to a MBR or partition boot sector. Installing to NTFS partitions messes up windows.

You should get a windows boot that lets you choose windows or Ubuntu. Then you get the standard grub2 menu that lets you boot Ubuntu, whether it has windows or not should not matter as you boot windows from the windows boot loader.

What does not work?

---

### Post by kamalrajonnet on 2010-12-11
> **oldfred said:**
> You have just wubi. You should not be installing grub2 at all. It has a grub2 boot as part of wubi but it is not installed to a MBR or partition boot sector. Installing to NTFS partitions messes up windows.

You should get a windows boot that lets you choose windows or Ubuntu. Then you get the standard grub2 menu that lets you boot Ubuntu, whether it has windows or not should not matter as you boot windows from the windows boot loader.

What does not work?

As I told in my initial message, I have wubi. I am getting the windows boot menu first to choose between windows 7 and ubuntu. Once I choose ubuntu, the grub boot menu pops up. In this grub menu I used to get the option for windows 7. But its missing now. i.e. I dont have a option to go back to windows once I booted to ubuntu.

[ATTACH]178094[/ATTACH]

---

### Post by Krytarik on 2010-12-11
> **kamalrajonnet said:**
> As I told in my initial message, I have wubi. I am getting the windows boot menu first to choose between windows 7 and ubuntu. Once I choose ubuntu, the grub boot menu pops up. In this grub menu I used to get the option for windows 7. But its missing now. i.e. I dont have a option to go back to windows once I booted to ubuntu.

[ATTACH]178094[/ATTACH]
Then you want to have two times the choice between Ubuntu and Windows? Is the first still working?

EDIT: Sorry, I didn't know about the submenu-way wubi installs Ubuntu until now.

---

### Post by kamalrajonnet on 2010-12-11
> **Krytarik said:**
> Then you want to have two times the choice between Ubuntu and Windows? Is the first still working?

EDIT: Sorry, I didn't know about the submenu-way wubi installs Ubuntu until now.

Yes The first menu (windows boot manager) works fine. It gives windows 7 and as well ubuntu option. Once I selected ubuntu, the GRUB comes in to picture. But it is not providing the option to load windows 7 once again.

This is something that was working fine before I installed some updates through update manger.

All I wanted to know is why it disappeared now? Is it possible to get it again?

---

### Post by Krytarik on 2010-12-11
Personally I'd leave it as it is, because you risk loosing your Windows-boot-menu.
Nevertheless my advice is still true, but you have to be CAREFUL on which disk/partition you install the grub-bootloader!

manual of version 0.97: [http://www.gnu.org/software/grub/grub-legacy-support.en.html](http://www.gnu.org/software/grub/grub-legacy-support.en.html)

---

### Post by kamalrajonnet on 2010-12-12
> **Krytarik said:**
> Personally I'd leave it as it is, because you risk loosing your Windows-boot-menu.
Nevertheless my advice is still true, but you have to be CAREFUL on which disk/partition you install the grub-bootloader!

manual of version 0.97: [http://www.gnu.org/software/grub/grub-legacy-support.en.html](http://www.gnu.org/software/grub/grub-legacy-support.en.html)

Ok. I will leave it as it is. Thanks for your all suggestions and ideas.

---

