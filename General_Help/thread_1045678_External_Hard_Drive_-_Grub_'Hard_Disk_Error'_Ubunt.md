---
title: "External Hard Drive - Grub 'Hard Disk Error' Ubuntu 8.10"
date: 2009-01-20
forum: General Help
---

### Post by alpine_uni on 2009-01-20
Howdy!

I am fairly new to the linux world, and have only played around with Ubuntu a little. I have recently installed Ubuntu 8.10 on an external USB hard drive. I have set my BIOS to boot from the hard drive, yet after selecting to boot from it I get a message saying "Hard Disk Error". How do I correct this so that I can boot from either my internal IDE Windows XP drive, or the external USB Ubuntu drive? Thanks!

---

### Post by Noblacktie on 2009-01-20
When you installed Ubuntu, did you specify that it should install the GRand Unified Bootloader (GRUB) into the root folder of your external hard drive? You need to do this to boot directly from that. Else, it will need to routed by the GRUB.

By default, GRUB goes into the MBR in the first partition of your first drive (hd0,0).

Try booting from your normal drive with your external drive plugged in and see if you get a GRUB menu.

---

### Post by alpine_uni on 2009-01-20
I took and tried using my Super Grub Disk to fix the issue, but it said that it could not find the hard disk... so nothing got changed. Any help would be greatly appreciated, thanks!

Mike

---

### Post by alpine_uni on 2009-01-20
When I boot with the external hard drive plugged in, my computer automatically goes to windows. If I hit the ESC key, I get a list of several different devices that could possibly be boot devices (cd drive, dvd drive, hard drive, usb drive). If I select my normal hard drive, it boots windows just fine, but if I select my USB drive, I get the 'Hard Disk Error' message.

I did not select where GRUB goes on the install, as I did not see any way to do this even.

---

### Post by Noblacktie on 2009-01-20
OK, do you have a USB pendrive handy? One that's at least 1GB?

If you do, fire up the Live CD and go to:

System > Administration > Create a USB Startup Disk

This will give you a LiveUSB image of Ubuntu.

Then try and boot from this. If your computer still won't then you have one of those finicky motherboards that don't support direct booting from a USB device.

If it does, something got messed up during your HDD install. Take this opportunity to mount your HDD and see if anything is missing. Check the /boot/grub/ folder to make sure that all looks fine.

If it doesn't, then come back and I'll point you towards a workaround method that might allow you to use your USB HDD.

---

### Post by alpine_uni on 2009-01-20
I have previously attempted the USB pendrive, and it has not worked (for one reason or another), but I am almost certain that my motherboard does support direct booting from a USB device, since it is in the BIOS as an option under 'Removable Devices'.

Where should I go next? You suggested to mount the drive, so I'm assuming I should boot up from the LiveCD and do it from there? Once I do that, what am I looking for? I don't know what it should look like, but at previous glances it definitely looks like there are linux files on the drive.

> **Noblacktie said:**
> OK, do you have a USB pendrive handy? One that's at least 1GB?

If you do, fire up the Live CD and go to:

System > Administration > Create a USB Startup Disk

This will give you a LiveUSB image of Ubuntu.

Then try and boot from this. If your computer still won't then you have one of those finicky motherboards that don't support direct booting from a USB device.

If it does, something got messed up during your HDD install. Take this opportunity to mount your HDD and see if anything is missing. Check the /boot/grub/ folder to make sure that all looks fine.

If it doesn't, then come back and I'll point you towards a workaround method that might allow you to use your USB HDD.

---

### Post by Noblacktie on 2009-01-20
You would think so, wouldn't you?

Unfortunately, this isn't the case. My own desktop rig as well as my ToshiSatt laptop purport to 'support USB booting' but have never even managed to do it once. Not even with a Windows Rescue image. 

It isn't the pendrives because they work on a third computer and numerous others belonging to friends. It's just that my two computers don't actually support USB booting despite showing the option to do so in the BIOS boot menu.

Anyway, try this to see if your install was successful and this is just a GRUB issue:

Boot the Live CD. At the first screen, select "BOOT FROM HARD DRIVE".

---

### Post by alpine_uni on 2009-01-20
I've tried the "Boot From Hard Drive" as well, and it states that no drive can be found, or something of that sort. If you want the exact message, I can get it for you.

---

### Post by Noblacktie on 2009-01-20
Can you mount the external hard drive in the Live session? Does it show up in the Nautilus file browser or the Places menu?

*edit* Site's a bit wonky, submitted reply while trying to Refresh.

Anyway, do this while you're in Live session:

Open the Terminal (Apps > Accs > Terminal) and type

```
sudo fdisk -l
```

Paste the output here.

---

### Post by alpine_uni on 2009-01-20
The external hard drive does mount in the live session. It shows up  under the places menu in the section with computer, cd/dvd creator, cd-rom/dvd-rom drive, cd-rw drive, and my internal hard drive. When I open the file browser, I see the drive on the left beneath the Places menu (again), and can open it from there to look at what is on the drive. It is also on my desktop.

> **Noblacktie said:**
> Can you mount the external hard drive in the Live session? Does it show up in the Nautilus file browser or the Places menu?

---

### Post by alpine_uni on 2009-01-20
The 80.0 GB is my internal HD, and the 30.0 GB is my external.

Disk /dev/sda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10340    78170368+   7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x756b756b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3492    28049458+  83  Linux
/dev/sdb2            3493        3648     1253070    5  Extended
/dev/sdb5            3493        3648     1253038+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-01-20
So are you booting your sda drive or sdb drive on start up? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by alpine_uni on 2009-01-20
Here are the results:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156340799    78170368+   7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x756b756b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    56098979    28049458+  83  Linux
/dev/sdb2        56098980    58605119     1253070    5  Extended
/dev/sdb5        56099043    58605119     1253038+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40F0C063F0C060B0" TYPE="ntfs" 
/dev/sdb1: UUID="100ddb23-9344-4257-8a87-b3dcfbf765f7" TYPE="ext3" 
/dev/sdb5: UUID="783622aa-7b83-4283-8510-8082e0c59094" TYPE="swap" 
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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows Whistler Personal" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=100ddb23-9344-4257-8a87-b3dcfbf765f7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=100ddb23-9344-4257-8a87-b3dcfbf765f7

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
uuid		100ddb23-9344-4257-8a87-b3dcfbf765f7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=100ddb23-9344-4257-8a87-b3dcfbf765f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		100ddb23-9344-4257-8a87-b3dcfbf765f7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=100ddb23-9344-4257-8a87-b3dcfbf765f7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		100ddb23-9344-4257-8a87-b3dcfbf765f7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=100ddb23-9344-4257-8a87-b3dcfbf765f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=783622aa-7b83-4283-8510-8082e0c59094 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2009-01-20 12:13 .
drwxr-xr-x 20 root root    4096 2009-01-20 12:13 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-20 12:14 grub
-rw-r--r--  1 root root 8179205 2009-01-20 12:13 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-20 12:14 .
drwxr-xr-x 3 root root   4096 2009-01-20 12:13 ..
-rw-r--r-- 1 root root    197 2009-01-20 12:14 default
-rw-r--r-- 1 root root     15 2009-01-20 12:14 device.map
-rw-r--r-- 1 root root   8108 2009-01-20 12:14 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-20 12:14 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-20 12:14 installed-version
-rw-r--r-- 1 root root   8712 2009-01-20 12:14 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-20 12:14 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-20 12:14 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-20 12:14 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-20 12:14 stage1
-rw-r--r-- 1 root root 121460 2009-01-20 12:14 stage2
-rw-r--r-- 1 root root   9556 2009-01-20 12:14 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-20
Since you all ready have the Super Grub Disk, how about booting that, at the first main menu press "c" to get the command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Compare the output of both those commands, and the (hdX) that shows three partitions should be your USB Ubuntu drive; if your Ubuntu drive comes before the Windows drive in the BIOS boot order, then the Ubuntu drive should be (hd0). Let me know if it isn't, but proceed with:
```
grub> rootnoverify (hd0)
grub> chainloader +1
grub> boot
```
And let me know what happens after you do that. We can work from there if you want.

---

### Post by alpine_uni on 2009-01-20
geometry (hd0) --> drive 0x80: C/H/S = 1023/240/63, The number of sectors = 156368016, LBA Partition num: 0, Filesystem type unknown, partition type 0x7

geometry (hd1) --> Error 21: Selected disk does not exist

My external Ubuntu drive is above my internal IDE drive for boot order, but the CD-Drive is the first on the list.

After entering the second set of code, it gave me the option to boot in XP Professional or XP Whistler (aka trying to boot from my internal drive).

---

### Post by caljohnsmith on 2009-01-20
That's strange, because the output of those geometry commands show that the Windows drive is first in the BIOS boot order or (hd0), and your USB drive is not even detected. Are you sure your BIOS supports booting from a USB drive? Since Grub can't even see the USB drive on start up, I don't think you're going to be a able to boot the USB drive on start up directly from BIOS. How about downloading the [PLoP Boot Manager ISO]("http://download.plop.at/files/bootmngr/plpbt-5.0.zip"), burn that to CD, boot it, and choose the option to boot the USB drive from its main menu. If there is any boot manager that might boot your USB drive in your situation, it would probably be PLoP, because PLoP has its own built-in USB drivers; therefore PLoP does not depend on having a BIOS that supports booting a USB drive. How about giving it a shot and let me know what happens.

---

### Post by alpine_uni on 2009-01-20
I have another USB Boot Loader disk that I tried earlier, and it never fully started up  (this was before I reinstalled Ubuntu). I just tried it again and got the Ubuntu start up screen (Ubuntu and orange status bar). The orange status bar kept going back and forth, and then the screen went black with one white bar top-left. Now it says:

Starting up . . .
Loading, please wait . . .


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

---

### Post by caljohnsmith on 2009-01-20
Sounds like you successfully initially booted Ubuntu, but Ubuntu is now having problems. What USB boot loader disk are you using? How about when you boot the USB drive, when you get the Grub menu (or you might have to press ESC to get the menu), select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line try adding any of these different parameters (you can add more than one at a time if you want):
```
noapic nolapic acpi=off pci=noacpi irqpoll ide=nodma nopcmcia all_generic_ide pci=nomsi
```
Then press enter to save the change, and finally "b" to boot. Let me know if any of those parameters makes a difference about booting Ubuntu.

---

### Post by alpine_uni on 2009-01-20
Same error popped up after trying to boot. : [

---

### Post by caljohnsmith on 2009-01-20
So how about downloading the PLoP boot manager and trying that?

---

### Post by alpine_uni on 2009-01-20
No luck... I think I will just get an adapter that will allow me to plug the 2.5" notebook hd into the tower instead, and hopefully that will work fine. Thank you both for your help!

---

### Post by Noblacktie on 2009-01-20
Sorry for the MIA, had to finish something my boss wanted 

But you're in much better hands with caljohnsmith.

Might I suggest you install GRUB in /dev/sda/ (your internal drive)?

My old Ubuntu Ext.USB install will not boot unless GRUB is on an internal drive.

The only issue with this is that the Ext. USB drive must now be permanently attached to the computer or else you will get GRUB errors.

The workaround is to create a small /boot partition in /dev/sda/. This will then allow you to remove the USB drive and still boot into Windows without issue.

---

