---
title: "Trying to triple boot with Grub"
date: 2009-01-21
forum: General Help
---

### Post by PoopyTheJ on 2009-01-21
I've installed XP and windows 7 and Ubuntu on my computer I succesfully reloaded grub to boot into Ubuntu and now I can't get into windows 7. I' get an error 29: Disk write error when trying to boot Win7 or XP.
Here is the output of sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56975697

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4001    32136192    7  HPFS/NTFS - [COLOR="Red"]This is Windows 7[/COLOR]
/dev/sda2            4002        6433    19535040   83  Linux
/dev/sda3            6434       30151   190514835   83  Linux
/dev/sda4           30152       30401     2008125   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8d4a8d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e0a9e0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+   7  HPFS/NTFS  - [COLOR="Red"]This is XP[/COLOR]
/dev/sdc2            2551       19457   135805477+  83  Linux


And here is the relevant section of boot/grub/menu.lst

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
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
rootnoverify		(hd0,0)
savedefault
chainloader	+1

title		Windows XP
rootnoverify		(hd2,0)
savedefault
chainloader	+1

---

### Post by kk9 on 2009-01-21
My wife's installer-generated menu.lst has this:

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

I suspect the makeactive is what you are missing.

---

### Post by PoopyTheJ on 2009-01-22
with or without makeactive I get the same error. Thanks for the idea though!

---

### Post by PoopyTheJ on 2009-01-22
Ok, I commented out the savedefault on both WinXP and the Vista entry and now when I choose vista it boots to XP when I choose XP I get the error 29 message.

---

### Post by caljohnsmith on 2009-01-22
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by PoopyTheJ on 2009-01-22
Ok, thanks for the reply, I'm currently at work so when I get home this evening I'll get that done!

---

### Post by PoopyTheJ on 2009-01-23
Results of Script below sorry it took me so long fighting a cold and my kids take a lot of time...
```

============================ Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda3 already mounted or sda3 busy
mount: according to mtab, /dev/sda3 is mounted on /media/disk

sda4: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdc2 already mounted or sdc2 busy
mount: according to mtab, /dev/sdc2 is mounted on /media/disk-2

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x56975697

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *         2,048   64,274,431   64,272,384   7 HPFS/NTFS
/dev/sda2         64,276,065  103,346,144   39,070,080  83 Linux
/dev/sda3        103,346,145  484,375,814  381,029,670  83 Linux
/dev/sda4        484,375,815  488,392,064    4,016,250  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d4a8d4

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  488,392,064  488,392,002  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e0a9e0a

Partition  Boot        Start          End         Size  Id System

/dev/sdc1                 63   40,965,749   40,965,687   7 HPFS/NTFS
/dev/sdc2         40,965,750  312,576,704  271,610,955  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E0A0C0F8A0C0D5E6" TYPE="ntfs" 
/dev/sda2: UUID="83c205f6-4edd-49e3-a268-c0ea83b3a05d" TYPE="ext3" 
/dev/sda3: UUID="23d87db5-b92e-416a-98f8-30edc202cd82" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="b8056c03-d47e-4ea7-a3fa-eed66946515e" 
/dev/sdb1: UUID="65226ddc-32d5-4c5a-a0b3-3d243285a8da" TYPE="ext2" 
/dev/sdc1: UUID="DCE02942E02923EC" TYPE="ntfs" 
/dev/sdc2: UUID="8bb92445-a648-4d09-adba-0765b9df049a" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/disk type ext2 (rw)
/dev/sdb1 on /media/disk-1 type ext2 (rw)
/dev/sdc2 on /media/disk-2 type ext2 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/poopythej/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=poopythej)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

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
# kopt=root=UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
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
rootnoverify		(hd0,0)
makeactive
#savedefault
chainloader	+1

title		Windows XP
rootnoverify		(hd2,0)
makeactive
#savedefault
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=83c205f6-4edd-49e3-a268-c0ea83b3a05d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=b8056c03-d47e-4ea7-a3fa-eed66946515e none            swap    sw              0       0
# /dev/sda3
UUID="23d87db5-b92e-416a-98f8-30edc202cd82"	/media/disk	ext2	defaults	0	2
# /dev/sdb1
UUID="65226ddc-32d5-4c5a-a0b3-3d243285a8da"	/media/disk-1	ext2	defaults	0	2
# /dev/sdc2
 UUID="8bb92445-a648-4d09-adba-0765b9df049a"	/media/disk-2	ext2	defaults	0	2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location  of files loaded by Grub: ===================


  40.1GB: boot/grub/menu.lst
  40.1GB: boot/grub/stage2
  40.0GB: boot/initrd.img-2.6.24-19-generic
  39.9GB: boot/initrd.img-2.6.24-19-generic.bak
  39.9GB: boot/initrd.img-2.6.24-23-generic
  40.0GB: boot/initrd.img-2.6.24-23-generic.bak
  39.9GB: boot/vmlinuz-2.6.24-19-generic
  40.0GB: boot/vmlinuz-2.6.24-23-generic
  39.9GB: initrd.img
  40.0GB: initrd.img.old
  40.0GB: vmlinuz
  39.9GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-23
It looks like you installed XP after Win7, is that true? I would recommend moving your XP boot files back to the XP partition, fixing the Win7 partition boot sector, and then you should be able to boot Win 7 or XP separately from your Grub menu. If that sounds good to you, how about doing:
```
sudo mkdir /mnt/sda1 /mnt/sdc1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdc1 /mnt/sdc1
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sdc1
```
Then pull up your boot.ini file:
```
gksudo gedit /mnt/sdc1/boot.ini
```
And change the "rdisk(2)" to "rdisk(0)" like:
```
[boot loader]
timeout=30
default=multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your existing Windows entries with the following three entries:
```

title Windows 7
rootnoverify (hd0,0)
chainloader +1

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
I think the 3rd entry will most likely work for XP, because it is likely that your XP sdc drive is 3rd in the BIOS boot order; but we should include the other (hd1) entry in case your sdc drive is actually 2nd in the BIOS boot order. Next boot your Win7 Install CD, go to the command line and do:
```
bootrec /fixboot
```
Then reboot, try both Win7 and XP from the Grub menu, and let me know exactly what happens when you try each entry. We can work from there if you want.

---

### Post by PoopyTheJ on 2009-01-23
Ok, I'm in windows xp now setting it up you're right I installed XP after 7 I'll reboot as soon as I get these video drivers installed and go through that, thank you very much for your help. So is basically what I did was overwrote the Win7 boot files with XP? And if so how do the boot files for each OS work together? I mean the win installs both want to be on the first physical disk right? So are we tricking XP or... Thanks for the help!

---

### Post by PoopyTheJ on 2009-01-24
It worked and though I think I understand what happened with what you had me do Windows is wierd. Thanks for the help!

---

### Post by caljohnsmith on 2009-01-24
Glad that worked OK; cheers and enjoy XP, Win7, and Ubuntu. :)

---

