---
title: "GRUB2 loading then crash"
date: 2009-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EvansFive on 2009-11-28
Since moving to GRUB2 on dual boot (Windows 7/ Ubuntu 9.10) every few restarts or cold boots I get:

GRUB LOADING

then **nothing** for a while then the **PC shuts down**!

Then at other times the GRUB2 menu appears and I can select either Ubuntu or Windows 7 to boot.  **The time to display the menu is much longer than for GRUB as well!**

I have done a:

update_grub2

but the problem remains.

Anybody please now how to fix this booting problem with GRUB2?

---

### Post by Mka on 2010-01-29
I am "dualbooting" Windows XP and Ubuntu 9.10 (karmic) and I have Grub2 on the MBR. Ubuntu is on an ext4 partition. If I boot to windows, I work just fine until I shutdown. After booting again from a previous shutdown from windows, Grub2 is broken ... all I get is a sible line like **GRUB Loading** and then nothing will ever happen no matter how long I wait.

As a remedy, I put my liveCD and recover grub by 'grub-install' but the same problem will occur once I boot Windows again.

Here is my disk structure:
```
mkanyicy@karmic:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4843    38901366    7  HPFS/NTFS
/dev/sda2           11315       12161     6796408+   c  W95 FAT32 (LBA)
/dev/sda3            8872       11315    19623366+   5  Extended
/dev/sda4   *        4844        6801    15727635   83  Linux
/dev/sda5            8872        9370     4000153+  82  Linux swap / Solaris
/dev/sda6            9370       11315    15623181   83  Linux

Partition table entries are not in disk order
```

Here is the breakdown of partitions:

sda1 = Windows XP
sda2 = Windows Laptop Recovery Partition
sda4 = Ubuntu 9.10 - Karmic Koala
sda5 = Swap
sda6 = Debian 5.0 - Lenny

Thanks

---

### Post by drs305 on 2010-01-29
Mka,

If you run the boot info script from this link we will have a good picture of your system. Please place the output between 'code' tags by using the # menu icon as described in the link.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by oldfred on 2010-01-29
I have saved a few of the comments of users with similar issues. Are you running any of these applications?

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.

---

### Post by Mka on 2010-02-01
Hi guys.

I was away on weekend with not internet access. Here is the output of the script that drs305 gave me.

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /linux.bin looks at sector 179021253 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    77,802,794    77,802,732   7 HPFS/NTFS
/dev/sda2         181,772,703   195,365,519    13,592,817   c W95 FAT32 (LBA)
/dev/sda3         142,525,970   181,772,702    39,246,733   5 Extended
/dev/sda5         142,525,971   150,526,277     8,000,307  82 Linux swap / Solaris
/dev/sda6         150,526,341   181,772,702    31,246,362  83 Linux
/dev/sda4    *     77,802,795   109,258,064    31,455,270  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BE44CA9244CA4CB9                       ntfs       WINDOWS                       
/dev/sda2        6D10-3A8B                              vfat       HP_RECOVERY                   
/dev/sda4        f180bd16-a659-4456-b4e9-d73a4a819854   ext4       KARMIC                        
/dev/sda5                                               swap                                     
/dev/sda6        93dcb2f3-f4a2-4592-8635-5d3aa1352cce   ext3       LENNY                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\linux.bin="Ubuntu Linux"


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda6/boot/grub/menu.lst: ===========================

default		0
timeout		10

title		Debian 5.0 - Lenny
root		(hd0,5)
kernel		/vmlinuz root=/dev/sda6 ro quiet splash
initrd		/initrd.img

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP System Recovery Drive
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.10 - Karmic Koala
root		(hd0,3)
savedefault
makeactive
chainloader	+1

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda6: Location of files loaded by Grub: ===================


  77.0GB: boot/grub/menu.lst
  77.0GB: boot/grub/stage2
  77.0GB: boot/initrd.img-2.6.26-2-686
  77.0GB: boot/initrd.img-2.6.26-2-686.bak
  77.0GB: boot/vmlinuz-2.6.26-2-686
  77.0GB: initrd.img
  77.0GB: vmlinuz

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set f180bd16-a659-4456-b4e9-d73a4a819854
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
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set f180bd16-a659-4456-b4e9-d73a4a819854
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f180bd16-a659-4456-b4e9-d73a4a819854 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set f180bd16-a659-4456-b4e9-d73a4a819854
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f180bd16-a659-4456-b4e9-d73a4a819854 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set be44ca9244ca4cb9
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 6d10-3a8b
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Debian 5.0 - Lenny (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 93dcb2f3-f4a2-4592-8635-5d3aa1352cce
	linux /vmlinuz root=/dev/sda6 ro quiet splash
	initrd /initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=f180bd16-a659-4456-b4e9-d73a4a819854 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

oldfred: My machine is an HP Compaq nx7400 laptop and it has a recovery partition. Last time it was a windows bootloader at the MBR and I used 'boot.ini' to chainload to GRUB. Now I dont know how to place it back nor having a Windows install CD.

Thanks a lot guys.

Mka

---

### Post by oldfred on 2010-02-01
I do not see anything in your boot script that looks wrong, maybe someone else will. 

I am still suspicious  of HP other software in windows messing with the MBR. If you can not find what it is, some have reverted to grub legacy or easyBCD. I do not normally recommend either and do not know easyBCD other than it uses windows to boot.

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by drs305 on 2010-02-01
I think oldfred is on the right track about something on Windows writing to the MBR. 

Meierfra has a good page on trying to resolve this issue:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")

Also, can you be more specific on how long "much longer" is for the Grub menu to display?

---

### Post by Mka on 2010-02-02
oldfred and drs305, thank you very much for your patience and support. I will clone the windows partitions and write them to dvd and then try removing the HP latop extras as suggested probably during weekend. 

To answer you, drs305, if you wait for 'Grub Loading', you wait forever, the menu just never comes. Now I always have a karmic LiveCD at the pocket of the laptop bag just in case i boot to windows (which i'ven't been keen to do as of late).

Cheers
Mka

---

