---
title: "Grub Error 22"
date: 2009-01-31
forum: General Help
---

### Post by xCel on 2009-01-31
I have searched and read quite a few posts about the Grub error 22....but, I am still stuck. :(

I was running Win XP, and decided to make a partition to install Ubuntu... well, I installed in the partition and now I reboot and it comes up with the Grub error 22. 

At this point, I would just like to load windows so I can redo my partition and start over. 

I inserted my Windows CD, went to the recovery console and used fixboot and fixmbr...Both did not do anything different.

I am stuck with using the LiveCD at this point, and would just like to get windows back working. Please, can someone help me restore my windows boot file?

Thank you for your time and patience.

EDIT: I would just like to say that I would LOVE to have this work dual boot, and I want Linux to run as well... I was just really bummed out last night not to have my computer working, so just to make it clear I am not anti Ubuntu or anything :D

---

### Post by GammaRay256 on 2009-01-31
You could try reinstalling grub using the live CD, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I know you said you already read some posts, I've had the error before too.  I don't quite remember how I fixed it though.  I think I just messed around a bit with some of the options on that thread...

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by xCel on 2009-01-31
I think I tried some things on that thread. I'll go through it again though. 

That script really showed a lot of information, thanks, here is the output:

As you can tell, I have 3 hard drives, and created a partition "Linux" in "/dev/sda2    *     42,186,690    78,156,224    35,969,535  83 Linux"

There appears to be an error/problem on sda2? I do not run a RAID configuration either. 

It would be great to get linux and windows running in dual boot format like I used to have! Its been so long. Thankyou for your patience!!

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Record 6 has no FILE magic (0xffffffff)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c22076d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    42,186,689    42,186,627   c W95 FAT32 (LBA)
/dev/sda2    *     42,186,690    78,156,224    35,969,535  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99999999

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bf8890e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="^J^J^J^J^J^J^J^J^J^J^J" UUID="1ADB-201A" TYPE="vfat" 
/dev/sda2: UUID="A0047E87047E6068" LABEL="Linux" TYPE="ntfs" 
/dev/sdb1: UUID="CEF8637AF8635FA7" TYPE="ntfs" 
/dev/sdc1: UUID="802CB5802CB57230" LABEL="Local Disk" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

C:\FREEDOS.BSS="FreeDOS" 


```

---

### Post by xCel on 2009-01-31
Don't know if this has any significance, but, I just tried mounting my "linux" partition and Ubuntu gave me the same error message about a hardware failure or something.

LASTLY:::Windows is installed on the "D:\" drive, not the C:\. I know Linux doesn't deal with this stuff, but, the valid boot.ini (for windows XP-64) is on the C:\ or /dev/sda? Does that make sense? :D

---

### Post by caljohnsmith on 2009-01-31
Did you try to install Ubuntu to an NTFS partition? Because your sda2 Ubuntu partition is detected as being NTFS, yet it is listed as type "83" or linux in the partition table. It looks like your best bet would be to reinstall Ubuntu. Before installing, I would open up gparted (System > Admin > Partition Editor), delete the sda2 partition, and then with that free space create 2 partitions: one ext3 partition for your main Ubuntu install (don't use NTFS), and one partition for swap. Once you have those two partitions created, I would run the installer and use the "manual" partition option so you can choose those partitions. Let me know how that goes or if you run into problems.

---

### Post by xCel on 2009-01-31
Ok Thanks!
That makes sense. I'll go ahead and try that.

---

### Post by xCel on 2009-01-31
Ugh. OK... Heres my update, and what I've tried.

Still getting the Grub error 22 message. Is there any way that this message is because it cannot find the boot.ini file for Windows?

I ended up wiping out a different drive, and creating a new partition table. It was a fairly new drive and not much on it...just a data drive. Created 3 partitons. One open for Windows data (NTSF) one partition for Ubuntu (ext3) and a smaller partition for "swap". All using Gparted.

Went ahead and started install, selected manual, had to select my exp3 for my linux partition, used "/" in the root directory input area, selected the swap for linux swap. Installed everything, restarted and still same Grub message.

Since I installed on a different drive, I went into BIOS, and selected the drive that Linux is on, and put that on highest priority. When restarted, I got "BOOT DISK FAILURE"... 

My question is, should I have made the first partition the linux partition? Or does the order of partitions not matter? Do I need to set it as the boot partition? It never asked me to do it. 

Thanks again for your time and patience.

---

### Post by caljohnsmith on 2009-01-31
> **xCel said:**
> Ugh. OK... Heres my update, and what I've tried.

Still getting the Grub error 22 message. Is there any way that this message is because it cannot find the boot.ini file for Windows?

Actually no, it's because Grub can't find its boot files on the drive/partition where it is looking, so Grub is probably looking on the wrong drive. :)
> **xCel said:**
> 
My question is, should I have made the first partition the linux partition? Or does the order of partitions not matter? Do I need to set it as the boot partition? It never asked me to do it. 

Thanks again for your time and patience.
Linux can go on any partition, whether it be the first one or any other one, and it can be either a primary or logical partition. Please run the Boot Info Script again on your new setup and post the results, and I'll try to help you sort out the booting problem.

---

### Post by xCel on 2009-01-31
Ok thank you!!

Also, I tried opening menu.lst, and there is nothing inside..

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99999999

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bf8890e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   969,924,374   969,924,312   7 HPFS/NTFS
/dev/sdb2         969,924,375 1,412,643,644   442,719,270  83 Linux
/dev/sdb3       1,412,643,645 1,465,144,064    52,500,420  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c22076d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    42,186,689    42,186,627   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CEF8637AF8635FA7" TYPE="ntfs" 
/dev/sdb1: UUID="173BE00400697C1E" TYPE="ntfs" 
/dev/sdb2: UUID="294b73ba-8198-460f-bb0e-cba5e2bfece5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="ba85cc58-da57-440d-bd9b-548b1c992d9e" TYPE="swap" 
/dev/sdc1: LABEL="^J^J^J^J^J^J^J^J^J^J^J" UUID="1ADB-201A" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== sdb2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=294b73ba-8198-460f-bb0e-cba5e2bfece5

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		FreeDOS
root		(hd2,0)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=ba85cc58-da57-440d-bd9b-548b1c992d9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location  of files loaded by Grub: ===================


 600.8GB: boot/grub/menu.lst
 600.8GB: boot/grub/stage2
 600.8GB: boot/initrd.img-2.6.27-7-generic
 600.7GB: boot/vmlinuz-2.6.27-7-generic
 600.8GB: initrd.img
 600.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

C:\FREEDOS.BSS="FreeDOS" 


```

---

### Post by caljohnsmith on 2009-01-31
Great, it looks like your booting problem may be easy to fix. How about doing:
```
sudo grub
grub> root (hd1,1)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu sdb drive, and I think you should be able to boot into Ubuntu just fine. If that works, when you get into Ubuntu do:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to the following two entries:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then reboot, and let me know if either of those entries works to boot Windows. If not, let me know exactly what happens when you select them from the Grub menu, and we can work from there.

---

### Post by xCel on 2009-01-31
Hey Caljohnsmith! It worked! I'm in Ubuntu, and I had the option of WindowsXP. Unfortunately I am getting a whole 'nother problem now... well, with windows.

I edited the menu.lst like you said. However, now when I try to go to WinXP,... it opens up in the middle of the installation process?! Weird!!

What is the point of having two menu entries for windows? I only have 1 installation of Windows XP. For whatever reason, ever since I installed x64, it always read off the C:\ for the boot.ini file and some other files, the only way i could get it to load was putting those files on the c:\. (Yet the installation is under D;\Windows) 

I dont know if you are a windows wiz as well, but, do you ahve any idea what I should do about that now? I used fixmbr in the "Recovery Console" last night and probably changed some stuff around. It would probably help to learn the structure of how an operating system boots. :/

Thanks for any help !!!

---

### Post by caljohnsmith on 2009-01-31
That's great news you can at least boot Ubuntu now. The reason for having two Windows entries is because I don't know where the Windows drive is in your BIOS boot order on start up, and when you boot the Ubuntu drive, that means your Windows drive could either be second (hd1) or third (hd2) in the BIOS boot order since you have 3 drives total. It sounds like you may have booted the wrong drive--did you actually try both Windows entries in the Grub menu? If so, which is the one that booted you into some sort of installation process? Since you have the Ubuntu drive booting OK now, I think it would be good to restore a Windows MBR to your Windows drive since your Windows drive currently has Grub in the MBR. How about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then you should be able to boot the Windows drive directly on start up if you select it from your BIOS. I would try doing that so we can get a better idea if the Windows problem you are experiencing is because you are actually booting the sdc drive which also has Windows boot files. Let me know how that goes.

---

### Post by xCel on 2009-01-31
Yes, I tried both entries of Windows. One started and said:

Windows could not start because the below file is missing or corrupt: 

<WINDIR>\System32\Ntoskrnl.exe

Then the second one started like usual. Says something about
Using C:\boot.ini file, then went to XP64 Splash Screen. Thought it was gravy then it asked for my Windows CD to finalize installation. (It was marked on #4 of #6 steps too...) I just got out of there....

I just did what you said, and now I'll try and going to Recovery Console and trying to fix my Windows MBR.

THank you!!

---

### Post by caljohnsmith on 2009-01-31
> **xCel said:**
> 
I just did what you said, and now I'll try and going to Recovery Console and trying to fix my Windows MBR.

If you ran the lilo command from my previous post, that would have installed a Windows equivalent MBR to your Windows drive, so there's no need to run "fixmbr" (although it doesn't hurt anything). :)

---

### Post by xCel on 2009-01-31
Oh hehe! Oops!

Ok well, I rebooted and it automatically went to Windows XP!! No Grub!? Ack! 

Anyways, it went back to the setup stuff... I just left my CD in there, I guess i'm reinstalling windows now too.. lol.... :(

I should have been cleaner with my harddrives and installations from the first place!

---

### Post by xCel on 2009-01-31
Well, this is bizarre. Windows XP "Re-installed" and nothing has changed... I am in XP right now, and it looks like it looked before this whole situation... Now Im scared to restart!!! :D

---

### Post by xCel on 2009-01-31
Just to report back: Both Ubuntu and Windows XP are working!!! Everything looks great. I've restarted and now I can load into whichever Id please.

Now I have to figure out how to make Windows XP default... I know you probably cringe hearing me say that :D

---

### Post by caljohnsmith on 2009-01-31
That's great news, I'm glad to hear both Windows and Ubuntu are booting OK. About making XP default in your Grub menu, it is as simple as modifying the "default X" line in your menu.lst (it's near the top). The way it works is:
```
default 0   --> 1st Grub entry
default 1   --> 2nd Grub entry
default 2   --> 3rd Grub entry
...etc.
```
So in other words, Grub begins counting at zero, not 1. If your Windows entry is for example the 5th entry in your Grub menu, then "default 4" is what you want. Anyway, cheers and enjoy Windows and Ubuntu. :)

---

### Post by thebozenator on 2009-01-31
hey! i am having the same error 22 problem and tried caljohnsmith's instructions but then i get error 17 cannot mount selected partition. do you have any idea why this happens or how to fix it?

---

### Post by xCel on 2009-01-31
Oh no! Not you too  :)

Well I finally got everything situated. On to the next? :D

---

