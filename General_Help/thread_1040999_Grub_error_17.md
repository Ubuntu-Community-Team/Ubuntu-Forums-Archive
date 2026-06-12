---
title: "Grub error 17"
date: 2009-01-16
forum: General Help
---

### Post by k3v1n83 on 2009-01-16
I've got a quad-boot system (XP, Vista, 7 beta and Ubuntu all installed one hard drive). When I start my pc the pc should firstly go through grub menu and give me the options to start ubuntu or go to the window boot loader, if I do the latter I should get the choice of XP, Vista or 7 beta. 

The problem is all I get now is "Grub 1.5 Error 17" when I boot my pc. Now if I put my ubuntu disk in and boot from that and choose the "boot from frist hard disk" I get a normal startup as described above.

I no expert when it comes to linux and I am still trying linux out, my best guess is the grub boot loader is just broken but I have no idea how to fix it. Thanks in advance for any help.

---

### Post by Tim Sharitt on 2009-01-16
You probably just need to reinstall grub on the MBR. Boot your live cd, open a terminal and do the following

```
sudo grub
```
```
find /boot/grub/stage1
```
Using this information, set the root device (fill in X,Y with whatever the find command returned): 
```
root (hdx,y)
```
```
setup (hd0)
```
```
quit
```

Now reboot to see if that worked.

---

### Post by k3v1n83 on 2009-01-16
I tried that, didn't work, then thought since I got hd(2,6) back from the find command I would try ```
setup (hd2)
```
and success I get to the grub boot loader and can boot Ubuntu.

Next probem is although I get the option to go to the windows boot loader I get a message saying as follows

```

Error 12: Invalid device requested

Press any key to continue...

```

Edit:

Ok, thought I seem to be getting somewhere, I hit "e" when I had the windows option selected in grub and got this
 
```

root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```

I started changing the numbers in the root line and found that "root (hd0,0)" gave me the windows boot loader but when I try load XP, the pc instantly restarts, Vista and 7 boot fine. Firstly how do get the "root (hd0,0)" to stay that way as it keeps reverting to "root (hd2,0)" and any ideas why XP wont boot?

---

### Post by Tim Sharitt on 2009-01-16
Does XP show up on the Vista or Windows 7 bootloader? It is my understanding that Vista (an likely Windows 7) will usually remove the bootloader from the XP partition and add an entry I it's respective bootloader. 
You could try to run fixmbr from the XP boot cd to restore it's bootloader and then re-install grub from the Ubuntu live CD afterwards.

---

### Post by k3v1n83 on 2009-01-16
XP shows in the 7 bootloader (as "prevous version of windows") but when I select it the pc restarts, so something seems to have gone wrong in the xp boot process. I did think of what you suggested but that (probably) would remove my abiltiy to get into vista and 7. 

I suppose, as long as the fixmbr worked on xp, worst case I could just reinstall Vista, 7 and Ubuntu. I just don't want to start again with XP.

ps, How do get the "root (hd0,0)" to stay that way as it keeps reverting to "root (hd2,0)"?

Thanks

---

### Post by Tim Sharitt on 2009-01-16
If I recall correctly, XP doesn't overwrite the boot loaders of other windows installations, it is a feature introduced in Vista's boot loader and likely carried over to Windows 7. There was probably an error adding XP to Windows 7's boot loader, which may be repairable from windows (probably something in C:\boot.ini but I'm not really sure). 

On the problem with getting the menu entry to stay as (hd0,0). Are you editing the /boot/grub/menu.lst with root priviledges or editing from grub on startup. Any editing at start up will not stay an permanent changes must be made as root to the menu.lst file.

---

### Post by k3v1n83 on 2009-01-16
Thanks for the advice, now too tired, will try again later.

---

### Post by caljohnsmith on 2009-01-16
k3v1n83, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by k3v1n83 on 2009-01-17
caljohnsmith, heres my results.txt

```
============================= Boot Info Summary: ==============================

 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       swap

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1577778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   625137344   312560640    f  W95 Ext'd (LBA)
/dev/sda5           16128   625137344   312560608+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdac56f87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   625137344   312560640    f  W95 Ext'd (LBA)
/dev/sdb5           16128   625137344   312560608+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe83eab9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    62910539    31455238+   7  HPFS/NTFS
/dev/sdc2        62912512   167766015    52426752    7  HPFS/NTFS
/dev/sdc3       167766016   230680575    31457280    7  HPFS/NTFS
/dev/sdc4       230693400   625137344   197221972+   5  Extended
/dev/sdc5       624141378   625137344      497983+  82  Linux swap / Solaris
/dev/sdc6       290680173   624141314   166730571    7  HPFS/NTFS
/dev/sdc7       230693526   290664044    29985259+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdc:

Warning: partition 2 does not start at a cylinder boundary

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="84886E6C886E5CA4" LABEL="Music" TYPE="ntfs" 
/dev/sdb5: UUID="9A0C13EC0C13C265" LABEL="Games" TYPE="ntfs" 
/dev/sdc1: UUID="4C28B3D428B3BB72" LABEL="XP" TYPE="ntfs" 
/dev/sdc2: UUID="FE7895017894B9BB" LABEL="Vista" TYPE="ntfs" 
/dev/sdc3: UUID="362C9A022C99BCF5" LABEL="7" TYPE="ntfs" 
/dev/sdc5: UUID="80413627-8c1b-4209-95f0-aec7f24f6566" TYPE="swap" 
/dev/sdc6: UUID="C4946B64946B57C6" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc7: UUID="083d0b10-1f30-4afd-a3a9-ada21fbf360d" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=kevin)

================================ sdc1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


================================== sdc1/Boot: ==================================

total 616
drwxrwxrwx 1 root root   4096 2009-01-12 21:20 .
drwxrwxrwx 1 root root  16384 2009-01-17 09:19 ..
-rwxrwxrwx 1 root root  32768 2009-01-12 14:22 BCD
-rwxrwxrwx 1 root root  29696 2009-01-12 14:04 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-08-25 21:26 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-08-25 21:26 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-12 21:20 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-12 21:20 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-12 21:20 da-DK
drwxrwxrwx 1 root root      0 2009-01-12 21:20 de-DE
drwxrwxrwx 1 root root      0 2009-01-12 21:20 el-GR
drwxrwxrwx 1 root root      0 2009-01-12 21:20 en-US
drwxrwxrwx 1 root root      0 2009-01-12 21:20 es-ES
drwxrwxrwx 1 root root      0 2009-01-12 21:20 fi-FI
drwxrwxrwx 1 root root   4096 2009-01-12 21:20 Fonts
drwxrwxrwx 1 root root      0 2009-01-12 21:20 fr-FR
drwxrwxrwx 1 root root      0 2009-01-12 21:20 hu-HU
drwxrwxrwx 1 root root      0 2009-01-12 21:20 it-IT
drwxrwxrwx 1 root root      0 2009-01-12 21:20 ja-JP
drwxrwxrwx 1 root root      0 2009-01-12 21:20 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 07:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-12 21:20 nb-NO
drwxrwxrwx 1 root root      0 2009-01-12 21:20 nl-NL
drwxrwxrwx 1 root root      0 2009-01-12 21:20 pl-PL
drwxrwxrwx 1 root root      0 2009-01-12 21:20 pt-BR
drwxrwxrwx 1 root root      0 2009-01-12 21:20 pt-PT
drwxrwxrwx 1 root root      0 2009-01-12 21:20 ru-RU
drwxrwxrwx 1 root root      0 2009-01-12 21:20 sv-SE
drwxrwxrwx 1 root root      0 2009-01-12 21:20 tr-TR
drwxrwxrwx 1 root root      0 2009-01-12 21:20 zh-CN
drwxrwxrwx 1 root root      0 2009-01-12 21:20 zh-HK
drwxrwxrwx 1 root root      0 2009-01-12 21:20 zh-TW

=========================== sdc7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=083d0b10-1f30-4afd-a3a9-ada21fbf360d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=083d0b10-1f30-4afd-a3a9-ada21fbf360d

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
uuid		083d0b10-1f30-4afd-a3a9-ada21fbf360d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=083d0b10-1f30-4afd-a3a9-ada21fbf360d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		083d0b10-1f30-4afd-a3a9-ada21fbf360d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=083d0b10-1f30-4afd-a3a9-ada21fbf360d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		083d0b10-1f30-4afd-a3a9-ada21fbf360d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc7
UUID=083d0b10-1f30-4afd-a3a9-ada21fbf360d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=80413627-8c1b-4209-95f0-aec7f24f6566 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc7/boot: ==================================

total 12808
drwxr-xr-x  3 root root    4096 2009-01-12 15:37 .
drwxr-xr-x 20 root root    4096 2009-01-12 15:37 ..
-rw-r--r--  1 root root  503560 2008-10-24 08:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 08:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-12 15:38 grub
-rw-r--r--  1 root root 8644990 2009-01-12 15:37 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 08:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 08:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 08:55 vmlinuz-2.6.27-7-generic

=============================== sdc7/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-12 15:38 .
drwxr-xr-x 3 root root   4096 2009-01-12 15:37 ..
-rw-r--r-- 1 root root    197 2009-01-12 15:37 default
-rw-r--r-- 1 root root     45 2009-01-12 15:37 device.map
-rw-r--r-- 1 root root   8108 2009-01-12 15:37 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-12 15:37 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-12 15:37 installed-version
-rw-r--r-- 1 root root   8712 2009-01-12 15:37 jfs_stage1_5
-rw-r--r-- 1 root root   4653 2009-01-12 15:38 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-12 15:37 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-12 15:37 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-12 15:37 stage1
-rw-r--r-- 1 root root 121460 2009-01-12 15:37 stage2
-rw-r--r-- 1 root root   9556 2009-01-12 15:37 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
```

Tim Sharitt, I had been editing on startup, ive now changed it in menu.lst.

---

### Post by caljohnsmith on 2009-01-17
K3v1n83, I think the reason you are getting a Grub error 17 is because you are booting the sda drive on start up; your sdc Ubuntu drive looks like it is all set to boot properly, so how about going into your BIOS and change the boot order so that the Ubuntu sdc drive boots first. That should allow you to boot into Ubuntu, but booting Windows from your Grub menu probably won't work with the way it is currently configured. If booting into Ubuntu works but Windows doesn't, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to be:
```
title		Windows
root		(hd0,0)
chainloader	+1

```
Then reboot, and let me know exactly what happens when you choose the Windows entry. It looks like you will probably get the Windows boot menu where you can choose between your various Windows installations, but let me know how it goes.

---

### Post by k3v1n83 on 2009-01-17
Im no longer getting the error 17, i fixed that with Tim Sharitt first post. After I did that I got the problem getting to the windows bootloader from grub, that was fixed by changing the line "root (hd2,0)" to "root (hd0,0)" in menu.lst as you suggested in your last post. 

The problem I am now having is when I get to the windows bootloader (where i have the option to boot XP, Vista or 7) choosing XP just restarts the pc, choosing vista or 7 works fine.

But when I was getting the grub error 17 and was using my ubuntu cd to get to the grub bootloader all OS's booted fine. In this whole process Ive somehow managed to break XP's boot process.

Hope that makes sense.

---

### Post by caljohnsmith on 2009-01-17
OK, how about booting into either Windows 7 or Vista, download [EasyBCD]("http://neosmart.net/dl.php?id=1"), and try using that to add Windows XP to your Vista/Win7 boot menu. Let me know how that goes.

---

### Post by k3v1n83 on 2009-01-17
Ive ran EasyBCD and this is what is coming up.

1. Error saying it can't detect BCD boot data and MBR are either not latest version or don't exist. "yes" to fix. I press "yes"

2. Unforunately it could detect the drive letter of my boot device. Possilbly beause of a non-standard MBR or 3rd party bootloader. please select boot drive letter. I leave at C:\, then click OK

3. It say its will attempt to recreate the BCD entry from scratch, then it asks for the target of the default boot target. I leave at c:\ and click OK.

4. "The store import operation has failed. The requested system device cannot be found." is what i get. I hit OK, it goes back to the start. I have tried various combination of drive letters to see if anything happened but to no avail.

Ive tried on vista and 7.

I tried to get into bcdedit from both OS's from the command line and get the error "The boot configuratipn data store could not be opened. Access is denied.".

Just a thought, if you read back on the thread to the 2nd and 3rd post when I was trying to fix the initial problem and Tim Sharitt asked to enter this in to the terminal

```
sudo grub
find /boot/grub/stage1
root (hd2,6)  <-- thats what i entered as that what was returned from the previous command
setup (hd0)
quit
```

but that initially didn't work but when I changed the above to

```
sudo grub
find /boot/grub/stage1
root (hd2,6)
setup (hd2) <--- the change
quit
```

that did work, but could I have accidently overwritten the first little bit of the XP partition in my first causing it not to work?

---

### Post by caljohnsmith on 2009-01-17
Using "setup (hd0)" installs Grub to the MBR of your sda drive, and it looks like that drive just has a data NTFS partition on it anyway; so that shouldn't hurt anything. Which partitions are Win 7 and Vista on? It looks like they are on sdc2 and sdc3, but which is which? Right now all your Windows boot files for Vista, Win7, and XP are all mixed up together in the sdc1 XP partition; that can work, but I would suggest we move the Vista and Win7 boot files back to their own partitions, reconfigure everything, and then you should be able to boot all your Windows partitions separate in the Grub menu without having to go through the Windows boot loader. Does that sound like maybe what you would want?

---

### Post by k3v1n83 on 2009-01-17
To your first question, I had previously labeled each partiton so I knew what was on what so this should answer that. From my results.txt

```
blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="84886E6C886E5CA4" LABEL="Music" TYPE="ntfs" 
/dev/sdb5: UUID="9A0C13EC0C13C265" LABEL="Games" TYPE="ntfs" 
/dev/sdc1: UUID="4C28B3D428B3BB72" LABEL="XP" TYPE="ntfs" 
/dev/sdc2: UUID="FE7895017894B9BB" LABEL="Vista" TYPE="ntfs" 
/dev/sdc3: UUID="362C9A022C99BCF5" LABEL="7" TYPE="ntfs" 
/dev/sdc5: UUID="80413627-8c1b-4209-95f0-aec7f24f6566" TYPE="swap" 
/dev/sdc6: UUID="C4946B64946B57C6" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc7: UUID="083d0b10-1f30-4afd-a3a9-ada21fbf360d" TYPE="ext3"
``` 

And to your second question, although having to got through 2 bootloaders was fine to me, only having grub would be good, I cant see any harm in it.

---

### Post by caljohnsmith on 2009-01-17
OK, thanks, I missed the fact that you had disk labels identifying the partitions. How about following step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") in order to restore the boot files back to the Vista and Win7 partitions and configure them. I think Win7 and Vista are alike about the initial booting process in that they both use bootmgr and the /Boot BCD folder, so I think you can restore the boot files to both Vista and Win7 from just the Win7 Install CD. Let me know how that goes.

---

