---
title: "GRUB having problems with Windows 7"
date: 2010-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Blackcraft on 2010-08-27
Hi, I'm new to Linux entirely. In fact I just downloaded Ubuntu 10.4 yesterday alongside Windows 7 on my Dell Inspiron Notebook. Anyway, I managed to get the hard drive partitioned correctly and Ubuntu installed and after playing around for awhile I decided I should to switch to Windows for awhile. After restarting out of Windows to go back to Ubuntu I got this error where the GRUB menu normally comes up
```
no module name found
```so I booted up using my live cd and looked around for an answer and found somewhere that Dell programs have trouble with writing over the MBR and GRUB particularly so after 2 days of messing around I eventually just reinstalled Ubuntu. I went in and deleted all of the programs I read that might have messed with GRUB and booted up windows then restarted to see if it was fixed. I had the same error again. Some help would be welcome cuz I'm lost. If you need any info/stats that I could give just ask. Please help!

Some additional info 

I tried doing this

```
 sudo grub
grub> find /boot/grub
Error 15: File not found
```But using

```
 sudo find /boot/grub
```it works but it shows there's nothing under grub.

I tried about every varient of
```
sudo grub-install /dev/sda2
```but it tells me 
```
Could not find device for /boot: Not found or not a block device.
```This is also the result of fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       22258   163385688    7  HPFS/NTFS
/dev/sda4           22335       38914   133172963    5  Extended
/dev/sda5           22335       22589     2048224+  82  Linux swap / Solaris
/dev/sda6           22590       38914   131124224   83  Linux

```

---

### Post by wilee-nilee on 2010-08-27
Dell data safe is what we have seen on the forum.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

Here is a MS recovery disc link to reload the MBR to get into windows if needed. Also included the commands and a link to how to use it in a http address, just the highlighted command is needed.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) 

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a Grub2 link to reload it from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


Really you ought to post the bootscript in my signature in code tags as described. To make sure you have not put grub in a windows partition, and to just see what is where.

---

### Post by Blackcraft on 2010-08-27
I tried loading GRUB2 from the live disk and got the error
```
The file /mnt/boot/boot/grub/stage1 not read correctly.
```I also tried the other fixes from the same site and none of them worked

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   357,573,295   326,771,376   7 HPFS/NTFS
/dev/sda4         358,795,834   625,141,759   266,345,926   5 Extended
/dev/sda5         358,795,836   362,892,284     4,096,449  82 Linux swap / Solaris
/dev/sda6         362,893,312   625,141,759   262,248,448  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            129     3,907,007     3,906,879   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        36F8A821F8A7DD7D                       ntfs       RECOVERY                      
/dev/sda3        9414ABD814ABBB9C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2b7d8416-a227-47b8-accd-68cb035081ef   swap                                     
/dev/sda6        3c620310-5b73-4809-b2de-d460f1a68717   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        BA13-CC15                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2
    ??GB: grub/stage2

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=3c620310-5b73-4809-b2de-d460f1a68717 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=3c620310-5b73-4809-b2de-d460f1a68717 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 3c620310-5b73-4809-b2de-d460f1a68717
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2cb8b1f1b8b1b9a2
    chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 286.8GB: boot/grub/core.img
 286.8GB: boot/grub/grub.cfg
 286.8GB: boot/initrd.img-2.6.32-24-generic-pae
 286.8GB: boot/vmlinuz-2.6.32-24-generic-pae
 286.8GB: initrd.img
 286.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  cc a7 7d b6 99 cb 6e ea  79 8d b1 93 c1 ce aa f9  |..}...n.y.......|
00000010  36 d9 dc c7 73 5d ba 87  d9 f4 bf 97 2f 2d f2 ef  |6...s]....../-..|
00000020  f5 29 1b 92 bd b6 03 a4  f9 a7 7d 74 19 9b 0a ea  |.)........}t....|
00000030  64 e7 19 09 48 e3 52 43  3d f1 ea bb 80 bb aa 00  |d...H.RC=.......|
00000040  aa 93 26 2d 34 d6 e0 16  e9 b5 06 e8 86 14 33 03  |..&-4.........3.|
00000050  41 40 d8 fa 67 41 03 41  67 93 80 47 ce 42 0e 4a  |A@..gA.Ag..G.B.J|
00000060  04 20 7f 9d 4c a3 61 bd  f2 78 f5 47 6f 0d 68 29  |. ..L.a..x.Go.h)|
00000070  7b 64 2a 29 11 72 6a 14  d8 6f a3 64 1f 8d e2 5c  |{d*).rj..o.d...\|
00000080  fa ff 4d 6b d1 6a 15 14  e7 f0 c8 94 c8 f2 33 4a  |..Mk.j........3J|
00000090  e5 46 93 4b 96 d5 16 c8  59 cf fe 21 12 29 f9 cc  |.F.K....Y..!.)..|
000000a0  fa d2 19 3e 7d 4b 5d c1  3d e9 13 af 7d 29 dd 0f  |...>}K].=...})..|
000000b0  33 31 4f fc 79 8a d0 54  cc 07 bf d2 40 79 aa 2c  |31O.y..T....@y.,|
000000c0  29 22 6c bb 49 11 2f 62  aa 85 19 5f 98 d4 b2 40  |)"l.I./b..._...@|
000000d0  08 12 19 25 1e 21 2a c9  a6 35 4a 56 df 66 af 15  |...%.!*..5JV.f..|
000000e0  d8 ad 28 64 ea 72 c5 bd  e5 42 3f 23 0c f3 f5 4b  |..(d.r...B?#...K|
000000f0  d9 aa ee 8d 67 fe 74 ec  cb ab 51 e8 ee 65 9d f6  |....g.t...Q..e..|
00000100  a9 d1 93 77 dc e8 9a 73  22 db 47 4b 58 5a 12 f6  |...w...s".GKXZ..|
00000110  74 42 72 b8 85 21 48 cb  44 56 2a ba b8 a7 a4 00  |tBr..!H.DV*.....|
00000120  59 13 54 ca 60 d8 3c f8  60 a4 67 79 08 8e 41 d8  |Y.T.`.<.`.gy..A.|
00000130  0a 7c bb 71 f0 36 17 92  b7 32 34 e0 53 82 20 8e  |.|.q.6...24.S. .|
00000140  03 25 71 0c 2a b3 69 22  a2 a0 88 5c ea f8 9f a9  |.%q.*.i"...\....|
00000150  49 5e 96 92 3d 31 9e b7  11 bd ac e5 f5 a9 77 fa  |I^..=1........w.|
00000160  16 90 db 36 3a 7b 92 19  99 f9 f4 d8 8b 6d 6e 56  |...6:{.......mnV|
00000170  6b db 6c ff ba 96 73 5b  f9 e4 46 7b 29 e6 df 69  |k.l...s[..F{)..i|
00000180  52 cf 3f 3c 44 02 d8 6e  77 22 74 72 d2 e0 fd 3f  |R.?<D..nw"tr...?|
00000190  e8 7f fe ff 00 0b b2 ff  fb a4 60 ac 00 03 ce 55  |..........`....U|
000001a0  d2 93 4f 1b 72 66 0b 7a  82 61 22 6e 0e b9 23 48  |..O.rf.z.a"n..#H|
000001b0  4c e0 6b c9 91 26 6a 8d  83 8d 79 c9 17 ea 00 fe  |L.k..&j...y.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 c1 81 3e 00 00 fe  |............>...|
000001d0  ff ff 05 fe ff ff c3 81  3e 00 03 9c a1 0f 00 00  |........>.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by wilee-nilee on 2010-08-28
So lets get more information as the script looks as it should boot either OS. Did you remove dell data safe or does this sound familiar in your file removal to fix this. Can you be a little more specific in this area.

---

### Post by Blackcraft on 2010-08-28
Aha! I managed to fix it, I followed the link to sevenforums.com and followed the instructions and managed to boot into windows 7 and found a datasafe file that was tucked away at the bottom of the list. I deleted it, reinstalled Ubuntu and added Windows 7 back into my grub.cfg. Thanks for the help! :D

---

### Post by wilee-nilee on 2010-08-28
> **Blackcraft said:**
> Aha! I managed to fix it, I followed the link to sevenforums.com and followed the instructions and managed to boot into windows 7 and found a datasafe file that was tucked away at the bottom of the list. I deleted it, reinstalled Ubuntu and added Windows 7 back into my grub.cfg. Thanks for the help! :D

Excellent work I was hoping you would get that removed, and grub reloaded.

---

### Post by novazol on 2010-08-29
Hi all, 

I am entirely new to linux. I had this same problem while installing Ubuntu in my Dell with preinstalled Windows 7. Thankfully this thread helped me to fix it. 

Accidentally I managed to fix it w/o removing dell data safe. Here is How :
During the first bootup using Grub I selected Windows 7 and there I downloaded a program called EasyBCD.exe. After its Installation i added ubuntu as the secondary load option there.

Next I restarted and Grub crashed. I had to put in the live usb again to reinstall grub and during the next restart I selected windows 7 (again :) ) .....there during the windows boot loader selection screen with the win 7 highlighted i pressed F8 to launch the system repair and followed the steps @ wilee-nilee. 

Its now working fine with the boot being primarily done by windows boot loader. If i select ubuntu there grub launches and the system is fine as long as i dont select windows 7 from grub.

- all these were the ramblings of a new linux user not ready to let go of windows yet and I hope maybe this will help ( :O ) some other person like me.


But of course the best way seems to be uninstalling the dell data safe backup

Thanks
wilee-nilee

---

