---
title: "Killed Grub - Need Help"
date: 2009-01-20
forum: General Help
---

### Post by MistaMatt90 on 2009-01-20
So today I decided that it would be a good idea to get rid of some of the crap partitions that Dell installed on my harddrive.  In the process, I managed to kill grub.  At first it wouldn't even get to the menu, but I reinstalled grub, and my menu was back.  Now, unfortunately, whenever I try to boot, it throws Error 22, saying that it can't boot from the partition.  I'm hoping that it's a simple issue with my menu.lst.  Here's some info:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot	  Start		 End	  Blocks   Id  System
/dev/sda3   *		   1		7758	62316103+   7  HPFS/NTFS
/dev/sda4			7759	   30402   181881179	f  W95 Ext'd (LBA)
/dev/sda5			7759		7820	  497952   82  Linux swap / Solaris
/dev/sda6			7821	   30401   181381851   83  Linux

Disk /dev/sdb: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00025ac3

   Device Boot	  Start		 End	  Blocks   Id  System
/dev/sdb1   *		   1		 991	 1997733+   b  W95 FAT32

Disk /dev/sdc: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot	  Start		 End	  Blocks   Id  System
/dev/sdc1			   1		 969	 1953439+   6  FAT16
```

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#			grub-install(8), grub-floppy(8),
#			grub-md5-crypt, /usr/share/doc/grub
#			and /usr/share/doc/grub-doc/.

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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#	  password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
##	  kopt_2_6_8=root=/dev/hdc1 ro
##	  kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##	  alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##	  lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##	  lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##	  altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##	  howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##	  memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

Thanks so much guys!

---

### Post by Sorivenul on 2009-01-20
From an initial glance, it looks like GRUB is looking for Ubuntu on (hd0,6), which would translate to /dev/sda7. You have no /dev/sda7. I would try switching all of the instances of (hd0,6) to (hd0,5) and see what happens.

---

### Post by Yellow Pasque on 2009-01-20
```
root		(hd0,6)
```
I think this is your problem. You're telling grub to look at the seventh partition of the first disk for /, but you only seem to have four partitions (numbered 3-6 oddly enough).

---

### Post by MistaMatt90 on 2009-01-20
Thanks for the replies, I got my Linux partition bootable by changing root to (hd0,5) but now when I select the Windows partition, Windows says it needs to be repaired. Should I run the repair console, or will that kill Grub again with the Windows Boot Loader?

---

### Post by Sorivenul on 2009-01-20
> **MistaMatt90 said:**
> Thanks for the replies, I got my Linux partition bootable by changing root to (hd0,5) but now when I select the Windows partition, Windows says it needs to be repaired. Should I run the repair console, or will that kill Grub again with the Windows Boot Loader?
It is probably wanting to run CHKDSK or whatever to ensure the integrity of the Windows partition after it was not cleanly unmounted. I don't think this should cause any problems, it should just check and repair any inconsistencies on the Windows partition.

---

### Post by MistaMatt90 on 2009-01-20
Thanks for the quick replies.  I thought I should elaborate a little on my last post.  Here's what it says when I try to boot to the Windows partition:

> Windows Boot Manager

Windows failed to start.  A recent hardware or software change might be the cause.  To fix the problem:
1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \Windows\system32\winload.exe

Status: 0xc0000225

Info:  The selected entry could not be loaded because the application is missing or corrupt.

Just thought I'd show that info before proceding.

Thanks,
Matt

---

### Post by caljohnsmith on 2009-01-20
My guess is that your Windows boot.ini file is using "partition(3)" since Windows is on sda3, but if you deleted sda1 and sda2, the boot.ini file should now use "partition(1)". In order to find out, how about posting the output of:
```
sudo mount /dev/sda3 /mnt
cat /mnt/boot.ini
```
If that uses anything other than "partition(1)", you could go ahead and edit it to use "partition(1)", and make sure you edit both instances. To edit your boot.ini file, you could do:
```
gksudo gedit /mnt/boot.ini
```
Let me know if that's the problem.

---

### Post by MistaMatt90 on 2009-01-20
```
matt@laptop:~$ sudo mount /dev/sda3 /mnt
matt@laptop:~$ cat /mnt/boot.ini
cat: /mnt/boot.ini: No such file or directory
```

Edit: does Vista use boot.ini?

---

### Post by caljohnsmith on 2009-01-20
Are you using Vista instead of XP? If so, then you don't have to worry about a boot.ini file, because I thought you had XP. Also, I notice that your sda3 partition now starts on the first cylinder of your drive, so did you resize the sda3 Windows partition from the beginning to use the space freed up by deleting sda1 and sda2? While you still have sda3 mounted on /mnt, please post:
```
ls -l /mnt
```

---

### Post by MistaMatt90 on 2009-01-20
Yes, I have Vista, and Yes, I used gparted to resize the partitions to take the space previously used by sda1 and sda2.
```
matt@laptop:~$ ls -l /mnt
total 7642721
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-02-03 18:06 Boot
-rwxrwxrwx 1 root root     333203 2008-01-20 21:24 bootmgr
-rwxrwxrwx 1 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root       8192 2008-07-08 20:46 DELL
-rwxrwxrwx 1 root root       4624 2008-06-29 01:25 dell.sdr
drwxrwxrwx 1 root root          0 2008-06-29 01:21 doctemp
drwxrwxrwx 1 root root          0 2008-06-28 22:45 Documents and Settings
drwxrwxrwx 1 root root          0 2008-09-07 16:54 dosbox
drwxrwxrwx 1 root root          0 2008-06-29 01:22 Drivers
-rwxrwxrwx 1 root root 3756064768 2009-01-19 13:40 hiberfil.sys
-rwxrwxrwx 1 root root 4069675008 2009-01-19 13:40 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-20 21:32 PerfLogs
drwxrwxrwx 1 root root       4096 2008-10-21 16:10 ProgramData
drwxrwxrwx 1 root root      12288 2008-10-27 12:09 Program Files
drwxrwxrwx 1 root root       4096 2008-07-08 20:10 $Recycle.Bin
drwxrwxrwx 1 root root       8192 2008-07-11 02:34 System Volume Information
drwxrwxrwx 1 root root       4096 2008-07-08 20:09 Users
drwxrwxrwx 1 root root      16384 2009-01-11 02:13 Windows
```

---

### Post by caljohnsmith on 2009-01-20
> **MistaMatt90 said:**
> Yes, I have Vista, and Yes, I used gparted to resize the partitions to take the space previously used by sda1 and sda2.

Ouch. Unfortunately resizing any Windows partition from the beginning is a big problem, because for one thing the starting sector of the partition is hard-coded in the Windows boot sector; that info is not updated when you resize the partition with a partition editor. I think Vista is a bit more robust about its booting process compared to XP, so with some work you might be able to get Vista booting again. The good news is that "testdisk" can at least fix your Vista boot sector, but it will take more than just fixing the boot sector to get Vista booting again. But let's start there, so how about making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda3 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". Next boot your Vista Install CD, go to the command line, and run:
```
bootrec /fixboot
bootrec /rebuildbcd
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. If you don't have a Vista Install CD (which seems likely since it sounds like your computer came with a recovery partition instead), you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and use that instead. After that reboot, try booting Vista from Grub, and let me know exactly what happens. We can work from there if you want.

---

### Post by MistaMatt90 on 2009-01-20
Thanks again for the speedy response.  I do have a disc at home, so I'll do that part tonight.  I'll run testdisc now and let you know if I run into issues.

Matt

---

### Post by MistaMatt90 on 2009-01-20
Just an update.  I followed your testdisk instructions and here's what it shows in my terminal:
```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 3 * HPFS - NTFS              0   1  1  7757 254 63  124632207 [OS]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```

---

### Post by caljohnsmith on 2009-01-20
Looks like I might be totally wrong--your Vista boot sector might be OK after all. I think it would help to get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post.

---

### Post by MistaMatt90 on 2009-01-20
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *          63   124632269    62316103+   7  HPFS/NTFS
/dev/sda4       124632394   488394751   181881179    f  W95 Ext'd (LBA)
/dev/sda5       124632396   125628299      497952   82  Linux swap / Solaris
/dev/sda6       125628363   488392064   181381851   83  Linux

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 4 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="F688ABA988AB6739" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="5c5f28c7-e1c5-4cf3-99b3-996e8499fa63" TYPE="swap" 
/dev/sda6: UUID="03ca7dbe-c054-4cb9-be09-2f009ddde693" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
none on /proc/bus/usb type usbfs (rw,devgid=126,devmode=664)
/dev/sda3 on /media/vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

================================== sda3/Boot: ==================================

total 796
drwxrwxrwx 1 root root   4096 2008-02-03 18:06 .
drwxrwxrwx 1 root root   8192 2009-01-19 14:44 ..
-rwxrwxrwx 1 root root  32768 2009-01-19 15:03 BCD
-rwxrwxrwx 2 root root  28672 2008-07-09 04:27 BCD.Backup.0001
-rwxrwxrwx 1 root root 262144 2009-01-19 13:41 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-02-03 18:06 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-02-03 18:06 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-02-03 18:06 bootstat.dat
drwxrwxrwx 1 root root      0 2008-02-03 18:06 cs-CZ
drwxrwxrwx 1 root root      0 2008-02-03 18:06 da-DK
drwxrwxrwx 1 root root      0 2008-02-03 18:06 de-DE
drwxrwxrwx 1 root root      0 2008-02-03 18:06 el-GR
drwxrwxrwx 1 root root      0 2008-02-03 18:06 en-US
drwxrwxrwx 1 root root      0 2008-02-03 18:06 es-ES
drwxrwxrwx 1 root root      0 2008-02-03 18:06 fi-FI
drwxrwxrwx 1 root root   4096 2008-02-03 18:06 Fonts
drwxrwxrwx 1 root root      0 2008-02-03 18:06 fr-FR
drwxrwxrwx 1 root root      0 2008-02-03 18:06 hu-HU
drwxrwxrwx 1 root root      0 2008-02-03 18:06 it-IT
drwxrwxrwx 1 root root      0 2008-02-03 18:06 ja-JP
drwxrwxrwx 1 root root      0 2008-02-03 18:06 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 21:23 memtest.exe
drwxrwxrwx 1 root root      0 2008-02-03 18:06 nb-NO
drwxrwxrwx 1 root root      0 2008-02-03 18:06 nl-NL
drwxrwxrwx 1 root root      0 2008-02-03 18:06 pl-PL
drwxrwxrwx 1 root root      0 2008-02-03 18:06 pt-BR
drwxrwxrwx 1 root root      0 2008-02-03 18:06 pt-PT
drwxrwxrwx 1 root root      0 2008-02-03 18:06 ru-RU
drwxrwxrwx 1 root root      0 2008-02-03 18:06 sv-SE
drwxrwxrwx 1 root root      0 2008-02-03 18:06 tr-TR
drwxrwxrwx 1 root root      0 2008-02-03 18:06 zh-CN
drwxrwxrwx 1 root root      0 2008-02-03 18:06 zh-HK
drwxrwxrwx 1 root root      0 2008-02-03 18:06 zh-TW

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=03ca7dbe-c054-4cb9-be09-2f009ddde693 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=5c5f28c7-e1c5-4cf3-99b3-996e8499fa63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb usbfs devgid=126,devmode=664 0 0
/dev/sda3       /media/vista ntfs-3g  defaults  0   0

================================== sda6/boot: ==================================

total 25516
drwxr-xr-x  3 root root    4096 2008-12-16 09:22 .
drwxr-xr-x 22 root root    4096 2008-11-28 12:54 ..
-rw-r--r--  1 root root  503560 2008-11-04 15:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 18:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 15:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 18:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-20 07:26 grub
-rw-r--r--  1 root root 8667126 2008-11-26 13:46 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8664093 2008-12-16 09:22 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 15:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 18:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 15:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 18:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 15:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 18:30 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2009-01-20 07:26 .
drwxr-xr-x 3 root root   4096 2008-12-16 09:22 ..
-rw-r--r-- 1 root root    197 2008-07-08 17:00 default
-rw-r--r-- 1 root root     15 2008-07-08 17:00 device.map
-rw-r--r-- 1 root root   8056 2008-07-08 17:00 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-08 17:00 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-07-08 17:00 installed-version
-rw-r--r-- 1 root root   8608 2008-07-08 17:00 jfs_stage1_5
-rw-r--r-- 1 root root   4496 2009-01-19 17:26 menu.bak
-rw-r--r-- 1 root root   4496 2009-01-20 07:26 menu.lst
-rw-r--r-- 1 root root   4496 2009-01-19 17:52 menu.lst~
-rw-r--r-- 1 root root   4575 2008-08-20 01:31 menu.old
-rw-r--r-- 1 root root   7324 2008-07-08 17:00 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-07-08 17:00 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-07-08 17:00 stage1
-rw-r--r-- 1 root root 108356 2008-07-08 17:00 stage2
-rw-r--r-- 1 root root   9276 2008-07-08 17:00 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

---

### Post by caljohnsmith on 2009-01-20
It looks like your Vista boot sector is OK after all, so I don't think we need to worry about that at least. So whenever you get the chance, how about running the commands from your Vista Install CD from post #11, and let me know what happens when you boot Vista after that. We can go from there.

---

### Post by MistaMatt90 on 2009-01-20
So I should do those commands rather than "Repair My Computer" like the message told me?

---

### Post by caljohnsmith on 2009-01-20
> **MistaMatt90 said:**
> So I should do those commands rather than "Repair My Computer" like the message told me?
Doing the automated "Repair My Computer" will probably work, so if you want to try that first, go for it. If it doesn't work, then we can try to fix Vista from the command line.

---

### Post by MistaMatt90 on 2009-01-20
Thanks for working with me on this so far.  I'll jump on this as soon as I get home.  :)

---

### Post by MistaMatt90 on 2009-01-20
Vista may very well be dead.  I did the automatic "Repair My Computer".  This made Vista bootable, and I was able to log in under my name.  However, my personal profile could bot be loaded, and I had to manually start explorer.exe.  I can't open any files, it just tells me they don't exist (even if I click directly on them).  I was hoping to do a repair install, but in Vista that has to be done once logged in--but I can't get the cd to run.  My C:\ drive has been changed to V:\

May be time to just kill it :(

Let me know if you have any ideas.

---

### Post by caljohnsmith on 2009-01-20
So are you saying you can't boot the Vista CD now? You did the repair option from the Vista CD, true? If you can boot the Vista CD at all, how about running the commands from my previous post.

---

### Post by MistaMatt90 on 2009-01-20
I can boot from the cd.  Unfortunately, MS made it so Repair Installs can only be done if you can boot to the system.  I did a quick google search and found this:
[http://www.techimo.com/forum/technical-support/219994-broke-vista-after-resizing-partition.html](http://www.techimo.com/forum/technical-support/219994-broke-vista-after-resizing-partition.html)

They have the exact problem as me.  Said that changing the drive letters back to C: fixed everything.  Any ideas on how I can do this?

---

### Post by MistaMatt90 on 2009-01-20
Fixed!  Turns out that having my drive labeled as V was the entire issue.  Followed this link:
[http://www.linuxhomenetworking.com/forums/showthread.php?t=16198](http://www.linuxhomenetworking.com/forums/showthread.php?t=16198)

Thanks for all the help everyone gave me!!!

---

