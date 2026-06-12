---
title: "got a grub problem ubuntu 8.10"
date: 2009-02-08
forum: General Help
---

### Post by subzero22 on 2009-02-08
Ok I was using ubuntu 7.10 just fine and even the grub installed fine. I reformatted the drive and installed ubuntu 8.10. Now the grub keeps saying stage 1.5 error 2. I'm not sure what's going on. I've looked at other posts in these forums but haven't found a way to fix it yet.

Menu.lst is:
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
# kopt=root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff

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
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Oh and for some reason or other when I look at the linux drive on the live cd it's saying mount point /media/disk and when I installed it I put the mount point as / Oh and the partition is in /dev/sda6.

Boot info script info is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbac79d93

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,424,159   145,424,097   7 HPFS/NTFS
/dev/sda2         145,424,160   227,351,879    81,927,720   7 HPFS/NTFS
/dev/sda3         227,351,880   390,716,864   163,364,985   5 Extended
/dev/sda5         227,351,943   239,641,604    12,289,662  82 Linux swap / Solaris
/dev/sda6         239,641,668   390,716,864   151,075,197  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdea8ddce

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,295,439   156,295,377   7 HPFS/NTFS


Drive sdg: _____________________________________________________________________

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A2F98382E559DDBD" LABEL="Windows Sucks" TYPE="ntfs" 
/dev/sda2: UUID="306856146855D8E4" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="920ffb0f-7378-48cb-9841-29b25efe2e61" TYPE="swap" 
/dev/sda6: UUID="46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff" TYPE="ext3" 
/dev/sdb1: UUID="5C28680B2867E28E" LABEL="Downloads" TYPE="ntfs" 
/dev/sdg1: LABEL="My Book" UUID="AA9D-F0BC" TYPE="vfat" 
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdg1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/Windows Sucks type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# kopt=root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff

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
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=46cc04da-aa4c-4ea5-b9ed-c00ce023e5ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=920ffb0f-7378-48cb-9841-29b25efe2e61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 194.0GB: boot/grub/menu.lst
 194.0GB: boot/grub/stage2
 194.1GB: boot/initrd.img-2.6.27-7-generic
 193.9GB: boot/vmlinuz-2.6.27-7-generic
 194.1GB: initrd.img
 193.9GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=======Devices which don't seem to have a corresponding hard drive==============

 sdc .
 sdd .
 sde .
 sdf .

```

Thanks in advance for any help.

---

### Post by subzero22 on 2009-02-08
well for now I'm going to bed. If anyone can help please post the info and I'll check in the morning

---

### Post by hyper_ch on 2009-02-08
on the live cd post the output of
```

sudo fdisk -l

```

```

ls -al /dev/disk/by-uuid

```

---

### Post by caljohnsmith on 2009-02-08
Do you know which drive you are booting on start up? You currently have Grub installed to the MBR (Master Boot Record) of both your sda and sdb drives. How about downloading the [Super Grub Disk]("http://www.supergrubdisk.org/"), boot that, and at the first main menu press "c" to get the Grub command line. Then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
One of those commands should show the HDD with four partitions (sda), and the other command should show only one partition (sdb). Please let me know which drive corresponds to (hd0), and we can work from there if you want.
> **hyper_ch said:**
> on the live cd post the output of
```

sudo fdisk -l

```

```

ls -al /dev/disk/by-uuid

```
I think you might have overlooked the results from the Boot Info Script, because the Boot Info Script results include that information. :)

---

### Post by subzero22 on 2009-02-08
I know from messing with grub before that windows and linux are installed in hd0. Unless re-installing 8.10 changed something? As for using the super grub disk that will kinda be hard as I'm using the ubuntu live cd to get on the internet and I don't have a floppy disk drive or even a spare cd drive :( But I did those commands on the live cd and here's the results. Oh and for some reason it's showing I have an ext2fs when I formated it as ext3 there is no ext2 on my drive. And why it's showing filesystem unknown I have no idea as my windows is still intact just can't get to it cause of this grub problem but can still go into the drive and see all of it's files.

Well anyway here's the results.

```
grub> geometry (hd0)
drive 0x80: C/H/S = 24321/255/63, The number of sectors = 390721968, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd1)
drive 0x81: C/H/S = 10337/240/63, The number of sectors = 156301488, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

```

---

### Post by caljohnsmith on 2009-02-08
That's OK if you want to run those geometry commands in the Grub CLI while you are in Ubuntu, but that's not the same as running them from the Super Grub Disk on start up. When you are in Ubuntu, (hd0) is sda, (hd1) is sdb, etc, but on start up that is not necessarily true. On start up, Grub sees the order of drives as your BIOS boot order, not as how the drives are ordered in Ubuntu. So if you are booting your sdb drive for instance, Grub will see it as (hd0) on start up. Therefore, the only way to know is to either go into your BIOS and check the boot order, or you can run the geometry commands from the Super Grub Disk on start up. You don't need to post the results or anything, I just need confirmation of which drive you are booting so we can know what might be the next best step to take to fix your problem. So if doing "geometry (hd0)" from the Super Grub Disk yields the same results as what you posted while doing that command in Ubuntu, we will know you are booting the sda drive on start up. Please let me know what you find.

---

### Post by subzero22 on 2009-02-08
will it change anything if I run it off a usb port?

---

### Post by caljohnsmith on 2009-02-08
> **subzero22 said:**
> will it change anything if I run it off a usb port?
That will be a problem only if you have to change your BIOS boot order to boot the USB drive; if your boot order is all ready set to boot the USB drive before your other drives, that should be fine.

---

### Post by subzero22 on 2009-02-08
ya I would have to change it. hmm I'll try and borrow a friends computer to make the cd.

---

### Post by caljohnsmith on 2009-02-08
How about trying this instead from the Ubuntu Live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
That will restore a Windows MBR to your 80 GB Windows drive. Then reboot, and let me know what happens on start up; if you still get the Grub error, we will know you are booting the sda drive on start up.

---

### Post by subzero22 on 2009-02-08
I borrowed my neighbors labtop to get it done. I got the cd in and it's weird as ubuntu 7.10 booted off hd0 but when doing the same commands you told me to do it shows the same info as last time but the hd's are switched. same info as above but hd0 is now hd1 and hd1 is now hd0 lol. I don't know how that happened.

---

### Post by caljohnsmith on 2009-02-08
> **subzero22 said:**
> I borrowed my neighbors labtop to get it done. I got the cd in and it's weird as ubuntu 7.10 booted off hd0 but when doing the same commands you told me to do it shows the same info as last time but the hd's are switched. same info as above but hd0 is now hd1 and hd1 is now hd0 lol. I don't know how that happened.
That's why it's sometimes necessary to check, because as you can see, your drives can get switched around in the boot order. :) Anyway, can you go into your BIOS and set the sda drive to boot on start up? And does booting the sda drive still return the same Grub error 2?

---

### Post by subzero22 on 2009-02-08
Yep that worked. thanks for all the help caljohnsmith your a guru at this. :)

---

### Post by caljohnsmith on 2009-02-08
> **subzero22 said:**
> Yep that worked. thanks for all the help caljohnsmith your a guru at this. :)
Glad to hear that changing your boot order is all it took to fix it. Cheers and enjoy your new Ubuntu 8.10 install. :)

---

