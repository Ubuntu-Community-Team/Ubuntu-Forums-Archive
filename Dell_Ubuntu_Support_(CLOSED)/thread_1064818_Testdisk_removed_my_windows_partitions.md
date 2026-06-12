---
title: "Testdisk removed my windows partitions"
date: 2009-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Abubaker on 2009-02-09
After having nightmares with Dell Media direct button writing the MBR and the grub error 17, I used testdisk utility and recovered all the partitions.
It successfully recovered all my linux partitions and when I rebooted, the grub was fine but 'NTLDR missing' error for booting windows Vista. 

Booting into Ubuntu works fine but I dont see my windows partitions in my fdisk or Computer. It doesnt show the Windows partitions at all. 

any way to recover the data?

---

### Post by caljohnsmith on 2009-02-09
You might have recovered the wrong partitions with testdisk, because testdisk can find lost/deleted partitions that previously existed. In order to get a better idea of which of your present partition setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. 

Also, how about running testdisk again so we can see all the partitions that it finds. I would recommend using the latest 6.10 version instead of what comes in the repositories, so how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also let me know if any of the partitions that give a directory listing look like your Windows partition. We can work from there if you want.

---

### Post by Abubaker on 2009-02-09
Here is my RESULTS.txt file

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd 
                       /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522   6 FAT16
/dev/sda2    *        144,585    67,264,154    67,119,570   c W95 FAT32 (LBA)
/dev/sda3         222,243,210   224,187,073     1,943,864  83 Linux
/dev/sda4         224,187,075   312,592,769    88,405,695   f W95 Ext d (LBA)
/dev/sda5         224,187,138   243,722,113    19,534,976  83 Linux
/dev/sda6         243,722,178   292,543,649    48,821,472  83 Linux
/dev/sda7         292,543,713   296,447,424     3,903,712  82 Linux swap / Solaris
/dev/sda8         307,337,216   312,578,047     5,240,832   c W95 FAT32 (LBA)

/dev/sda4 ends after the last sector of /dev/sda
/dev/sda8 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0711" TYPE="vfat" 
/dev/sda2: UUID="07D7-0711" TYPE="vfat" 
/dev/sda3: UUID="ddfe480b-664e-419d-af4f-6496234350da" TYPE="ext3" 
/dev/sda5: UUID="019270ff-3977-4820-8e8e-6ee14c541684" TYPE="ext3" 
/dev/sda6: UUID="f21c4235-217c-4194-8a1f-b9e790447670" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="755681cc-5735-402d-b59a-a7994bb0f852" 
/dev/sda8: LABEL="MEDIADIRECT" UUID="DE54-1889" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda3 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/abubaker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=abubaker)
/dev/sda2 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda8 on /media/MEDIADIRECT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

============================= sda3/grub/menu.lst: =============================

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
# kopt=root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


 113.9GB: grub/menu.lst
 113.9GB: grub/stage2
 113.8GB: initrd.img-2.6.24-19-generic
 113.8GB: initrd.img-2.6.24-19-generic.bak
 113.8GB: initrd.img-2.6.24-23-generic
 113.9GB: initrd.img-2.6.24-23-generic.bak
 113.8GB: vmlinuz-2.6.24-19-generic
 113.9GB: vmlinuz-2.6.24-23-generic

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
# kopt=root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f21c4235-217c-4194-8a1f-b9e790447670 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f21c4235-217c-4194-8a1f-b9e790447670 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ddfe480b-664e-419d-af4f-6496234350da /boot           ext3    relatime        0       2
# /dev/sda5
UUID=019270ff-3977-4820-8e8e-6ee14c541684 /home           ext3    relatime        0       2
# /dev/sda7
UUID=755681cc-5735-402d-b59a-a7994bb0f852 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 124.9GB: boot/grub/menu.lst
 124.9GB: boot/grub/stage2
 124.8GB: boot/initrd.img-2.6.24-19-generic
 124.8GB: boot/initrd.img-2.6.24-19-generic.bak
 124.8GB: boot/initrd.img-2.6.24-23-generic
 124.9GB: boot/initrd.img-2.6.24-23-generic.bak
 124.8GB: boot/vmlinuz-2.6.24-19-generic
 124.9GB: boot/vmlinuz-2.6.24-23-generic
 124.8GB: initrd.img
 124.8GB: initrd.img.old
 124.9GB: vmlinuz
 124.8GB: vmlinuz.old

================================ sda8/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


```

And here is my output of testdisk:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     8 254 63     144522 [DellUtility]
D FAT32 LBA                9   0  1  4186 254 63   67119570 [NO NAME]
D HPFS - NTFS              9  13  5  1314 119 21   20971520 [RECOVERY]
D HPFS - NTFS           1314 119 22 13833  53 21  201113577 [OS]
P Linux                13834   0  1 13954 254 62    1943864
D Linux                13955   1  1 15170 254 62   19534976
D Linux                13958   1  1 15824 254 59   29993288
D Linux                13962   0  1 15177 253 62   19534976
D Linux                15171   1  1 18209 254 63   48821472
P Linux Swap           18210   1  1 18452 254 43    3903712
L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]


```

The partition named "OS" is my Windows Partition with all my data. I can see my files when I list out the files in that partition. Can I go ahead and write this partition table with testdisk?

PS: I have been using Testdisk 6.10 only.

Thanks for your help.

---

### Post by caljohnsmith on 2009-02-09
> **Abubaker said:**
> 
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Blue"]P[/COLOR] FAT16 >32M               0   1  1     8 254 63     144522 [DellUtility]
[COLOR="Blue"]D[/COLOR] FAT32 LBA                9   0  1  4186 254 63   67119570 [NO NAME]
[COLOR="Blue"]P[/COLOR] HPFS - NTFS              9  13  5  1314 119 21   20971520 [RECOVERY]
[COLOR="Blue"]*[/COLOR] HPFS - NTFS           1314 119 22 13833  53 21  201113577 [OS]
[COLOR="Blue"]L[/COLOR] Linux                13834   0  1 13954 254 62    1943864
[COLOR="Blue"]L[/COLOR] Linux                13955   1  1 15170 254 62   19534976
[COLOR="Blue"]D[/COLOR] Linux                13958   1  1 15824 254 59   29993288
[COLOR="Blue"]D[/COLOR] Linux                13962   0  1 15177 253 62   19534976
[COLOR="Blue"]L[/COLOR] Linux                15171   1  1 18209 254 63   48821472
[COLOR="Blue"]L[/COLOR] Linux Swap           18210   1  1 18452 254 43    3903712
[COLOR="Blue"]L[/COLOR] FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]


```
OK, using your right/left arrow keys, how about marking the partitions as I've shown above highlighted in blue. Once you are sure the partitions are marked exactly as shown above, press enter to get to the next screen, and then choose "write" so the new partition table will be written. Then please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda3 /mnt && ls -l /mnt
```
And we can work from there.

---

### Post by Abubaker on 2009-02-09
I just continued with my first deepsearch and chose 'write' and it asked for a reboot. After reboot, it again went back to Grub loading error. 17. 

I booted through live cd and again ran testdisk.

Here is the output with partitions changed as per your instructions. When I change the partition type of the one marked in bold to anything other than 'D', it shows 'Structure:Bad'. And there is no option to set it to 'L'

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
P FAT16 >32M               0   1  1     8 254 63     144522 [DellUtility]
D FAT32 LBA                9   0  1  4186 254 63   67119570 [NO NAME]
P HPFS - NTFS              9  13  5  1314 119 21   20971520 [RECOVERY]
* HPFS - NTFS           1314 119 22 13833  53 21  201113577 [OS]
**D Linux                13834   0  1 13954 254 62    1943864**
D Linux                13955   1  1 15170 254 62   19534976
L Linux                15171   1  1 18209 254 63   48821472
L Linux Swap           18210   1  1 18452 254 43    3903712
L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

Can I go ahead and 'write'?

Thanks.

---

### Post by caljohnsmith on 2009-02-09
> **Abubaker said:**
> 
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
P FAT16 >32M               0   1  1     8 254 63     144522 [DellUtility]
D FAT32 LBA                9   0  1  4186 254 63   67119570 [NO NAME]
P HPFS - NTFS              9  13  5  1314 119 21   20971520 [RECOVERY]
* HPFS - NTFS           1314 119 22 13833  53 21  201113577 [OS]
**D Linux                13834   0  1 13954 254 62    1943864**
D Linux                13955   1  1 15170 254 62   19534976
L Linux                15171   1  1 18209 254 63   48821472
L Linux Swap           18210   1  1 18452 254 43    3903712
L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

I think you could keep the linux partition marked in bold if you want to delete either your RECOVERY or DellUtility partition; then I think testdisk will allow you to mark the bold linux partition as "P". But if you want to keep your DellUtility and RECOVERY partitions, it looks like you will have to delete your linux partition. If you really want to keep all three partitions, i.e. the linux partition, DellUtility, and the RECOVERY partition, what you could do is temporarily delete DellUtility or RECOVERY so that you can make the linux partition "P", write the partition table, and then afterwards you could shrink that partition just a little in order to allow that linux partition to become a logical partition instead of a primary partition. Then you could run testdisk again and recover all your partitions, including both the DellUtility and RECOVERY partitions. It's up to you if you want to go through the trouble.

---

### Post by Abubaker on 2009-02-09
I can delete the Dell Utility partition. I dont need it. But making the other linux partition (below the bold one) to 'D', deletes the partition? why is that?

---

### Post by caljohnsmith on 2009-02-09
Won't testdisk let you keep that linux partition by marking it as "L"? That's what I originally recommended in post #4.

---

### Post by Abubaker on 2009-02-09
I got my Windows partitions after writing the partition table. I will have to check to see if Linux is fine now. Anyways, thanks for your help.

Now I will have to find a way to disable my Dell Media Direct button in Linux.

---

### Post by caljohnsmith on 2009-02-10
Glad to hear the partition recovery effort was a success. Good luck and hope things go smoother for you now in Ubuntu.

---

