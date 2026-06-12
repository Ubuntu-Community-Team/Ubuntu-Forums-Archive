---
title: "Fix GRUB from liveCd won't work! :("
date: 2010-05-23
forum: Desktop Environments
---

### Post by lancelot69fr on 2010-05-23
Hi,

I have a Windows / Ubuntu dual boot system and I recently upgraded my system to 10.04 from the package manager.
I ran into what seem to be not an unusual issue with the new version of GRUB2 being installed hosing up the MBR. When I try to boot now I get a message stating: [B]the symbol 'grub_puts_' not found.
[/B]
There are a few posts and solutions out there about the issue... but the most promising ones, using the Ubuntu 10.04 liveCD don't work for me. 

The GRUB changes don't seem to stick. It's almost like I'm doing all the grub command line work in a virtual system that gets wiped out as soon as I reboot. 

For reference, here is one of the posts I've been working w/, some links in there seemed very promising, but again nothing seem to stick for me from the liveCD:

[http://ubuntuforums.org/showthread.php?t=1397629](http://ubuntuforums.org/showthread.php?t=1397629)

Should I be using some rescue disk of some sort? Or is there a way to boot directly to a command line from the Ubuntu CD menu?

Please help!!!

---

### Post by emma00 on 2010-05-23
you should post this problem in this post



[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wilee-nilee on 2010-05-23
You might consider posting this boot script, it will show what exactly is going on post it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have yet to see a boot problem that can't be traced to user error in putting grub in the wrong places. I have seen one where it appeared to be a HP setup problem but it was compounded by grub being put in the windows boot partition.

---

### Post by lancelot69fr on 2010-05-23
[QUOTE=wilee-nilee]You might consider posting this boot script, it will show what exactly  is going on post it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have yet to see a boot problem that can't be traced to user error in  putting grub in the wrong places. I have seen one where it appeared to  be a HP setup problem but it was compounded by grub being put in the  windows boot partition.     [/QUOTE]I attached the RESULTS.txt file. Not sure what I'm looking at here. :confused:

---

### Post by lancelot69fr on 2010-05-23
[QUOTE=emma00]you should post this problem in this post
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)[/QUOTE]I tried the steps for: 

[SIZE=3][COLOR=red]How to restore the Ubuntu grub  bootloader (9.10 and beyond)[/COLOR][/SIZE]

But no success. When I restarted, same error message.

---

### Post by wilee-nilee on 2010-05-23
I hope you don' mind but I am posting the script so it is easily accessible.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for 
    (UUID=11a86201-2485-4d78-a1cb-7178b04190a6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   937,167,839   937,167,777  83 Linux
/dev/sda2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sda5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   210,547,889   210,547,827   7 HPFS/NTFS
/dev/sdb2         210,547,890   420,340,724   209,792,835   7 HPFS/NTFS
/dev/sdb3         420,340,725   625,137,344   204,796,620   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        11a86201-2485-4d78-a1cb-7178b04190a6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        16ddb2f0-b982-4393-8995-5ecb4bfc5333   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C4E83A99E83A89A6                       ntfs       first                         
/dev/sdb2        389852F19852AD5E                       ntfs       second                        
/dev/sdb3        68745FC4745F93A2                       ntfs       third                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5EC07E68C07E45F5                       ntfs       primary                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=11a86201-2485-4d78-a1cb-7178b04190a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=11a86201-2485-4d78-a1cb-7178b04190a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=11a86201-2485-4d78-a1cb-7178b04190a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=11a86201-2485-4d78-a1cb-7178b04190a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 11a86201-2485-4d78-a1cb-7178b04190a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 5ec07e68c07e45f5
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=11a86201-2485-4d78-a1cb-7178b04190a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=16ddb2f0-b982-4393-8995-5ecb4bfc5333 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
  81.1GB: boot/initrd.img-2.6.31-21-generic
  81.2GB: boot/initrd.img-2.6.32-22-generic
  49.4GB: boot/vmlinuz-2.6.31-21-generic
   2.3GB: boot/vmlinuz-2.6.32-22-generic
  81.2GB: initrd.img
  81.1GB: initrd.img.old
   2.3GB: vmlinuz
  49.4GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

```

---

### Post by lancelot69fr on 2010-05-23
[QUOTE=wilee-nilee]I hope you don' mind but I am posting the script so it is easily  accessible.[/QUOTE]Doesn't like anything can uniquely identify my computer in that file... so that's all good. :)
I posted it in the first place. 

Thanks wilee-nilee

---

### Post by wilee-nilee on 2010-05-23
I think your in okay shape for a fairly easy fix. I see grub loaded in 3 different MBR's sda/sdb/sdc, but not in any partition's. If it was me I would Pop the live cd in go to gparted and put the boot flag on sda1 and make sure it is the 1st in the bios to be read, and maybe sdc second before sdb. This is only a idea, and will not damage anything. The sdc HD has the XP boot.ini in it for the XP boot. What is in the sdb hard drive I am curious?

A more experienced adviser is needed though to get you back in shape I think, but you are in good shape in that as I suggested I don't see grub in the XP boot, just the mbr of sdc. It may be as simple as setting the boot to sda1 and maybe reloading the XP bootloader in sdc, but lets wait for the people who wear the fix-it capes, they are my heroes.

Am I correct that you have XP and do you have a XP ISO or install disc, if not you probably should get one in that, it will help you maybe now or in the future.

---

### Post by lancelot69fr on 2010-05-23
[QUOTE=wilee-nilee]Am I correct that you have XP and do you have a XP ISO or install disc,  if not you probably should get one in that, it will help you maybe now  or in the future.     [/QUOTE]Yes I have the XP cd that's not an issue.

[QUOTE=wilee-nilee]What is in the sdb hard drive I am curious?[/QUOTE]I only have 2 physical HDDs. One for Windows and one for Linux. However the Windows HDD has multiple 3 logical partitions for ease of maintenance. NFTS is not up to par vs. EXT3/4 Linux FS. But that's an entire other story. 

So it looks like sda is my Linux drive and sdc is my Windows drive w/ all the sdb partitions being my logical Windows partitions. 

[QUOTE=wilee-nilee]If it was me I would Pop the live cd in go to gparted and put the boot  flag on sda1 and make sure it is the 1st in the bios to be read, and  maybe sdc second before sdb.[/QUOTE]I tried to select "install xubuntu" and follow the process until the partitioner part, but then when I select, can't remember if it's "advanced" or "manual" partitioning, anyway the one that let's you take care of the partitioning, I couldn't find where I set the boot flag and most important where the option is to NOT format the drives.

---

### Post by wilee-nilee on 2010-05-23
> **lancelot69fr said:**
> Yes I have the XP cd that's not an issue.



I only have 2 physical HDDs. One for Windows and one for Linux. However the Windows HDD has multiple 3 logical partitions for ease of maintenance. NFTS is not up to par vs. EXT3/4 Linux FS. But that's an entire other story. 

So it looks like sda is my Linux drive and sdc is my Windows drive w/ all the sdb partitions being my logical Windows partitions. 

[QUOTE]If it was me I would Pop the live cd in go to gparted and put the boot  flag on sda1 and make sure it is the 1st in the bios to be read, and  maybe sdc second before sdb./QUOTE]

I tried to select "install xubuntu" and follow the process until the partitioner part, but then when I select, can't remember if it's "advanced" or "manual" partitioning, anyway the one that let's you take care of the partitioning, I couldn't find where I set the boot flag and most important where the option is to NOT format the drives.

You don't want to run the installer again if that's what I'm seeing. Go to system>administration and open gparted right click on the sda1 partition then manage flags and click on boot. Then go to the bios and set sdc as the second in line in the boot list, boot into Xubuntu and run ```
sudo update-grub
``` in the terminal This should set grub to read the XP partition and add it to the grub list. Like I said I'm not sure if maybe the XP bootloader needs to be in the MBR of sdc for this to work though. Lets see if this works before messing with the MBR anymore.

I think what is throwing off the XP boot is having the logical partitions in between sdc and sda, as it is now the computer boots off of sdc probably, finds Xubuntu but can't get back to the sdc for boot.

---

### Post by darkod on 2010-05-23
@lancelot
Do you still have problems booting?

And I hate to ask such a dumb question, but are you SURE you have only two disks???

This shows clearly three disks detected, also the partitions have different UUIDs and even different labels that you have set:

```
Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        11a86201-2485-4d78-a1cb-7178b04190a6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        16ddb2f0-b982-4393-8995-5ecb4bfc5333   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C4E83A99E83A89A6                       ntfs       first                         
/dev/sdb2        389852F19852AD5E                       ntfs       second                        
/dev/sdb3        68745FC4745F93A2                       ntfs       third                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5EC07E68C07E45F5                       ntfs       primary                       
/dev/sdc: PTTYPE="dos"
```

It would be an extremely big bug in the script to report two disks like this.

And if you still have problems booting, there are few things I would like you to try.

---

### Post by oldfred on 2010-05-23
The script says you have a 320 and two 500GB drives? Were you sold a 1000GB but it happens to be two 500's?

Are you booting from sda the 320GB drive? Check in BIOS and see what drives BIOS sees and set the 320 to boot.

---

