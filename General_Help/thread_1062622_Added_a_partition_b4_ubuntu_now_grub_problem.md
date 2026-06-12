---
title: "Added a partition b4 ubuntu now grub problem"
date: 2009-02-07
forum: General Help
---

### Post by Shishant on 2009-02-07
Hello,

I had 5 ntfs and 1 ext2(atlast) partition before, 

later i made space for windows 7 and made it to 6 ntfs and 1 ext2(again ext2 was atlast after partitioning) but now my grub shows error loading i guess its because boot configuration /sda 9 (which it was before) i think i should change it to sda 10 but can u help me guiding how to change it and restore my grub so that i have windows 7 too in boot menu.

Thank You very much.

Regards,
Shishant Todi.

---

### Post by Shishant on 2009-02-07
[IMG]http://i41.tinypic.com/2dm615x.jpg[/IMG]

My partition structure where 
C Drive (Windows Xp), 
H Drive (Windows 7) is newly added 
and last 1 is ext2 (Ubuntu).

---

### Post by caljohnsmith on 2009-02-07
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should reinstall Grub to the MBR and point it to the correct partition. Let me know how that goes.

---

### Post by Shishant on 2009-02-07
Yes i did it thanks for your reply, but i want to add windows 7 to my grub 

[IMG]http://i41.tinypic.com/j5cac8.png[/IMG]

where drive h is windows 7, i added this to my grub

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7
root		(hd0,9)
savedefault
makeactive
chainloader	+1
```

but it was showing an error and when i boot ubuntu it shows (hd0,9) it means ubuntu is in 9 so where is windows 7

I was searching forums could find but i am pasting my boot information

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04ca04c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    32,676,209    32,676,147   7 HPFS/NTFS
/dev/sda2          32,676,210   312,576,704   279,900,495   f W95 Ext d (LBA)
/dev/sda5          32,676,273    73,641,959    40,965,687   7 HPFS/NTFS
/dev/sda6          73,642,023   155,557,394    81,915,372   7 HPFS/NTFS
/dev/sda7         155,557,458   205,503,479    49,946,022   7 HPFS/NTFS
/dev/sda8         205,503,543   263,080,439    57,576,897   7 HPFS/NTFS
/dev/sda9         263,080,503   286,856,639    23,776,137   7 HPFS/NTFS
/dev/sda10        286,856,703   312,576,704    25,720,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="C08C33318C3320F8" LABEL="C Drive" TYPE="ntfs" 
/dev/sda5: UUID="9CF84586F845601E" LABEL="D Drive" TYPE="ntfs" 
/dev/sda6: UUID="983455333455159A" LABEL="SONGS" TYPE="ntfs" 
/dev/sda7: UUID="C67C5E597C5E4479" LABEL="MOVIES" TYPE="ntfs" 
/dev/sda8: UUID="A2FC6AD9FC6AA76F" LABEL="SETUP" TYPE="ntfs" 
/dev/sda9: UUID="01C9892B2A386DB0" LABEL="H Drive" TYPE="ntfs" 
/dev/sda10: UUID="99ebb212-5cbd-4ee0-84d3-769fd30ee61a" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda8 on /media/SETUP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/MOVIES type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/SONGS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/D Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/C Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shishant/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shishant)
/dev/sda9 on /media/H Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


========================== sda10/boot/grub/menu.lst: ==========================

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
default		4

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
# kopt=root=UUID=99ebb212-5cbd-4ee0-84d3-769fd30ee61a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=99ebb212-5cbd-4ee0-84d3-769fd30ee61a

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
uuid		99ebb212-5cbd-4ee0-84d3-769fd30ee61a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=99ebb212-5cbd-4ee0-84d3-769fd30ee61a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		99ebb212-5cbd-4ee0-84d3-769fd30ee61a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=99ebb212-5cbd-4ee0-84d3-769fd30ee61a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		99ebb212-5cbd-4ee0-84d3-769fd30ee61a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7
root		(hd0,9)
savedefault
makeactive
chainloader	+1


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda10 :
UUID=99ebb212-5cbd-4ee0-84d3-769fd30ee61a / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/SETUP ntfs-3g defaults,locale=en_IN 0 0
/dev/sda7 /media/MOVIES ntfs-3g defaults,locale=en_IN 0 0
/dev/sda6 /media/SONGS ntfs-3g defaults,locale=en_IN 0 0
/dev/sda5 /media/D\040Drive ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/C\040Drive ntfs-3g defaults,locale=en_IN 0 0
/dev/sda9 /media/H\040Drive ntfs-3g defaults,locale=en_IN 0 0

=================== sda10: Location of files loaded by Grub: ===================


 149.7GB: boot/grub/menu.lst
 149.7GB: boot/grub/stage2
 150.2GB: boot/initrd.img-2.6.27-11-generic
 149.7GB: boot/initrd.img-2.6.27-7-generic
 149.7GB: boot/initrd.img-2.6.27-9-generic
 149.8GB: boot/vmlinuz-2.6.27-11-generic
 149.7GB: boot/vmlinuz-2.6.27-7-generic
 149.7GB: boot/vmlinuz-2.6.27-9-generic
 150.2GB: initrd.img
 149.7GB: initrd.img.old
 149.8GB: vmlinuz
 149.7GB: vmlinuz.old

```

i had windows vista installed in past so its still showing windows vista in boot information i guess... i have windows xp in drive c:

---

### Post by caljohnsmith on 2009-02-07
According to the results of the script, even though Windows 7 is on sda9, Windows 7 put its boot files in your sda1 primary partition since you installed Windows 7 to a logical partition. Therefore, to boot Windows 7, try booting Windows XP from your Grub menu, and you should get the Windows 7 boot manager where it will let you choose between Win XP and Win 7. Let me know if that works or not.

---

### Post by geirha on 2009-02-07
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows 7
root (hd0,9)
savedefault
makeactive
chainloader +1

```

Grub starts counting at 0, while the /dev/sdaX-scheme starts counting from 1, so /dev/sda1 is typically hd0,0 and /dev/sda9 is hd0,8 (not hd0,9, which is your ext2/3 partition)

BTW. It's better if you put terminal output and file content that you paste in here, inside code tags rather than quote tags. makes the post shorter and easier to read the output IMO.

---

### Post by Shishant on 2009-02-07
I changed it to hd0,8 but it still doesnt boot windows 7 but when i boot windows xp it shows me boot menu of windows 7 where i can select either of 2.

but i would love to have that option in grub.

my ext3 partition is dev/sda10 which when boots shows hd0,9

---

### Post by caljohnsmith on 2009-02-07
If you want to boot XP and Win 7 separately from Grub, you will have to put Win 7's boot files back in Win 7's partition, reconfigure them, repair the boot sector of your sda1 XP partition, and also repair the boot sector of your Win 7 sda9 partition. If you want to go through all that trouble, I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showthread.php?t=813628") for step-by-step instructions of how to do it. If you have any questions, feel free to post to that thread and meierfra will probably have time to help you out.

---

