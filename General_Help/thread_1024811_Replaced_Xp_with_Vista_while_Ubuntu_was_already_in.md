---
title: "Replaced Xp with Vista while Ubuntu was already installed and now not booting"
date: 2008-12-29
forum: General Help
---

### Post by tarutaruomen on 2008-12-29
Hello, I had setup a windows xp/Ubuntu 8.10 to dual boot in my machine.  however i recently purchased a copy of windows vista to upgrade windows xp.  Thing is I just formatted the Windows partition and installed Vista there but now it won't boot because a bootmgr is not available.  The windows partition is in one drive and the ubuntu installation is in the other.  Ubuntu boots perfectly but I have no idea how to change grub to load the new Vista installation.

If you need any additional info let me know ^^ thank you

---

### Post by mikewhatever on 2008-12-29
You need to post the output of <sudo fdisk -l> command from Applications/Accessories/Terminal.

---

### Post by tarutaruomen on 2008-12-29
output is as follows 
```

Disk /dev/sda: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xd41c07e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     1453517   732572536+   7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65695290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdf2           12749       60801   385985722+   5  Extended
/dev/sdf5           12749       13495     6000246   82  Linux swap / Solaris
/dev/sdf6           13496       19720    50002281   83  Linux
/dev/sdf7           19721       60801   329983101   83  Linux

```

---

### Post by Arenlor on 2008-12-29
I have vista as:
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

That's in /boot/grub/menu.lst which you need to be root to edit:
```
sudo nano /boot/grub/menu.lst
```
Add those lines to the bottom, and edit the part that says (hd0,0) to whatever your XP was.

---

### Post by tarutaruomen on 2008-12-29
so far i tried 
grub>setup (hd0) but it doesn't work either
:(
i just don't want to erase everything since i  spent some time tweaking it to my tastes.
gives me this error Invalid device requested.

---

### Post by Arenlor on 2008-12-29
Can you post the current contents of /boot/grub/menu.lst please?

---

### Post by caljohnsmith on 2008-12-29
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it would take to boot Vista from Grub.

---

### Post by tarutaruomen on 2008-12-29
Here it goes:

```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd41c07e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1465145135   732572536+   7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65695290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       204796620   976768064   385985722+   5  Extended
/dev/sdb5       204796683   216797174     6000246   82  Linux swap / Solaris
/dev/sdb6       216797238   316801799    50002281   83  Linux
/dev/sdb7       316801863   976768064   329983101   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

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

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="5AAC10F7AC10CEFF" LABEL="BackupII" TYPE="ntfs" 
/dev/sdb1: UUID="B096AE8B96AE51A0" TYPE="ntfs" 
/dev/sdb5: UUID="67666581-b14b-4035-9269-8ff9eabcc70c" TYPE="swap" 
/dev/sdb6: UUID="cebb9ae4-8551-4b46-abbb-29609820f38f" TYPE="ext3" 
/dev/sdb7: UUID="cd05645c-4824-4def-83ae-7528973c202a" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/darkomen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darkomen)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=darkomen)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


================================== sda1/Boot: ==================================

total 504
drwxrwxrwx 1 root root   4096 2008-12-29 16:38 .
drwxrwxrwx 1 root root   8192 2008-12-29 16:38 ..
-rwxrwxrwx 1 root root  24576 2008-12-29 16:49 BCD
-rwxrwxrwx 1 root root  21504 2008-12-29 16:48 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-29 16:32 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-29 16:32 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-29 16:38 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-29 16:32 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-29 16:32 da-DK
drwxrwxrwx 1 root root      0 2008-12-29 16:32 de-DE
drwxrwxrwx 1 root root      0 2008-12-29 16:32 el-GR
drwxrwxrwx 1 root root      0 2008-12-29 16:38 en-US
drwxrwxrwx 1 root root      0 2008-12-29 16:32 es-ES
drwxrwxrwx 1 root root      0 2008-12-29 16:32 fi-FI
drwxrwxrwx 1 root root      0 2008-12-29 16:38 Fonts
drwxrwxrwx 1 root root      0 2008-12-29 16:32 fr-FR
drwxrwxrwx 1 root root      0 2008-12-29 16:32 hu-HU
drwxrwxrwx 1 root root      0 2008-12-29 16:32 it-IT
drwxrwxrwx 1 root root      0 2008-12-29 16:32 ja-JP
drwxrwxrwx 1 root root      0 2008-12-29 16:32 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 05:51 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-29 16:32 nb-NO
drwxrwxrwx 1 root root      0 2008-12-29 16:32 nl-NL
drwxrwxrwx 1 root root      0 2008-12-29 16:32 pl-PL
drwxrwxrwx 1 root root      0 2008-12-29 16:32 pt-BR
drwxrwxrwx 1 root root      0 2008-12-29 16:32 pt-PT
drwxrwxrwx 1 root root      0 2008-12-29 16:32 ru-RU
drwxrwxrwx 1 root root      0 2008-12-29 16:32 sv-SE
drwxrwxrwx 1 root root      0 2008-12-29 16:32 tr-TR
drwxrwxrwx 1 root root      0 2008-12-29 16:32 zh-CN
drwxrwxrwx 1 root root      0 2008-12-29 16:32 zh-HK
drwxrwxrwx 1 root root      0 2008-12-29 16:32 zh-TW

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
# kopt=root=UUID=cebb9ae4-8551-4b46-abbb-29609820f38f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cebb9ae4-8551-4b46-abbb-29609820f38f

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
uuid		cebb9ae4-8551-4b46-abbb-29609820f38f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cebb9ae4-8551-4b46-abbb-29609820f38f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cebb9ae4-8551-4b46-abbb-29609820f38f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cebb9ae4-8551-4b46-abbb-29609820f38f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cebb9ae4-8551-4b46-abbb-29609820f38f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdg6
UUID=cebb9ae4-8551-4b46-abbb-29609820f38f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdg7
UUID=cd05645c-4824-4def-83ae-7528973c202a /home           ext3    relatime        0       2
# /dev/sdg5
UUID=67666581-b14b-4035-9269-8ff9eabcc70c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb6/boot: ==================================

total 14364
drwxr-xr-x  3 root root     4096 2008-12-19 16:05 .
drwxr-xr-x 22 root root     4096 2008-12-19 16:05 ..
-rw-r--r--  1 root root   503560 2008-11-04 16:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root    85316 2008-11-04 16:53 config-2.6.27-7-generic
drwxr-xr-x  3 root root     4096 2008-12-19 21:29 grub
-rw-r--r--  1 root root 10237605 2008-12-19 16:05 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root   124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root  1352144 2008-11-04 16:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root     1130 2008-11-04 16:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root  2339712 2008-10-24 03:55 vmlinuz-2.6.27-7-generic

=============================== sdb6/boot/grub: ===============================

total 244
drwxr-xr-x 3 root root   4096 2008-12-19 21:29 .
drwxr-xr-x 3 root root   4096 2008-12-19 16:05 ..
-rw-r--r-- 1 root root    197 2008-12-19 16:05 default
-rw-r--r-- 1 root root     45 2008-12-19 16:05 device.map
-rw-r--r-- 1 root root   8108 2008-12-19 16:05 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-19 16:05 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-19 16:05 installed-version
-rw-r--r-- 1 root root   8712 2008-12-19 16:05 jfs_stage1_5
-rw-r--r-- 1 root root   4875 2008-12-19 21:28 menubak.lst
-rw-r--r-- 1 root root   4598 2008-12-19 21:28 menubak.lst~
-rw-r--r-- 1 root root   4597 2008-12-19 21:29 menu.lst
-rw-r--r-- 1 root root   4875 2008-12-19 16:05 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-19 16:05 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-19 16:05 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-06 17:24 splashimages
-rw-r--r-- 1 root root    512 2008-12-19 16:05 stage1
-rw-r--r-- 1 root root 121460 2008-12-19 16:05 stage2
-rw-r--r-- 1 root root   9556 2008-12-19 16:05 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
```

---

### Post by tarutaruomen on 2008-12-29
wow that's a nice script!! mind if i keep it to use?

---

### Post by caljohnsmith on 2008-12-29
[QUOTE=tarutaruomen]wow that's a nice script!! mind if i keep it to use?[/QUOTE]
Sure, you can keep it and use it :); you might actually want to keep the web link instead, because the script is being updated quite often right now. If you use the link you will always get the latest version of the script. I'm glad that you like the script; forum member meierfra is the one who wrote it and deserves the credit for it.

But about booting Vista, I believe I see the problem; even though you installed Vista to sdb1, Vista put its boot files on the other drive in sda1. So to boot Vista, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then change your Windows entry at the bottom to:
```
title Windows Vista
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Let me know if that works or not, and if it doesn't, let me know exactly what error you get or what happens. We can work from there.

---

### Post by tarutaruomen on 2008-12-29
yes, works perfectly thank you.  one last question.  Can you point me to a good guide I could use to learn about all these (h0,0) and bootloader stuff?
I kinda see why it worked but I still have some questions  'bout it. :D

---

### Post by caljohnsmith on 2008-12-29
> **tarutaruomen said:**
> yes, works perfectly thank you.  one last question.  Can you point me to a good guide I could use to learn about all these (h0,0) and bootloader stuff?
I kinda see why it worked but I still have some questions  'bout it. :D
Glad to hear that worked OK; if you want to learn more about Grub, you could start with these resources:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Anyway, cheers and enjoy Vista and Ubuntu. :)

---

