---
title: "Grub giving &quot;error 17&quot; since i installed my new sata drive"
date: 2009-06-19
forum: General Help
---

### Post by coldpizza721 on 2009-06-19
Grub wont let me in and im getting error 17. I have tried searching on this topic and doing some things but then it became alittle confusing.Could someone please help me out thanks.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf33af33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ea5d11f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d7ce5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

``````
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2968c501-c43e-4fd2-8a91-5612563ff4bc

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by merlinus on 2009-06-19
It is possible that grub is installed in the wrong partition.  The windows entry is menu.lst looks to be correct.

Try this for reinstalling it:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by coldpizza721 on 2009-06-19
> **merlinus said:**
> It is possible that grub is installed in the wrong partition.  The windows entry is menu.lst looks to be correct.

Try this for reinstalling it:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
k thanks....ill try this out later......should i have grub on my 40gb xp or 30gb xubuntu

---

### Post by synapsys on 2009-06-19
Grub should always be installed on your first hard drive. 40g xp, hd0, sda, whatever you want to call it. Your system will always look to the first (primary) hard drive for boot info.

---

### Post by Nythain on 2009-06-19
did you install linux onto the new SATA drive, or just add the SATA drive, and is it your only SATA drive (as in the rest being IDE)

grub 17 means its having trouble finding the partition its told to find, wich means more than likely either A. its looking at the wrong partition for the boot root, and or B. your bios is booting the new SATA before the IDE drives, wich is confusing grub and causing it to look at the wrong partition for the boot root...

either way, the easiest fix, would be as above mentioned, just re-installing grub, and pointing it to the correct partition with the boot root

---

### Post by coldpizza721 on 2009-06-20
> **synapsys said:**
> Grub should always be installed on your first hard drive. 40g xp, hd0, sda, whatever you want to call it. Your system will always look to the first (primary) hard drive for boot info.

ok thanks.....can someone help me out idk what to do. Im on a live cd and i think i might even have grub on more than 1 hdd now

---

### Post by merlinus on 2009-06-20
Post results of

```

sudo fdisk -l

```

---

### Post by coldpizza721 on 2009-06-20
> **merlinus said:**
> Post results of

```

sudo fdisk -l

```
its uptop in post #1

---

### Post by merlinus on 2009-06-20
So.... sda1=windows, sdc1=linux?  Sorry I missed your earlier post.

And is this the boot order for your hdds in bios?

---

### Post by coldpizza721 on 2009-06-20
> **merlinus said:**
> So.... sda1=windows, sdc1=linux?  Sorry I missed your earlier post.

And is this the boot order for your hdds in bios?

sda1 = windows
sdc = linux...ubuntu gave me 3 paretitions i dont even no which one its on
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris

```well i guess sdc1

o the only setting for bootorder i think is "cdrom then harddrives" i unchecked floppy cuz i took tht out.....all the harddrives are on cable select except for the new sata of course that doesnt have a jumper

---

### Post by merlinus on 2009-06-20
linux is on sdc1.

Try this:

```

sudo grub
root (hd2,0)
setup (hd0)
quit

```

and restart.

---

### Post by coldpizza721 on 2009-06-20
k did tht

---

### Post by SuperSonic4 on 2009-06-20
What happened after a reboot?

It might be easier to change the order in BIOS though

---

### Post by coldpizza721 on 2009-06-20
> **SuperSonic4 said:**
> What happened after a reboot?

It might be easier to change the order in BIOS though

nothing different happened....i went back into bios....it boots to the c drive and i cant change that

---

### Post by coldpizza721 on 2009-06-21
is it supposed to be hd0???
grub> find /boot/grub/stage1
 (hd2,0)

---

### Post by unutbu on 2009-06-21
coldpizza721, please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3"). Then post the RESULTS.txt file.

---

### Post by coldpizza721 on 2009-06-21
i have a thumb drive in also now....sde i think it is```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf33af33

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ea5d11f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d7ce5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    57,496,634    57,496,572  83 Linux
/dev/sdc2          57,496,635    60,050,969     2,554,335   5 Extended
/dev/sdc5          57,496,698    60,050,969     2,554,272  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 259 MB, 259522560 bytes
17 heads, 32 sectors/track, 931 cylinders, total 506880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  32       506,878       506,847   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="70C4334DC43314B6" TYPE="ntfs" 
/dev/sdb1: UUID="2220BDF320BDCE53" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="2968c501-c43e-4fd2-8a91-5612563ff4bc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="35ebe9c1-7992-4f20-b830-c107d5b00896" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sde1: SEC_TYPE="msdos" UUID="8541-12DB" TYPE="vfat" 

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
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2968c501-c43e-4fd2-8a91-5612563ff4bc

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=35ebe9c1-7992-4f20-b830-c107d5b00896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   8.0GB: boot/grub/menu.lst
   8.1GB: boot/grub/stage2
   8.0GB: boot/initrd.img-2.6.27-7-generic
   8.1GB: boot/initrd.img-2.6.28-11-generic
   8.1GB: boot/vmlinuz-2.6.27-7-generic
   8.1GB: boot/vmlinuz-2.6.28-11-generic
   8.1GB: initrd.img
   8.0GB: initrd.img.old
   8.1GB: vmlinuz
   8.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 3c 90 42 53 44 20 20  34 2e 34 00 02 08 01 00  |.<.BSD  4.4.....|
00000010  02 00 02 00 00 f0 f8 00  20 00 20 00 00 00 00 00  |........ . .....|
00000020  df bb 07 00 00 00 29 db  12 41 85 4e 4f 20 4e 41  |......)..A.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 31  |ME    FAT16   .1|
00000040  c0 8e d0 bc 00 7c fb 8e  d8 e8 00 00 5e 83 c6 19  |.....|......^...|
00000050  bb 07 00 fc ac 84 c0 74  06 b4 0e cd 10 eb f5 30  |.......t.......0|
00000060  e4 cd 16 cd 19 0d 0a 4e  6f 6e 2d 73 79 73 74 65  |.......Non-syste|
00000070  6d 20 64 69 73 6b 0d 0a  50 72 65 73 73 20 61 6e  |m disk..Press an|
00000080  79 20 6b 65 79 20 74 6f  20 72 65 62 6f 6f 74 0d  |y key to reboot.|
00000090  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by unutbu on 2009-06-21
Am I right in assuming sdd is the new sata drive?

I am not sure this is the problem, but here is my guess:

sdd has an "Invalid MBR Signature". This means the partition table on sdd is corrupt (or simply empty). When GRUB tries to boot sdc2, it has to find the partition with UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc. 
In the process, I assume it reads the partition table on each drive. If it reaches sdd before finding sdc2, then it encounters the invalid partition table and perhaps this causes it to fail.

So perhaps try this: Boot from a LiveCD. Click System>Admin>Partition Editor. This will launch GParted.
Now make a partition or partitions in sdd. Click Apply.
GParted will rewrite the partition table on sdd and hopefully fix the problem.

Then try to reboot and see what happens.

If it does not work, please run boot_info_script again and post RESULTS.txt again. Also describe what error message you see when you try to boot Linux again.

---

### Post by coldpizza721 on 2009-06-21
i was kind of hoping that was the problem when you suggjested that.

here are the new results
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf33af33

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ea5d11f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d7ce5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    57,496,634    57,496,572  83 Linux
/dev/sdc2          57,496,635    60,050,969     2,554,335   5 Extended
/dev/sdc5          57,496,698    60,050,969     2,554,272  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005411e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sdd2         104,856,255   167,766,794    62,910,540  83 Linux
/dev/sdd3         167,766,795   230,677,334    62,910,540  83 Linux
/dev/sdd4         230,677,335 1,953,520,064 1,722,842,730   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 259 MB, 259522560 bytes
17 heads, 32 sectors/track, 931 cylinders, total 506880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  32       506,878       506,847   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="70C4334DC43314B6" TYPE="ntfs" 
/dev/sdb1: UUID="2220BDF320BDCE53" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="2968c501-c43e-4fd2-8a91-5612563ff4bc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="35ebe9c1-7992-4f20-b830-c107d5b00896" TYPE="swap" 
/dev/sdd1: UUID="365F1E8F23816042" LABEL="F" TYPE="ntfs" 
/dev/sdd2: LABEL="G" UUID="e37366ad-f58c-4f14-8434-0a738bf55e41" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd3: LABEL="H" UUID="7a05133d-dbbd-4182-a650-c311a1f85894" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd4: UUID="0BC47C1744C7A376" LABEL="E" TYPE="ntfs" 
/dev/sde1: SEC_TYPE="msdos" UUID="8541-12DB" TYPE="vfat" 
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
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2968c501-c43e-4fd2-8a91-5612563ff4bc

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        2968c501-c43e-4fd2-8a91-5612563ff4bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=2968c501-c43e-4fd2-8a91-5612563ff4bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=35ebe9c1-7992-4f20-b830-c107d5b00896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   8.0GB: boot/grub/menu.lst
   8.1GB: boot/grub/stage2
   8.0GB: boot/initrd.img-2.6.27-7-generic
   8.1GB: boot/initrd.img-2.6.28-11-generic
   8.1GB: boot/vmlinuz-2.6.27-7-generic
   8.1GB: boot/vmlinuz-2.6.28-11-generic
   8.1GB: initrd.img
   8.0GB: initrd.img.old
   8.1GB: vmlinuz
   8.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 3c 90 42 53 44 20 20  34 2e 34 00 02 08 01 00  |.<.BSD  4.4.....|
00000010  02 00 02 00 00 f0 f8 00  20 00 20 00 00 00 00 00  |........ . .....|
00000020  df bb 07 00 00 00 29 db  12 41 85 4e 4f 20 4e 41  |......)..A.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 31  |ME    FAT16   .1|
00000040  c0 8e d0 bc 00 7c fb 8e  d8 e8 00 00 5e 83 c6 19  |.....|......^...|
00000050  bb 07 00 fc ac 84 c0 74  06 b4 0e cd 10 eb f5 30  |.......t.......0|
00000060  e4 cd 16 cd 19 0d 0a 4e  6f 6e 2d 73 79 73 74 65  |.......Non-syste|
00000070  6d 20 64 69 73 6b 0d 0a  50 72 65 73 73 20 61 6e  |m disk..Press an|
00000080  79 20 6b 65 79 20 74 6f  20 72 65 62 6f 6f 74 0d  |y key to reboot.|
00000090  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
when i turn on my computer i get something like this at a black screen
```

Grub loading stage 1.5.

Grub loading please wait ...
Error 17
_

```and you cant do anything...i have to pull the plugg and put it back in

---

### Post by unutbu on 2009-06-21
coldpizza721, okay, let's try something else: The RESULTS.txt says that Syslinux is installed on the MBR of sdc. And the BIOS you say is set to boot sdc. So Syslinux is controlling the boot process. Let's replace that with GRUB -- mainly because I'm more familiar with GRUB, and because boot_info_script gives more detailed information about what GRUB is doing than Syslinux.

So using a Jaunty LiveCD, in the terminal, how about try:
```

sudo grub
root (hd2,0)
setup (hd2)
quit
```

Then try booting once more.

If it doesn't work, you know the drill -- another RESULTS.txt please.

---

### Post by coldpizza721 on 2009-06-21
> **unutbu said:**
> coldpizza721, okay, let's try something else: The RESULTS.txt says that Syslinux is installed on the MBR of sdc. And the BIOS you say is set to boot sdc. So Syslinux is controlling the boot process. Let's replace that with GRUB -- mainly because I'm more familiar with GRUB, and because boot_info_script gives more detailed information about what GRUB is doing than Syslinux.

So using a Jaunty LiveCD, in the terminal, how about try:
```

sudo grub
root (hd2,0)
setup (hd2)
quit
```Then try booting once more.

If it doesn't work, you know the drill -- another RESULTS.txt please.

sorry if i was unclear but when i said it boot to my c drive i ment like windows drive (sda)

---

### Post by unutbu on 2009-06-21
Okay, I understand the BIOS is set to boot from sda. 
When that happens, the GRUB stage1 and stage1.5 boot loader is run. 
They are located in the first 18 sectors of sda. 
It then looks in the first partition on your third drive for the GRUB stage2 file.

Perhaps the problem is that with sdd connected, the meaning of "third drive" has changed.
The BIOS might be listing drives in a different order than how Linux lists them.
So when we say
```

root (hd2,0)
```

we expect GRUB to hand off to sdc1, but in fact perhaps this command is causing GRUB to try to boot the first partition on some other drive.

The following experiment will either confirm or deny this theory.

Boot from a Jaunty LiveCD, and run
```

sudo grub
root (hd3,0)
setup (hd0)
quit
```

Reboot and pray.

If that does not work, try
```

sudo grub
root (hd1,0)
setup (hd0)
quit
```

and 
```

sudo grub
root (hd4,0)
setup (hd0)
quit
```

and 
```

sudo grub
root (hd0,0)
setup (hd0)
quit
```

I doubt the last one (root (hd0,0)) has any hope of succeeding, but it is harmless to try these experiments. You can always return to your current state by running
```

sudo grub
root (hd2,0)
setup (hd0)
quit

```

Also, when you disconnect sdd, can you once again boot Ubuntu (sdc1) and Windows (sda1)?

---

### Post by coldpizza721 on 2009-06-22
k. im trying the first set and im getting an error
```
grub> root (hd3,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

```

should i just continue to the next sets....or does tht change

---

