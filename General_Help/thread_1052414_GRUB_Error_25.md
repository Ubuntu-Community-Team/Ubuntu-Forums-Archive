---
title: "GRUB Error 25"
date: 2009-01-27
forum: General Help
---

### Post by seubill on 2009-01-27
Getting grub error 25 after 8.10 server installation

Output from Results.txt file;


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       jfs
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot        Start          End         Size  Id System

/dev/sda1                 63      112,454      112,392  de Dell Utility
/dev/sda2    *       112,455  146,480,669  146,368,215   7 HPFS/NTFS
/dev/sda3        146,496,735  156,232,124    9,735,390  db CP/M / CTOS / ...


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x900d00fe

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  163,846,934  163,846,872   7 HPFS/NTFS
/dev/sdb2        163,846,935  328,111,559  164,264,625   5 Extended
/dev/sdb5        163,846,998  169,903,439    6,056,442  82 Linux swap / Solaris
/dev/sdb6        169,903,503  328,111,559  158,208,057  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0102" TYPE="vfat" 
/dev/sda2: UUID="664CB32E4CB2F7BF" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: UUID="CEF0EDB4F0EDA347" LABEL="Server 2003" TYPE="ntfs" 
/dev/sdb5: UUID="8dc7cf27-d831-4863-ad06-a55793df017e" TYPE="swap" 
/dev/sdb6: UUID="97896d6a-5856-4cf1-b8ff-03d4e0bf1683" TYPE="jfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows Server 2003, Standard" /noexecute=optout /fastdetect


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=97896d6a-5856-4cf1-b8ff-03d4e0bf1683 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97896d6a-5856-4cf1-b8ff-03d4e0bf1683

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

title		Ubuntu 8.10, kernel 2.6.27-7-server
uuid		97896d6a-5856-4cf1-b8ff-03d4e0bf1683
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=97896d6a-5856-4cf1-b8ff-03d4e0bf1683 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-server
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode)
uuid		97896d6a-5856-4cf1-b8ff-03d4e0bf1683
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=97896d6a-5856-4cf1-b8ff-03d4e0bf1683 ro  single
initrd		/boot/initrd.img-2.6.27-7-server

title		Ubuntu 8.10, memtest86+
uuid		97896d6a-5856-4cf1-b8ff-03d4e0bf1683
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=97896d6a-5856-4cf1-b8ff-03d4e0bf1683 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=8dc7cf27-d831-4863-ad06-a55793df017e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location  of files loaded by Grub: ===================


 153.5GB: boot/grub/menu.lst
 153.5GB: boot/grub/stage2
  89.1GB: boot/initrd.img-2.6.27-7-server
 113.8GB: boot/vmlinuz-2.6.27-7-server
  89.1GB: initrd.img
 113.8GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-27
Can you change your BIOS to boot the 250 GB sdb drive on start up? If so, that would be ideal. If you can do that, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,5)
grub> setup (hd1)
grub> quit
```
And please post the output of the commands before typing "quit". If the commands are successful, try rebooting, set your BIOS to boot the sdb drive, and let me know how far you get. We can work from there. :)

---

### Post by seubill on 2009-01-27
In the system BIOS, under `Boot Sequence`, I have CD-ROM, USB device, and then SATA Hard Drive. Does not show an option of the two different hard drives. Am I looking in the wrong place?

---

### Post by seubill on 2009-01-27
Here are those outputs:



```
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)

grub> makeactive

grub> root (hd1,5)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/jfs_stage1_5" exists... yes
 Running "embed /boot/grub/jfs_stage1_5 (hd1)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+18 p (hd1,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> root (hd1,0)

```

---

### Post by caljohnsmith on 2009-01-27
> **seubill said:**
> In the system BIOS, under `Boot Sequence`, I have CD-ROM, USB device, and then SATA Hard Drive. Does not show an option of the two different hard drives. Am I looking in the wrong place?
It sounds like you're in the right place, but I don't know how to help since I don't know your BIOS. Is the SATA drive it is referring to the 250 GB drive (is your 250 GB drive SATA)? Is the 80 GB drive IDE? There's no way to toggle the SATA drive in the boot sequence to another drive?

---

### Post by seubill on 2009-01-27
Both drives are SATA`s. Both use the `cable select` setting on the physical drive, as opposed to Master and Slave settings.

The 80 GB drive came OEM with XP.

The additional 250 GB drive has Server 2003 on it, and now also 8.10 Server.

Before the Ubuntu Server install on the 250 GB drive, the system would dual-boot in the ordinary fashion, listing XP or Server 2003 as options.

I do not know of any method to toggle between the drives.

---

### Post by seubill on 2009-01-27
There is mention of IDE hard drive in the boot sequence (in BIOS), the last device in the list. But, in parenthesis after that is (not present).

---

### Post by rweaver4 on 2009-01-27
I believe sata drives should be set as master rather than cable select.
rweaver4

---

### Post by caljohnsmith on 2009-01-27
OK, how about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), burn it to CD, and boot that; when you get the main menu, press "c" to get the command line, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
And please let me know what those commands return. Since there is no way of copying/pasting the text, if you have a digital camera you could take a picture of the screen if you want. Or if you can just give me an idea of the size of the drives and partitions that those commands return, we can go from there.

---

### Post by seubill on 2009-01-27
I have a Super Grub Disk now. Will give it a try. I think that I`m about to lose power again in this ice storm.

---

### Post by seubill on 2009-01-27
Here are the results from the Super Grub disk:


grub> geometry (hd0)  Error 25: Disk Read Error

grub> geometry (hd1)  drive 0x81: C/H/S=1023/255/63, The number of sectors=156250000, LBA

partition num: 0, Filesystem type is fat, partition type 0xde

partition num: 1, Filesystem type is unknown, partition type 0x7

partition num: 2, Filesystem type is unknown, partition type 0xdb

---

### Post by caljohnsmith on 2009-01-27
Yikes, so according to those results, Grub can't even read your sdb drive right now, it just gives "disk read error". But the sdb drive is (hd0), so that means the sdb drive is before the sda drive in the BIOS boot order, which is good. How about next posting:
```
sudo mount /dev/sdb6 /mnt && ls -l /mnt
```

---

### Post by seubill on 2009-01-27
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt && ls -l /mnt
total 76
drwxr-xr-x  2 root root 4096 2009-01-27 22:33 bin
drwxr-xr-x  3 root root 4096 2009-01-27 22:35 boot
lrwxrwxrwx  1 root root   11 2009-01-27 22:22 cdrom -> media/cdrom
drwxr-xr-x  4 root root 4096 2009-01-27 22:23 dev
drwxr-xr-x 72 root root 8192 2009-01-27 22:35 etc
drwxr-xr-x  3 root root    8 2009-01-27 22:35 home
lrwxrwxrwx  1 root root   31 2009-01-27 22:23 initrd.img -> boot/initrd.img-2.6.27-7-server
drwxr-xr-x 13 root root 4096 2009-01-27 22:33 lib
drwxr-xr-x  4 root root   24 2009-01-27 22:22 media
drwxr-xr-x  2 root root    1 2008-10-20 12:27 mnt
drwxr-xr-x  2 root root    1 2009-01-27 22:22 opt
drwxr-xr-x  2 root root    1 2008-10-20 12:27 proc
drwxr-xr-x  2 root root   16 2009-01-27 22:22 root
drwxr-xr-x  2 root root 4096 2009-01-27 22:35 sbin
drwxr-xr-x  2 root root    1 2009-01-27 22:22 srv
drwxr-xr-x  2 root root    1 2008-10-14 13:02 sys
drwxrwxrwt  2 root root    1 2009-01-27 22:35 tmp
drwxr-xr-x 11 root root   80 2009-01-27 22:33 usr
drwxr-xr-x 13 root root   88 2009-01-27 22:22 var
lrwxrwxrwx  1 root root   28 2009-01-27 22:23 vmlinuz -> boot/vmlinuz-2.6.27-7-server
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2009-01-27
At least you can mount and read your new server partition, but Grub can't read that drive on start up for some reason. Would it be too much trouble to physically swap the connections on both your SATA drives? In other words, plug the sdb drive into the slot sda is in right now, and vice-versa? If you can do that, please do the Grub geometry commands again from the Super Grub Disk and let me know if it makes any difference in the results.

---

### Post by rweaver4 on 2009-01-28
I responded earlier about SATA drives, I think I was probably wrong in that SATA drives do not need to be allocated 'master', 'slave', and even 'cable select' may confuse the issue.

Not so small world? I am sitting in front of my computer in South Australia with the A/C running flat out as the outside temperature is currently 45'C and you are about to lose power in an ice storm! Which would you prefer? :D
rweaver4

---

### Post by seubill on 2009-01-30
rweaver4,  Yes, cable select is the proper method using a sata cable and 2 sata drives.  I am from Brasil originally, and would much prefer the 45C and air c. as opposed to a rather nasty ice storm.  Still have no power, internet or fone service. Using laptop and work location for this one!:p

---

### Post by seubill on 2009-01-31
Have swapped hard drives locations vice-versa. Here is output from Super Grub Disk: (to compare to post 11)

```
grub> geometry (hd0)   Error 25: Disk read Error



grub> geometry (hd1)   drive 0x81:  C/H/S=1023/255/63, The number of sectors =488281250, LBA



Partition num: 0,  Filesystem type unknown, partition type 0x7



Partition num: 4,  No BSD/SOLARIS sub-partition found, partition type 0x82



Partition num: 5,  Filesystem type unknown, partition type 0x83

```

---

### Post by caljohnsmith on 2009-01-31
OK, that's good news you can at least boot the Ubuntu drive now that you swapped it with the Windows drive, but the bad thing is that Grub still can not access drive (hd0), which is now your Windows drive. It seems that any drive in the (hd0) slot of your computer can't be accessed on start up through BIOS, because Grub uses your BIOS to access that drive on start up. Also, when you boot into the Ubuntu Server, what do you get? Do you have any kind of Windows manager or is it solely command line based? I'm not familiar with Ubuntu Server, and I thought I remember reading that it is solely command line driven with no GUI; so correct me if I'm wrong. 

How about from your Live CD try:
```
sudo mount /dev/[COLOR="Blue"]sdb6[/COLOR] /mnt
```
And change "sdb6" to sda6 if the Ubuntu drive is now sda (it might be since you swapped it with the Windows drive). Then download the [PLoP boot manager]("http://download.plop.at/files/bootmngr/plpbt-5.0.zip") file to your Ubuntu desktop, and then do:
```
cd ~/Desktop
unzip plp*.zip
sudo cp plp*/plpbt.bin /mnt/boot
gksudo gedit /mnt/boot/grub/menu.lst
```
Delete your current Windows XP entry and replace it with:
```
title PLoP Boot Manager
uuid		97896d6a-5856-4cf1-b8ff-03d4e0bf1683
kernel /boot/plpbt.bin
```
Then reboot, select PLoP from your Ubuntu Grub menu, and then choose the USB option in the PLoP boot menu. It's a bit of a long shot since your Windows drive is not USB, but PLoP has its own built-in drivers and maybe can access your Windows drive. Let me know how that goes.

---

### Post by seubill on 2009-01-31
Yes, it sure is sda6 now, thanks for having me check for that!  You are correct, Ubuntu server is command line only, no GUI, but I have heard that a person can install a GUI to it.  When I boot server, it gives 3 lines about a `string error -71`, but does start up. User name and password required, then you get the command line. I have found that `sudo shutdown now -h` gets you back out and shuts down the system.

Have rebooted to PloB, but cannot seem to get the arrow keys to work in order to highlight the USB option. It`s stuck on `HDA Partition 1` in the selection box. What do I need to do now?

---

### Post by caljohnsmith on 2009-01-31
OK, I think I have a better idea than trying to get PLoP working at this point. How about downloading the attached "Win_boot_files.zip" to your desktop, and do:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip Win_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace all entries after the "Other operating systems" line with:
```
title Windows XP & Windows Server
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you choose "Windows XP & Windows Server" from your Grub menu. We can work from there.

---

### Post by seubill on 2009-01-31
```
gksudo gedit /boot/grub/menu.lst
```

The list is completely empty

---

### Post by caljohnsmith on 2009-01-31
Sorry, I forgot you are using the Live CD. How about:
```
sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6
gksudo gedit /media/sda6/boot/grub/menu.lst
```

---

### Post by seubill on 2009-01-31
Ok, did everything and rebooted.  Selected `Windows XP and Windows Server 2003` from GRUB menu. Next was presented the dual-boot menu like I had before Ubuntu server;  Windows XP or Server 2003.  Selected XP and then got this:
----------------------------------------------------------------------------

Windows could not start because of a computer disk hardware configuration problem. Could not read from the selected boot disk. Check boot path and disk hardware. Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

---------------------------------------------------------------------------------

---

### Post by caljohnsmith on 2009-02-01
OK, we're definitely making progress I think. How about when you get your Grub menu on start up, press "c" to get the command line, and do again:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
And please let me know if the results are the same as what you got in post #17 when you used the Super Grub Disk (I would expect them to be the same, but something doesn't seem consistent right now, so I just want to make sure).

---

### Post by seubill on 2009-02-01
OK, that sounds great that you are thinking we are making progress!
Here is the output:

```


grub> geometry (hd0) drive 0x80: C/H/S = 1023/255/63, The number of sectors = 488281250, LBA
Partition num: 0, Filesystem type unknown, partition type 0x7
Partition num: 4, Filesystem type unknown, partition type 0x82
Partition num: 5, Filesystem type is jfs, partition type 0x83

grub> geometry (hd1) Error 25: Disk read error


```

---

### Post by caljohnsmith on 2009-02-01
That's interesting, because now the Ubuntu Server drive is (hd0), yet before when you used Super Grub Disk, the Ubuntu Server drive was (hd1). Did you have to change the BIOS boot order in order to boot the Super Grub Disk? If you didn't change the BIOS boot order, I don't know why the drive would have gone from (hd1) to (hd0). But unfortunately, I think you have more serious problems at this point. When you tried to boot Windows XP on the the other drive from your Ubuntu Server drive, it gave you the error:
> Windows could not start because of a computer disk hardware configuration problem. [COLOR="Red"]Could not read from the selected boot disk[/COLOR]. Check boot path and disk hardware. Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information.
So Windows gives the same error that Grub gives when you try to access that drive: "Disk read error". We know it isn't a problem with the HDDs, because when you swapped them, each can be individually accessed just fine when they use the SATA slot on the motherboard that works with your BIOS. Also, both HDDs can be accessed just fine when you boot into Ubuntu. So based on that evidence, my guess is that it's not a hardware issue, but an issue with your BIOS. Is there any way you can update the BIOS on that computer? Have you checked the manufacturer's website of your computer's motherboard to see if a BIOS update is available?

---

### Post by seubill on 2009-02-01
I noticed that the Disk read error is now to (hd1) and before was to (hd0).  Did not change anything in the BIOS.  This particular BIOS only allows changing boot sequence order of devices, CD-ROM, Floppy, USB, HD, etc...  Does not give me the option of selecting which hard drive to boot from.  I had upgraded and flashed the BIOS about a year ago. Will slip in the live CD to get on the net and check if another upgrade is available, but I don`t hold out any hope of that.

---

### Post by meierfra. on 2009-02-01
I suggest to have a look at your jumper settings:  [Hermanzone's Grub Error 25]("http://users.bigpond.net.au/hermanzone/p15.htm#25")

(Edit: Ignore this.  I hadn't  been paying attention. There is no such thing as jumper setting for SATA drives)

---

### Post by seubill on 2009-02-01
The latest BIOS version is A07,  which is installed.

Maybe 8.10 Server on this machine not meant to be?

---

### Post by meierfra. on 2009-02-01
Ignore my previous post.  I hadn't realized that your  drive is a SATA drive.

---

### Post by seubill on 2009-02-01
meierfra,  right, thank you for trying to help just the same.:)

---

### Post by meierfra. on 2009-02-01
Sometimes the CDrom drive can interfere. Is your CD drive an IDE drive?

---

### Post by caljohnsmith on 2009-02-01
The problem is that we tried to boot XP from your Ubuntu server drive using the same technique that you were using to boot Windows Server before. In other words, I don't think it's an issue with Ubuntu server right now, because even if you go back to your previous configuration, I think you will get the same "Could not read from the selected boot disk" error from Windows again. As far as I know, that's a windows error that doesn't depend on whether you have Ubuntu Server or Grub installed. So I really don't know at this point what you can do to fix things, I'll have to think about it some more; but the bottom line is I don't think uninstalling Ubuntu Server will magically make your setup work again (but I could be wrong). Maybe Meierfra has some more ideas, because I'm not sure what else you can do if your BIOS is all ready up-to-date. :)

---

### Post by seubill on 2009-02-01
CD-ROM is PATA-0  (IDE Master)  and also there is another optical drive,

DVD+/-RW  which is PATA-1  (IDE Slave).

Thinking about replacing the hard drives back into their original bays and deleting the jfs partition and the linux swap partition, going back to the existing Windows Server configuration.

---

### Post by seubill on 2009-02-01
OK, I have replaced the hard drives back to their bays, deleted jfs and swap, have all partitions on both drives back to the way as was before 8.10 sever installation.  Rebooted and gave the Error 25 again.  Ran the Super grub disk and rewrote the MBR onto sdb, now everything is ok, have XP and Server 2003 dual booting. 

So what is the lesson with this, can Ubuntu Server only be used independently, as the only OS on a system?

---

### Post by caljohnsmith on 2009-02-01
I'm just wondering, but when you boot the Super Grub Disk, does it still return "disk read error" for one of your drives when you run the geometry commands? If so, I don't understand how Windows is getting around that problem when we tried that same technique by putting Windows boot files in your Windows Server partition; I must be missing something. But I'm glad both XP and and Windows Server are working at least now.

---

### Post by seubill on 2009-02-01
This is indeed a good question, John.  Rebooted the Super Grub Disk and did the geometry commands again:

```


grub> geometry (hd0)  Error 25; Disk read error

grub> geometry (hd1)  drive 0x81: C/H/S = 1023/255/63, The number od sectors = 156250000, LBA
Partition num: 0, Filesystem type is fat, partition type 0xde
Partition num: 1, Filesystem type is unknown, partition type 0x7
Partition num; 2, Filesystem type is unknown, partition type 0xdb


```

This does not make much sense, as showing (hd1) as the smaller drive (80 GB), where XP lives exclusively. /dev/sda1 is a fat16 partition for Dell Utility, /dev/sda2 is ntfs, XP with boot flag, /dev/sda3 is fat32 Dell restore partition. I was thinking all this should be (hd0)?

---

### Post by seubill on 2009-02-01
I spoke too soon.  XP is booting up fine. Server 2003 gives the same error message has in post #23, so cannot boot up Server now.

---

### Post by caljohnsmith on 2009-02-01
Well that's bad news Windows Server now gives you the same "Could not read from the selected boot disk" error that you previously got when we tried to boot XP, but at least it makes sense now since that is consistent with our previous findings, and also with the Grub "disk read errors". So fortunately it looks like it's not a problem with Grub or Ubuntu Server, it unfortunately appears to be an issue with your computer.

---

### Post by seubill on 2009-02-01
Right, but I`m puzzled because both XP and Server 2003 booted without any problems immeadiately before the Ubuntu Server installation.

---

### Post by seubill on 2009-02-01
Slipped the Super Grub Disk back in just for fun. Showing the partitions from Grub`s point of view, there is nothing on sda (hd0), 74 GB on sdb (hd1), and 78 GB on sdc (hd2).


Tried booting MBR of (hd2) with SGD and returned Error 22.

---

