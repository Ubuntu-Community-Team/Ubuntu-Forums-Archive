---
title: "Resized Partitions with GParted -&gt; Cannot Boot Vista"
date: 2009-04-25
forum: General Help
---

### Post by Oblivion590 on 2009-04-25
I was using the GParted live disc on a USB flash drive to shift some space from my root Linux partition to Vista, but this has resulted in being unable to boot either my Vista partition or the recovery partition at the start of my hard drive.  I am still able to boot to Linux via my GRUB Legacy install, though.



My installation of Linux is completely capable of mounting the Vista NTFS partition and reading the files, but GRUB claims "Filesystem type unknown" when attempting to mount my Vista partition.  Attempting to work around that with rootnoverify simply returns Error 17: "Cannot mount selected partition."  Additionally, the Vista recovery CD is capable of finding Windows Vista, but BootRec.exe /ScanOS cannot find any Vista installations; many solutions for Vista booting problems involve rebuilding the BCD file, but even doing so manually with bcdedit.exe fails to be effective.


Is there any reason why these programs would be unable to read the Vista partition, when I can mount it just fine after booting to Linux?  Additionally, I was using the "TestDisk" utility to see if rebuilding my partition table would help, but alas, the only lasting result is that GParted views my disk as having 255 heads instead of 240 heads in CHS notation!  fdisk, on the other hand, detects the drive geometry correctly.


Here is the output from "fdisk -l -u", if it is helpful:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9455d63a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    13940639     6970288+  27  Unknown
/dev/sda2   *    13940640   175694399    80876880    7  HPFS/NTFS
/dev/sda3       175694400   175769999       37800   83  Linux
/dev/sda4       175770000   312605999    68418000    f  W95 Ext'd (LBA)
/dev/sda5       175785120   179686079     1950480   82  Linux swap / Solaris
/dev/sda6       179686143   271842479    46078168+  83  Linux
/dev/sda7       271842543   312575759    20366608+   b  W95 FAT32

```I am not afraid of command-line solutions, but I would prefer not having to reinstall Vista, especially as I do not possess a Vista DVD, and the recovery partition that I cannot boot to is of no assistance.

---

### Post by meierfra. on 2009-04-25
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post(use the code tags)

---

### Post by Oblivion590 on 2009-04-26
I have run the script, and the results are as follows.  The secondary disk detected is my USB flash drive.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 13942784. But according to the info from 
                       fdisk, sda2 starts at sector 13940640.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/bcd /Boot/BCD 
                       /Windows/System32/winload.exe 
                       /Windows/System32/Winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9455d63a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    13,940,639    13,940,577  27 Hidden HPFS/NTFS
/dev/sda2    *     13,940,640   175,694,399   161,753,760   7 HPFS/NTFS
/dev/sda3         175,694,400   175,769,999        75,600  83 Linux
/dev/sda4         175,770,000   312,605,999   136,836,000   f W95 Ext d (LBA)
/dev/sda5         175,785,120   179,686,079     3,900,960  82 Linux swap / Solaris
/dev/sda6         179,686,143   271,842,479    92,156,337  83 Linux
/dev/sda7         271,842,543   312,575,759    40,733,217   b W95 FAT32

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
5 heads, 32 sectors/track, 97894 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf244be00

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064    15,663,103    15,655,040   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2A9C301D9C2FE1D5" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="C63E346A3E345621" LABEL="Windows System" TYPE="ntfs" 
/dev/sda3: UUID="ee46df09-e0d2-4ec0-ba0b-e312a5fc4df2" TYPE="ext3" 
/dev/sda5: TYPE="swap" 
/dev/sda6: LABEL="Debian Ext3" UUID="bbafb375-23dc-4b14-a80a-ce25db2f9c8d" TYPE="ext3" 
/dev/sda7: LABEL="OS SHARE" UUID="FEB3-0857" TYPE="vfat" 
/dev/sdb1: LABEL="PATRIOT" UUID="F416-CACF" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda3 on /boot type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdb1 on /media/PATRIOT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=lower,uid=1000)


============================= sda3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,2)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/sda6 ro 
initrd        /initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/sda6 ro single
initrd        /initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.18-6-amd64
root        (hd0,2)
kernel        /vmlinuz-2.6.18-6-amd64 root=/dev/sda6 ro 
initrd        /initrd.img-2.6.18-6-amd64

title        Debian GNU/Linux, kernel 2.6.18-6-amd64 (single-user mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.18-6-amd64 root=/dev/sda6 ro single
initrd        /initrd.img-2.6.18-6-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
kernel /bootmgr
chainloader /bootmgr
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
kernel /bootmgr
chainloader /bootmgr
#savedefault
#makeactive
#chainloader    +1

# Trying yet more things!
title        Windows Vista!
find --set-root /bootmgr
makeactive
kernel /bootmgr
chainloader /bootmgr

=================== sda3: Location of files loaded by Grub: ===================


  89.9GB: grub/menu.lst
  89.9GB: grub/stage2
  89.9GB: initrd.img-2.6.18-6-amd64
  89.9GB: initrd.img-2.6.18-6-amd64.bak
  89.9GB: initrd.img-2.6.26-2-amd64
  89.9GB: initrd.img-2.6.26-2-amd64.bak
  89.9GB: vmlinuz-2.6.18-6-amd64
  89.9GB: vmlinuz-2.6.26-2-amd64

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,2)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/sda6 ro 
initrd        /initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.26-2-amd64 root=/dev/sda6 ro single
initrd        /initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.18-6-amd64
root        (hd0,2)
kernel        /vmlinuz-2.6.18-6-amd64 root=/dev/sda6 ro 
initrd        /initrd.img-2.6.18-6-amd64

title        Debian GNU/Linux, kernel 2.6.18-6-amd64 (single-user mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.18-6-amd64 root=/dev/sda6 ro single
initrd        /initrd.img-2.6.18-6-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
kernel /bootmgr
chainloader /bootmgr
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
kernel /bootmgr
chainloader /bootmgr
#savedefault
#makeactive
#chainloader    +1

# Trying yet more things!
title        Windows Vista!
find --set-root /bootmgr
makeactive
kernel /bootmgr
chainloader /bootmgr

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    errors=remount-ro 0       1
/dev/sda3       /boot           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda6: Location of files loaded by Grub: ===================


  92.0GB: boot/grub/menu.lst
  92.0GB: boot/grub/stage2
  92.0GB: boot/initrd.img-2.6.18-6-amd64
  92.0GB: boot/initrd.img-2.6.18-6-amd64.bak
  92.0GB: boot/initrd.img-2.6.26-2-amd64
  92.0GB: boot/initrd.img-2.6.26-2-amd64.bak
  92.0GB: boot/vmlinuz-2.6.18-6-amd64
  92.0GB: boot/vmlinuz-2.6.26-2-amd64
  92.0GB: initrd.img
  92.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda7: device is busy
umount: /tmp/BootInfo/sda7: device is busy
```

---

### Post by Legace on 2009-04-26
Try to fix with [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Oblivion590 on 2009-04-26
As you might read in my original post, I already tried using TestDisk. It was not helpful, except that now I cannot read my partitions with GParted. ;)

EDIT: And, speaking of GParted, I have asked this same question on their forums, at this link: [http://gparted-forum.surf4.info/viewtopic.php?id=13395](http://gparted-forum.surf4.info/viewtopic.php?id=13395)

---

### Post by El Zoido on 2009-04-26
AFAIK this happens when you don't resize your Partition in Vista.
Something about how Vista treats NTFS.
It happened to a friend of mine and we ended up reinstalling Vista, then Linux.
The data should still be there, you should be able to make a backup.
Could be that there is an alternative solution, though.

---

### Post by Oblivion590 on 2009-04-26
Yes, El Zoido, you are quite correct--the data is completely intact.  I could backup any data if I wished (Luckily, the Vista partition is entirely non-critical data, anyhow), but that would ignore the problem that I would have no way of recovering Vista; both the recovery partition and the Vista partition are unbootable.  The summary above suggests that the sectors specified in different areas of the disk do not match, due to Vista's disk partitioning scheme, so a way to fix them might solve this problem.

---

### Post by El Zoido on 2009-04-26
Hm, that you cannot access the recovery partition certainly complicates the problem.
It was still possible for my friend.
While by default the recovery partition wasn't accessible, he could activate it.
Doing so on his Laptop involved changing some Bios-setting and then pressing the right key on startup, but I guess this depends strongly on how your PC treats the recovery partition.

---

### Post by Oblivion590 on 2009-04-26
I moved the recovery and Vista partitions, so they do not begin in the same places--this, I suspect, is the core cause of the problem.  Thus, I cannot still boot to the recovery partition.

---

### Post by meierfra. on 2009-04-26
> Boot sector info:  According to the info in the boot sector, sda1 starts   at sector 2048. But according to the info from fdisk,  sda1 starts at sector 63.


> Boot sector info:  According to the info in the boot sector, sda2 starts  at sector 13942784. But according to the info from  fdisk, sda2 starts at sector 13940640.


This prevents you from booting Vista.   But testdisk can fix the problem.

```
sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Recovery  partition. and choose
"boot"
"RebuildBS"
"Write"  

then press "q" once or twice  times  to get  back to partition selection screen.  
This time select the Vista partition and continue as above,

But you have more work to do to  be able to boot Vista:

Boot from your Vista DVD. After selecting your favorite language, select "Repair Computer". 
If the DVD  offers you do fix a problem, say yes. Otherwise select "Startup Repair" at the next screen.

You might have to run Startup Repair more than once.


> dev/sda4 ends after the last sector of /dev/sda

This prevents "gparted" from seeing your partitions.  It can also be fixed with testdisk. But we'll work on this after you fixed your Vista problem.

---

### Post by Oblivion590 on 2009-04-26
I went into TestDisk, changed the heads and cylinders to match fdisk's output, and rebuilt the boot sectors for both the RE and Vista partitions.  However, GRUB still cannot mount the partitions, and Vista's recovery disc still finds no startup errors.  BootRec.exe /ScanOS also still cannot find any Vista installations.  However, the boot info script now has no complaints about the boot sectors for sda1 and sda2.

---

### Post by meierfra. on 2009-04-26
Add these entries to menu.lst:

title  Recovery
rootnoverify (hd0,0)
chainloader +1


title  Vista
rootnoverify (hd0,1)
chainloader +1


I'm pretty sure none of those  entries will work, but I would like to know what error messages you get.

---

### Post by Oblivion590 on 2009-04-26
I can already tell you without trying those: Error 17: Cannot mount selected partition.

EDIT:  Oh yes, and for the extended partition issue, can I just use fdisk to change the ending sector to 312 575 759 from 312 605 999 and be done, or is it more complicated than that?

---

### Post by meierfra. on 2009-04-26
> I can already tell you without trying those: Error 17: Cannot mount selected partition.

Could you please try?  Error 17  is  a Grub error. As far as I can see Grub is configured correctly.  You should get an error message from Vista.


> Can I just use fdisk to change the ending sector to 312 575 759 from 312 605 999 and be done, 
That should do it.

---

### Post by Oblivion590 on 2009-04-26
Okay, I guess it's only the makeactive command that causes that Grub error.  I get no error, or response, or anything, by only using rootnoverify and chainloader +1.  In fact, I was able to attempt it with both partitions on the command line, and then merely hit ESC and return to the menu to load Linux.

Additionally, the fix in size for the extended partition has made it so that GParted can read my partition table, so at least that worked.

---

### Post by meierfra. on 2009-04-26
> Okay, I guess it's only the makeactive command that causes that Grub error. I get no error, or response, or anything, by only using rootnoverify and chainloader +1. In fact, I was able to attempt it with both partitions on the command line, and then merely hit ESC and return to the menu to load Linux.

If you use the code from the Grub command line, you need to  add a  "boot" line:

title Recovery
rootnoverify (hd0,0)
chainloader +1
boot

---

### Post by Oblivion590 on 2009-04-26
Oh wow, it works!  That's what I get for doubting what the pro tells me to do. ;)

Thank you so much for your help!

---

### Post by meierfra. on 2009-04-26
> Oh wow, it works! 
Great.


> Thank you so much for your help! 
You are welcome.

---

### Post by escher1st on 2009-04-27
Hello I am having a similar problem.
Need some serious help.
I have messed up my MBR I believe. I have Acer aspire 6920g.

Here is what I did. (try not to laugh to loud, or for the sensitive ones, this will be shocking) LoL

Ok, I was going to install Caos Linux. But for some reason I selected the auto install method. When I started to realize that it was going to utilize the whole disk. I panicked and hit the power button to shut down. On the off chance it had not changed anything yet. ( I know huge mistake ) So for those who know needless to say, but viola I could not start up windows again or anything else.

So for my next bright idea, I decided to install Ubuntu 9.04. It formated the hard but the recovery partition didnt show.


With Acronis I am only showing 298 Gigs of 320. I am including a snap shot of the partition setup I have put together. I am also including a pick of the MBR info with Acronis. I did notice that under "hidden sectors" there is a figure of 309755? Now I am wondering is this where the 10 gig acer restore partiton is?

So is there a way to fix the mbr or replace it , so that the recovery partition is available again? Because it is the only copy I have of the partition. I was never able to back it up on disk, because the dvd burner has not worked from day one. I have sent it back for repairs, but it was there for three problems. And they didnt fix the burner issue.

Thanks in advance

---

### Post by meierfra. on 2009-04-27
> So is there a way to fix the mbr or replace it , so that the recovery partition is available again? 
I'm not sure. Your recovery partition might have been erased. But lets have close look at your system:
Boot into Ubuntu. 

1)  Download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. 

2) download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  

```

After starting testdisk with the above command, choose
"No Log".
 Select the hard drive containing the recovery partition.
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" or "N" (depending whether you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by escher1st on 2009-04-28
Hello meierfra and thank you very much for responding to my request for help.

Since my last post , before you had reponded. I went and tried my wife's Acer recovery disk. It is a slightly different machine and is only the 32 bit version. It did put her version on the NTFS partition that I made with linux, which is a different version of the usual Type. So I may have really sol'd myself. But here is the info you requested. 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1faddc8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   409,593,239   204,796,620   7 HPFS/NTFS
/dev/sda3         409,593,240   507,252,374    97,659,135  83 Linux
/dev/sda4         507,252,375   625,137,344   117,884,970   5 Extended
/dev/sda5         507,252,438   515,059,964     7,807,527  82 Linux swap / Solaris
/dev/sda6         515,060,028   625,137,344   110,077,317  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3868F57268F52EEE" LABEL="ACER" TYPE="ntfs" 
/dev/sda2: UUID="7B1F7874796E5EE2" TYPE="ntfs" 
/dev/sda3: UUID="3a043b9d-ddd4-4407-9db9-04195501a77d" TYPE="ext3" 
/dev/sda5: UUID="d2d6db3f-3a4f-4b5f-bb7c-fbcb74147d09" TYPE="swap" 
/dev/sda6: UUID="1329e8eb-42de-4a8f-9494-5ad4d3636fac" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nirrad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nirrad)


=========================== sda3/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3a043b9d-ddd4-4407-9db9-04195501a77d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a043b9d-ddd4-4407-9db9-04195501a77d

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3a043b9d-ddd4-4407-9db9-04195501a77d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3a043b9d-ddd4-4407-9db9-04195501a77d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3a043b9d-ddd4-4407-9db9-04195501a77d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3a043b9d-ddd4-4407-9db9-04195501a77d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3a043b9d-ddd4-4407-9db9-04195501a77d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=3a043b9d-ddd4-4407-9db9-04195501a77d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1329e8eb-42de-4a8f-9494-5ad4d3636fac /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=d2d6db3f-3a4f-4b5f-bb7c-fbcb74147d09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 258.8GB: boot/grub/menu.lst
 258.9GB: boot/grub/stage2
 258.8GB: boot/initrd.img-2.6.28-11-generic
 258.9GB: boot/vmlinuz-2.6.28-11-generic
 258.8GB: initrd.img
 258.9GB: vmlinuz
```

Here is the output from Testdisk

```
TestDisk 6.11.1, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 12747 254 63  204796557 [ACER]
D HPFS - NTFS              0   1  1 38912 254 63  625137282
D HPFS - NTFS           8102   0  5 25786 254 63  284109521 [DATA]
D HPFS - NTFS          12748   0  1 25495 254 63  204796620
D Linux                25496   0  1 31574 254 56   97659128
D Linux                25787   1  1 29610 254 62   61432496 [/]
D Linux                28517 157 57 34596 157 49   97659128
D Linux                29120 220 29 36415 220 21  117194168
D Linux                29122 165 36 36417 165 28  117194168
D Linux                29122 198  5 36417 197 60  117194168
D Linux                29122 230 37 36417 230 29  117194168
D Linux                29123   8  6 36418   7 61  117194168
D Linux                29123 235 41 36418 235 33  117194168
D Linux Swap           29611   1  1 30119 254 41    8177000
D Linux                30120   1  1 38912 254 61  141259480 [/home]
D Linux Swap           31575   1  1 32060 254 40    7807504
D Linux                32061   1  1 38912 254 58  110077312
D Linux Swap           32791   1  1 33276 254 40    7807504
D Linux                33277   1  1 38912 254 58   90542272
D Linux                33372   1  1 38402 254 63   80822952
D Linux                34201   1  1 38912 254 62   75698216
D HPFS - NTFS          38450  98 49 38913  37 36    7434240





Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 104 GB / 97 GiB

```

And here is a list of the partitions with directory listings.

```
D HPFS - NTFS              0   1  1 12747 254 63  204796557 [ACER]

D HPFS - NTFS          12748   0  1 25495 254 63  204796620

D Linux                25496   0  1 31574 254 56   97659128

D Linux                25787   1  1 29610 254 62   61432496 [/]

D Linux                30120   1  1 38912 254 61  141259480 [/home]

D Linux                32061   1  1 38912 254 58  110077312

D Linux                33277   1  1 38912 254 58   90542272

D Linux                33372   1  1 38402 254 63   80822952

D Linux                34201   1  1 38912 254 62   75698216
```


I was wondering about the disk geometry,if it should be 255, or 240 cylinders. But I will not change anything more without first hearing from you. 
Thanks again very much.

P.S. I could even live without windows if I have to. But would like to have the full hard drive available. ( I do know a 320 G is not actually 320. But I still feel the 10 Gigs they use for the PQSERVICE partition is still there.)

---

### Post by meierfra. on 2009-04-28
Your  recovery partition seems to be gone. If you call   Acer, they  should send you a Recovery DVD for free or for  a small fee.

> With Acronis I am only showing 298 Gigs of 320.

320GB=298GiB. Also according to partition table  in RESULTS.txt, you are using the full disk.

---

### Post by escher1st on 2009-04-28
> **meierfra. said:**
> Your  recovery partition seems to be gone. If you call   Acer, they  should send you a Recovery DVD for free or a small fee.



320GB=298GiB. Also according to partition table  in RESULTS.txt, you are using the full disk.


Ok thank you very much for the info.

---

