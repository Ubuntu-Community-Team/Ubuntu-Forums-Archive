---
title: "Grub 2 Problems"
date: 2010-02-18
forum: Desktop Environments
---

### Post by sphariss on 2010-02-18
I have installed Ubuntu 9.10 which loads grub 2 by default.  My system is basically running fine with Windows 7, XP, and Ubuntu 9.10 (with several kernel updates) all showing in the grub boot menu.  The problem is with Centos 5.4 which is the last OS I loaded.  It does not show up in the grub boot menu.
 
the centos partition is bootable (tested by actually booting from that drive via bios)

I have added the needed code to 40_custom (and also changing the priority by renaming to 15_custom):

 #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the ‘exec tail’ line above.
menuentry “CentOS 5.4&#8243; {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
     insmod ext3
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 1d755bf6-b132-44c8-80f6-75f5d8cf5d76
    linux /vmlinuz-2.6.18-164.el5xen root=UUID=1d755bf6-b132-44c8-80f6-75f5d8cf5d76 rhgb ro quiet
     initrd /initrd-2.6.18-164.el5xen.img
}


blkid shows the correct UUID: (/dev/sdd1 is the boot partition for centos)

/dev/sdd1: LABEL="/boot" UUID="1d755bf6-b132-44c8-80f6-75f5d8cf5d76" SEC_TYPE="ext2" TYPE="ext3" 
 /dev/sdd2: UUID="y3FJeW-Dvic-kPaD-h0cw-70y3-HK3Q-kkQKN8" TYPE="LVM2_member" 


update-grub appears to find Centos :

Generating grub.cfg ...
Found Debian background: Windbuchencom.tga
 Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
 Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
 Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdc1
 **Found CentOS release 5.4 (Final) on /dev/mapper/VolGroup00-****LogVol02  **(interesting that it is finding the LVM instead of /boot)
done


And lastly, /boot/grub/grub.cfg has found and added Centos to the menu. (excerpt from file showing relevant section, I tried to run it as 15_custom as well... neither worked):
 
### BEGIN /etc/grub.d/15_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the ‘exec tail’ line above.
menuentry “CentOS 5.4&#8243; {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext3
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 1d755bf6-b132-44c8-80f6-75f5d8cf5d76
     linux /vmlinuz-2.6.18-164.el5xen root=UUID=1d755bf6-b132-44c8-80f6-75f5d8cf5d76 rhgb ro quiet
    initrd /initrd-2.6.18-164.el5xen.img
}
### END /etc/grub.d/15_custom ###

---

### Post by meierfra. on 2010-02-18
What error message do you get when  your try to boot CentOS via your coustom entry?

> menuentry &#8220;CentOS 5.4&#8243; {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod [COLOR="Red"]ext3[/COLOR]
set root=(hd3,1)
search --no-floppy --fs-uuid --set 1d755bf6-b132-44c8-80f6-75f5d8cf5d76
linux /vmlinuz-2.6.18-164.el5xen root=[COLOR="Red"]UUID=1d755bf6-b132-44c8-80f6-75f5d8cf5d76[/COLOR] rhgb ro quiet
initrd /initrd-2.6.18-164.el5xen.img

Grub use ext2.mod for ext2, ext3 and ext4.  So it should be

"insmod ext2"

Also the "root" statement in the linux line needs to refer to "/" partition and not the "/boot" partition. So try

root=/dev/mapper/VolGroup00-LogVol02

You might also use "insmod lvm", but since  you boot partition  is ext3 that should not be necesssary:

```
menuentry &#8220;CentOS 5.4&#8243; {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod [COLOR="Red"]ext2
insmod  lvm[/COLOR]
set root=(hd3,1)
search --no-floppy --fs-uuid --set 1d755bf6-b132-44c8-80f6-75f5d8cf5d76
linux /vmlinuz-2.6.18-164.el5xen root=[COLOR="Red"]/dev/mapper/VolGroup00-LogVol02[/COLOR] rhgb ro quiet
initrd /initrd-2.6.18-164.el5xen.img

```

Disclaimer: I have no experience booting CentOS, so I have no idea whether this menuentry will work.

---

### Post by sphariss on 2010-02-18
hmmm still not working.... No errors as I am not even able to choose the centos entry.  It does not even show up on the boot menu, but it IS listed in /boot/grub/grub.cfg

```
menuentry “CentOS 5.4&#8243; {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    insmod lvm
    search --no-floppy --fs-uuid --set 1d755bf6-b132-44c8-80f6-75f5d8cf5d76
    linux /vmlinuz-2.6.18-164.el5xen root=/dev/mapper/VolGroup00-LogVol02 rhgb ro quiet
    initrd /initrd-2.6.18-164.el5xen.img
}

```I have tried with and without the insmod lvm line.  is there a log file for grub2 that might show what is happening?

This is the partition info (I have also tried set root=(hd3,0) with no joy.) :
```
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082e93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          33      265041   83  Linux
/dev/sdd2              34        6407    51199155   8e  Linux LVM

```

---

### Post by meierfra. on 2010-02-19
Lets check out your system:
Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

### Post by sphariss on 2010-02-21
I have ran the bootinfo script and here are the results.  I have also reloaded centos 5.4 so the UUID for /boot has changed from my original post.

```
                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=5c0cfa32-8922-4c2e-ad58-db410e460028)/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

VolGroup01-LogVol00: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.4 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

VolGroup01-LogVol01: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e3f324

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   586,070,015   585,863,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031917

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       481,949       481,887  83 Linux
/dev/sdb2             481,950   582,163,469   581,681,520   5 Extended
/dev/sdb5             482,013   582,163,469   581,681,457  83 Linux
/dev/sdb3         582,163,470   586,067,264     3,903,795  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x431c431b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   716,804,234   716,804,172   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00082e93

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63       530,144       530,082  83 Linux
/dev/sdd2             530,145 1,953,520,064 1,952,989,920  8e Linux LVM


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81fc8e12

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sde2         204,796,620   586,067,264   381,270,645   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/VolGroup01-LogVol00 d4795427-4645-4813-9989-1d4bf1143d3b   ext3                                     
/dev/mapper/VolGroup01-LogVol01                                        swap                                     
/dev/sda1        CA38D18738D17345                       ntfs       System Reserved               
/dev/sda2        60E4D695E4D66CB2                       ntfs       win7_010109                   
/dev/sdb1        5c0cfa32-8922-4c2e-ad58-db410e460028   ext2                                     
/dev/sdb3        307e708b-2a66-477a-b4c9-3fec2d36ef7f   swap                                     
/dev/sdb5        30e2bf3d-4b9f-45da-bd4a-120e411ebaec   ext4                                     
/dev/sdc1        EAD028D6D028AAB1                       ntfs       old_xp                        
/dev/sdd1        f90eb909-dad1-48f8-afdd-a1e24bf6f72c   ext3       /boot                         
/dev/sdd2        WfLyie-vBXn-vf3x-WlVA-Tjct-1YM9-Bg2k2l LVM2_member                               
/dev/sde1        380C0EAD0C0E666A                       ntfs       PesoPalo                      
/dev/sde2        DA60BD2760BD0AF1                       ntfs       Media                         

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
VolGroup01-LogVol00
VolGroup01-LogVol01

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /boot                    ext2       (rw)
/dev/sde1        /media/PesoPalo          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde2        /media/Media             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


============================= sdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 30e2bf3d-4b9f-45da-bd4a-120e411ebaec
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 30e2bf3d-4b9f-45da-bd4a-120e411ebaec
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5c0cfa32-8922-4c2e-ad58-db410e460028
    linux    /vmlinuz-2.6.31-19-generic root=UUID=30e2bf3d-4b9f-45da-bd4a-120e411ebaec ro   quiet splash
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5c0cfa32-8922-4c2e-ad58-db410e460028
    linux    /vmlinuz-2.6.31-19-generic root=UUID=30e2bf3d-4b9f-45da-bd4a-120e411ebaec ro single 
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5c0cfa32-8922-4c2e-ad58-db410e460028
    linux    /vmlinuz-2.6.31-17-generic root=UUID=30e2bf3d-4b9f-45da-bd4a-120e411ebaec ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5c0cfa32-8922-4c2e-ad58-db410e460028
    linux    /vmlinuz-2.6.31-17-generic root=UUID=30e2bf3d-4b9f-45da-bd4a-120e411ebaec ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/15_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the ‘exec tail’ line above.
menuentry “CentOS 5.4&#8243; {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,1)
    insmod lvm
    search --no-floppy --fs-uuid --set f90eb909-dad1-48f8-afdd-a1e24bf6f72c
    linux /vmlinuz-2.6.18-164.el5xen root=/dev/mapper/VolGroup01-LogVol00 rhgb ro quiet
    initrd /initrd-2.6.18-164.el5xen.img
}
### END /etc/grub.d/15_custom ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ca38d18738d17345
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set ead028d6d028aab1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-17-generic
    .1GB: initrd.img-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-19-generic

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=30e2bf3d-4b9f-45da-bd4a-120e411ebaec /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=5c0cfa32-8922-4c2e-ad58-db410e460028 /boot           ext2    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=307e708b-2a66-477a-b4c9-3fec2d36ef7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .4GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .3GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

=================== sdd1: Location of files loaded by Grub: ===================


    .0GB: initrd-2.6.18-164.el5xen.img
    .0GB: vmlinuz-2.6.18-164.el5xen

======================== VolGroup01-LogVol00/etc/fstab: ========================

/dev/VolGroup01/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb3               swap                    swap    defaults        0 0
/dev/VolGroup01/LogVol01 swap                    swap    defaults        0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on VolGroup01-LogVol01

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200

```

---

### Post by meierfra. on 2010-02-21
```
"Ubuntu, Linux 2.6.31-19-generic (recovery mode)" 
“CentOS 5.4&#8243; 
```

I hadn't noticed this before, but if you looks closely, you will notice that the quotient marks used in the  "Ubuntu" entry are  different than  the  ones in “CentOS 5.4&#8243;  entry.  Maybe that's the reason CentOS does not show up on the Grub menu.

---

