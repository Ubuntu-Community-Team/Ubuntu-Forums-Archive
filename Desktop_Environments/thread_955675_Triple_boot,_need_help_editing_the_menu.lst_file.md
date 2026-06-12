---
title: "Triple boot, need help editing the menu.lst file"
date: 2008-10-22
forum: Desktop Environments
---

### Post by ghen on 2008-10-22
I have installed XP on 1 hard drive; Vista and Ubuntu on a second drive. I want the Grub bootloader to control all 3.

Currently since I installed them in order XP->Vista->Ubuntu I can access the vista bootloader as an option in the Grub menu to get to XP. This works great, but I want to learn how hard drives and partitions are numbered in the menu.lst file seen here:

```
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
# kopt=root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (recovery - PC Angel)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

The only place where I know of in Ubuntu to access hard drive and partition information is in the GParted program so here are some screenshots:

[IMG]http://home.comcast.net/~ghen/lin/Screenshot--dev-sdb.png[/IMG]
[IMG]http://home.comcast.net/~ghen/lin/Screenshot--dev-sda.png[/IMG]

I have no idea what to put in the menu.lst file to give me access to XP. Help please. :)


edit: after looking at the information again.. it seems like vista's boot loader is on the drive with my XP install (same one as the fat32 recovery partition for xp) that might complicate things.

---

### Post by caljohnsmith on 2008-10-22
How about first posting the output of the following so we can get a better picture of your setup and see where your XP/Vista boot files are (do it from a terminal in Applications > Accessories > Terminal):
```

sudo fdisk -lu
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
```
Where "-l" is a lowercase L.

---

### Post by ghen on 2008-10-22
```
jason@copeland-linux:~$ sudo fdisk -lu
[sudo] password for jason: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79ed79ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    12562830   156296384    71866777+   7  HPFS/NTFS
/dev/sda2              63    12562829     6281383+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdacbf7e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    67110911    33554432    7  HPFS/NTFS
/dev/sdb2        67119570    71103689     1992060   82  Linux swap / Solaris
/dev/sdb3        71103690   156296384    42596347+  83  Linux
jason@copeland-linux:~$ sudo mkdir /mnt/sda1 /mnt/sdb1
jason@copeland-linux:~$ sudo mount /dev/sda1 /mnt/sda1
jason@copeland-linux:~$ sudo mount /dev/sdb1 /mnt/sdb1
jason@copeland-linux:~$ ls -l /mnt/sda1 /mnt/sdb1
/mnt/sda1:
total 1561387
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 AUTOEXEC.BAT
drwxrwxrwx 1 root root       4096 2008-10-21 19:06 Boot
-rwxrwxrwx 1 root root        355 2008-10-21 19:06 Boot.BAK
-rwxrwxrwx 1 root root        103 2008-03-14 14:23 BootErr.log
-rwxrwxrwx 1 root root        355 2008-10-21 18:11 boot.ini
-rwxrwxrwx 1 root root     333203 2008-01-20 21:22 bootmgr
-rwxrwxrwx 1 root root       8192 2008-10-21 19:06 BOOTSECT.BAK
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-10-15 08:11 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-10-15 15:33 F@h 1
drwxrwxrwx 1 root root       4096 2008-10-15 15:41 F@h 2
drwxrwxrwx 1 root root          0 2008-03-12 16:03 Intel
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 IO.SYS
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-03-14 14:35 MSOCache
drwxrwxrwx 1 root root          0 2008-03-12 16:07 MyWorks
drwxrwxrwx 1 root root          0 2008-03-14 14:43 NextgenLC
-rwxrwxrwx 1 root root      47564 2007-07-27 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-10-15 14:26 ntldr
-rwxrwxrwx 1 root root         16 2007-01-28 07:15 OFFTAG.txt
-rwxrwxrwx 1 root root 1598029824 2008-10-22 14:38 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-10-17 14:30 Program Files
drwxrwxrwx 1 root root       4096 2008-10-21 15:47 $RECYCLE.BIN
drwxrwxrwx 1 root root       4096 2008-10-15 08:16 RECYCLER
-rwxrwxrwx 1 root root        575 2008-03-12 16:09 RHDSetup.log
drwxrwxrwx 1 root root       4096 2008-03-14 15:21 _rpcs
drwxrwxrwx 1 root root       4096 2008-03-14 14:32 System Volume Information
drwxrwxrwx 1 root root      12288 2008-06-18 11:05 temp
drwxrwxrwx 1 root root     122880 2008-10-22 14:45 WINDOWS

/mnt/sdb1:
total 2381689
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
-rwxrwxrwx 2 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 08:00 Documents and Settings
-rwxrwxrwx 1 root root 1062469632 2008-10-21 14:40 hiberfil.sys
-rwxrwxrwx 1 root root 1376346112 2008-10-21 14:40 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-20 21:30 PerfLogs
drwxrwxrwx 1 root root       4096 2006-11-02 08:00 ProgramData
drwxrwxrwx 1 root root       4096 2006-11-02 08:00 Program Files
drwxrwxrwx 1 root root          0 2008-10-21 15:47 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2008-10-22 14:39 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-21 15:46 Users
drwxrwxrwx 1 root root      16384 2008-10-21 16:02 Windows
jason@copeland-linux:~$ 

```

---

### Post by caljohnsmith on 2008-10-22
Your right, it looks like Vista put all its boot files in your Win XP partition on sda1. I would recommend putting all of Vista's boot files back in the Vista partition, and then we can work on booting XP and Vista separately. You'll need both your Windows XP and Vista Install CDs, so make sure you have them handy. 

If that sounds good to you, then start with the following:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv /mnt/sda1/boot /mnt/sdb1/.
sudo mv /mnt/sda1/boot.mgr /mnt/sdb1/.

```

Next boot your Windows XP Install CD, go to the "recovery console" and do:
```
map
```
From that, figure out the drive letter for the XP install on sda1, and then do:
```
fixboot <drive>
chkdsk /r <drive>
```
Where <drive> is the XP drive letter. Then boot your Vista Install CD, go to the command line, and run: 
```
bootrec /fixboot
bootrec /rebuildbcd
```
Also, you are currently booting from your Windows XP sda drive on start up, because Grub must be in the MBR (Master Boot Record) of that drive. That's not exactly ideal, because then if anything happens to either of your drives, you won't be able to boot the other one. It is more ideal if you can set your BIOS to boot the Ubuntu drive on start up, and we can easily install the Grub to the MBR of the Ubuntu drive and reinstall a Windows MBR to the Win XP drive. That way if anything happens to the Ubuntu drive, you will be able to boot the Windows XP drive, and vice versa. Does this sound good to you?

---

### Post by ghen on 2008-10-23
sounds like fun =) I'll get right on your suggestions and post back when I'm able.

---

### Post by ghen on 2008-10-24
Success! It wasn't exact, but I adjusted things to their new happy homes. Thanks! here is my new menu.lst with the piece I added for vista:

```
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
# kopt=root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ca1dc1d9-20b8-41ef-9626-a8c2a8ddfc7e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (recovery - PC Angel)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

#added by ghen
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

and the ls -l that you asked for before:
```
jason@copeland-linux:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79ed79ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    12562830   156296384    71866777+   7  HPFS/NTFS
/dev/sda2              63    12562829     6281383+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdacbf7e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    67110911    33554432    7  HPFS/NTFS
/dev/sdb2        67119570    71103689     1992060   82  Linux swap / Solaris
/dev/sdb3        71103690   156296384    42596347+  83  Linux
jason@copeland-linux:~$ sudo mount /dev/sda1 /mnt/sda1
jason@copeland-linux:~$ sudo mount /dev/sdb1 /mnt/sdb1
jason@copeland-linux:~$ ls -l /mnt/sda1 /mnt/sdb1
/mnt/sda1:
total 1561055
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 AUTOEXEC.BAT
drwxrwxrwx 1 root root          0 2008-10-24 13:20 Boot
-rwxrwxrwx 1 root root        355 2008-10-21 19:06 Boot.BAK
-rwxrwxrwx 1 root root        103 2008-03-14 14:23 BootErr.log
-rwxrwxrwx 1 root root        355 2008-10-21 18:11 boot.ini
-rwxrwxrwx 1 root root       8192 2008-10-21 19:06 BOOTSECT.BAK
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-10-15 08:11 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-10-15 15:33 F@h 1
drwxrwxrwx 1 root root       4096 2008-10-15 15:41 F@h 2
drwxrwxrwx 1 root root          0 2008-03-12 16:03 Intel
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 IO.SYS
-rwxrwxrwx 1 root root          0 2007-11-02 12:30 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-03-14 14:35 MSOCache
drwxrwxrwx 1 root root          0 2008-03-12 16:07 MyWorks
drwxrwxrwx 1 root root          0 2008-03-14 14:43 NextgenLC
-rwxrwxrwx 1 root root      47564 2007-07-27 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-10-15 14:26 ntldr
-rwxrwxrwx 1 root root         16 2007-01-28 07:15 OFFTAG.txt
-rwxrwxrwx 1 root root 1598029824 2008-10-24 14:13 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-10-17 14:30 Program Files
drwxrwxrwx 1 root root       4096 2008-10-21 15:47 $RECYCLE.BIN
drwxrwxrwx 1 root root       4096 2008-10-15 08:16 RECYCLER
-rwxrwxrwx 1 root root        575 2008-03-12 16:09 RHDSetup.log
drwxrwxrwx 1 root root       4096 2008-03-14 15:21 _rpcs
drwxrwxrwx 1 root root       4096 2008-03-14 14:32 System Volume Information
drwxrwxrwx 1 root root      12288 2008-06-18 11:05 temp
drwxrwxrwx 1 root root     122880 2008-10-24 14:13 WINDOWS

/mnt/sdb1:
total 1037933
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-10-21 19:06 Boot
-rwxrwxrwx 1 root root     333203 2008-01-20 21:22 bootmgr
-rwxrwxrwx 2 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 08:00 Documents and Settings
-rwxrwxrwx 1 root root 1062469632 2008-10-21 14:40 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-01-20 21:30 PerfLogs
drwxrwxrwx 1 root root       4096 2006-11-02 08:00 ProgramData
drwxrwxrwx 1 root root       4096 2006-11-02 08:00 Program Files
drwxrwxrwx 1 root root          0 2008-10-21 15:47 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2008-10-22 14:39 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-21 15:46 Users
drwxrwxrwx 1 root root      16384 2008-10-21 16:02 Windows
jason@copeland-linux:~$ 

```

Now, vista still runs its own bootloader but I think I can handle that.

---

### Post by caljohnsmith on 2008-10-24
That's great news that things are working. One thing I was going to mention is that Ubuntu uses (hd1,2) in the menu.lst, so that means you must be booting from your Windows XP drive, not the Ubuntu + Vista drive; that also means that Grub is installed to the MBR (Master Boot Record) of you Windows XP drive. The disadvantage of that is if anything happens to either drive, you won't be able to boot either one.

I would recommend reinstalling a Windows MBR to your Windows XP drive, and then installing Grub to your Ubuntu drive; that way if anything happens to either drive, you will still be able to boot the other one. To make it work you would need to set your BIOS to boot the Ubuntu drive first on start up. If you are interested in doing this, let me know, and I can give you the specifics of how to do it. :)

And by the way, a great program for modifying your Vista boot menu is [EasyBCD]("http://neosmart.net/dl.php?id=1"). You may want to give it a shot.

---

