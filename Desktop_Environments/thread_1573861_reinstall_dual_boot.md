---
title: "reinstall dual boot"
date: 2010-09-13
forum: Desktop Environments
---

### Post by mersey on 2010-09-13
Hi,

Several months ago I installed Ubuntu (9.1) as dual boot with Windows XP. Then Windows crashed and I had to re-install windows. This meant I lost the dual boot start up options.

I would like to re-set this up. I assume it's just a matter of re-setting up the dual boot option in Windows. But how do I do this?

Thanks

---

### Post by claracc on 2010-09-13
This document [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) can help you.

---

### Post by oldfred on 2010-09-13
If it was a wubi install and not in another partition it is gone. If a full install in separate partitions, you just need to reinstall grub legacy or grub2 depending on version and if a newer version of Ubuntu whether you upgraded or did new install. 

If you know which grub to install - same instructions worded slightly differently:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by mersey on 2010-09-13
Thanks for the quick response. I'll have a look at the links and give it a try.

---

### Post by mersey on 2010-09-13
> **oldfred said:**
> If it was a wubi install and not in another partition it is gone. If a full install in separate partitions, you just need to reinstall grub legacy or grub2 depending on version and if a newer version of Ubuntu whether you upgraded or did new install. 

If you know which grub to install - same instructions worded slightly differently:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Hi,

claracc's option seemed far to complicated for me to understand so, as it was a full Ubuntu install into a seperate partition, I went for this one
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I did as it said for Ubuntu.
It left me with the bootloader coiming up but the XP selection didn't work so I went to section 3 for updating XP

After booting from the original Windows CD & putting in "r" for recovery console it asked the question
Which Windows installation would you like to log onto?

After figuring out that the answer was "1" I was then asked for, and gave, the Administrator password.

It then said:
The target partition is C:
Are you sure you want to write a new bootsector to the partition c ?

At this point I chickened out. Do I want to answer Yes to that?

Is this going to work?

---

### Post by wilee-nilee on 2010-09-13
Post the bootscript in my signature in code tags as described if you can. The text from the script will give us all the what and where things are better. I would follow oldfred they know whats up, and the script will make it easier in general.

As far as using the MS cd to reload the MS bootloader you hit the r for repair choose the command terminal and run fixmbr. here is a instructional link.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

I would just stop and post that script using a live Ubuntu cd and we will watch out for your posts.

---

### Post by mersey on 2010-09-13
HI,

I'm struggling to follow all this. I hope this is right.
For info I have two NTFS partitions. In Windows the first one comes up as drive C and contains programs etc. The second comes up as drive D and contains all my data.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39d039d0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,850,249    61,850,187   7 HPFS/NTFS
/dev/sda2          61,850,250   249,441,254   187,591,005   7 HPFS/NTFS
/dev/sda3         249,441,255   312,576,704    63,135,450   5 Extended
/dev/sda5         249,441,318   309,877,784    60,436,467  83 Linux
/dev/sda6         309,877,848   312,576,704     2,698,857  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        72B09952B0991E23                       ntfs                                     
/dev/sda2        01C8E432A226AB00                       ntfs                                     
/dev/sda5        8169021e-1b64-4343-8877-16604425e63e   ext4                                     
/dev/sda6        c47ca825-a9f4-4b2e-ac63-ec09ad3b63af   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/01C8E432A226AB00  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/72B09952B0991E23  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="6"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 8169021e-1b64-4343-8877-16604425e63e
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8169021e-1b64-4343-8877-16604425e63e
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8169021e-1b64-4343-8877-16604425e63e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8169021e-1b64-4343-8877-16604425e63e
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=8169021e-1b64-4343-8877-16604425e63e ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8169021e-1b64-4343-8877-16604425e63e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8169021e-1b64-4343-8877-16604425e63e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8169021e-1b64-4343-8877-16604425e63e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8169021e-1b64-4343-8877-16604425e63e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ba94af4a94af07c9
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8169021e-1b64-4343-8877-16604425e63e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c47ca825-a9f4-4b2e-ac63-ec09ad3b63af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/core.img
 128.6GB: boot/grub/grub.cfg
 128.3GB: boot/initrd.img-2.6.31-14-generic
 128.6GB: boot/initrd.img-2.6.31-16-generic
 128.3GB: boot/vmlinuz-2.6.31-14-generic
 128.3GB: boot/vmlinuz-2.6.31-16-generic
 128.6GB: initrd.img
 128.3GB: initrd.img.old
 128.3GB: vmlinuz
 128.3GB: vmlinuz.old
```P.S. don't need to boot from live Ubuntu CD as I can boot into Ubuntu, just not Windows XP

---

### Post by wilee-nilee on 2010-09-13
> **mersey said:**
> Hi,

claracc's option seemed far to complicated for me to understand so, as it was a full Ubuntu install into a seperate partition, I went for this one
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I did as it said for Ubuntu.
**It left me with the bootloader coiming up but the XP selection didn't work **

So the script looks okay, oldfred is back on line I suspect they will drop in for a spell. Sometimes it just takes a reload of grub into the mbr and having the partition=sda5 mounted to get things back in place.

I am curious when you choose XP and it doesn't load what actually happens. The highlighted section is the only real description.


Edit: It also just occurred to me that taking a look at the hard drive from gparted might also show a flag on your ntfs partition, if it does you can right click on the partition then information.

You might need to install gparted if you haven't.
```
sudo apt-get install gparted
```

---

### Post by oldfred on 2010-09-13
If Ubuntu boots then it is not a grub issue. The partition with XP per the script looks ok. Do you get an error message from windows as it looks like grub should be passing the boot to windows correctly.

The windows files look ok but this will replace them and rebuild boot.ini which also looks ok. You may want to run chkdsk first.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 


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

---

### Post by mersey on 2010-09-14
> **wilee-nilee said:**
> So the script looks okay, oldfred is back on line I suspect they will drop in for a spell. Sometimes it just takes a reload of grub into the mbr and having the partition=sda5 mounted to get things back in place.

I am curious when you choose XP and it doesn't load what actually happens. The highlighted section is the only real description.


Edit: It also just occurred to me that taking a look at the hard drive from gparted might also show a flag on your ntfs partition, if it does you can right click on the partition then information.

You might need to install gparted if you haven't.
```
sudo apt-get install gparted
```

Hi,
Perhaps I should have said more about the boot load error.

When I start up the PC I get these options

Ubuntu linux 2.6.31 - 16 generic
Ubuntu linux 2.6.31 - 16 generic recovery mode
Ubuntu linux 2.6.31 - 14 generic
Ubuntu linux 2.6.31 - 14 generic recovery mode
memory test....
memory test....
Microsoft Windows XP Home Edition (on/dev/sda1)

The Ubuntu options boot into Ubuntu but the Windows XP one then says:
error no such device = ba94af4a94af07c9
Press any key to continue

pressing any key takes me back to the boot selection.

Ref gparted - how do I run that.

Please note I know virtually nothing about Ubuntu and all these commands.

---

### Post by mersey on 2010-09-14
> **oldfred said:**
> If Ubuntu boots then it is not a grub issue. The partition with XP per the script looks ok. Do you get an error message from windows as it looks like grub should be passing the boot to windows correctly.

The windows files look ok but this will replace them and rebuild boot.ini which also looks ok. You may want to run chkdsk first.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 


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

HI,

I copied the ntdetect.com and ntldr files but that didn't help.
I went into recovery console and typed in FIXMBR and it said this:

This computer appears to have a non-standard or invalid master boot record.

FIXMBR may damage your partition tables if you proceed.

This could cause all the partitions on the current hard disc to become inaccessible

If you are not having problems accessing your drive, do not continue.

Are you sure you want to write a new MBR ?

to which I said No because it sounds pretty scary. Should I continue at that point?

Also the previous instructions for this gave the order 
FIXBOOT
FIXMBR

Whilst yours above gave
FIXMBR
FIXBOOT

Does the order matter?

Thanks

---

### Post by oldfred on 2010-09-14
Order does not matter. FixMBR will overwrite grub in the MBR and put in the windows boot loader. You can do that to test that windows boots on its own, but then you have to reinstall grub2 to the MBR.

I missed the bad partition number. But grub should have updated that with
sudo update-grub

That should change this from the incorrect UUID to the correct one.

If it does not work then we will have to manually edit 40_custom.

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=Red]ba94af4a94af07c9[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1
}

 Correct UUID per results.txt 72B09952B0991E23  

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=Red]72B09952B0991E23[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1

---

### Post by mersey on 2010-09-14
> **oldfred said:**
> Order does not matter. FixMBR will overwrite grub in the MBR and put in the windows boot loader. You can do that to test that windows boots on its own, but then you have to reinstall grub2 to the MBR.

I missed the bad partition number. But grub should have updated that with
sudo update-grub

That should change this from the incorrect UUID to the correct one.

If it does not work then we will have to manually edit 40_custom.

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=Red]ba94af4a94af07c9[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1
}

 Correct UUID per results.txt 72B09952B0991E23  

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=Red]72B09952B0991E23[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1


HI,

Ran FIXMBR and I'm now back to booting straight into Windows.
Phew!, I haven't lost anything.
On the other hand I still don't have dual boot.

Would I be better to delete the Ubuntu partition and re-install Ubuntu from scratch and let it sort out the dual boot on the way?

---

### Post by oldfred on 2010-09-14
You should be able just to reinstall grub2 to the MBR. A sudo update-grub should fix the incorrect UUID, if not we can add a corrected entry to 40_custom.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

once booted:

sudo update-grub

---

### Post by mersey on 2010-09-15
> **oldfred said:**
> You should be able just to reinstall grub2 to the MBR. A sudo update-grub should fix the incorrect UUID, if not we can add a corrected entry to 40_custom.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

once booted:

sudo update-grub

Hi,

That worked. I now have dual boot with both Windows and Ubuntu working

Many thanks for your help.

---

