---
title: "My Boot Loader Is Gone/ Access Data?"
date: 2009-06-17
forum: General Help
---

### Post by james.brantley on 2009-06-17
[SIZE=3]It appears as though I have broken my installation of Ubuntu and to make matters worse I did not back things up because I was so involved with customizing my desktop. I can not boot into Ubuntu because my machine goes into memtest when ever I attempt to boot into Ubuntu and apparently there is no way to edit this from windows. I am able to boot into Vista, is there anyway that I can access data that I saved while using Ubuntu from Vista? I have only one hard drive and a dual boot system. 
[/SIZE]

---

### Post by Dysport on 2009-06-17
Clearly you can't edit the GRUB menu from windows, but booting from a (X/K/Ed)Ubuntu LiveCD you should be able to edit the menu.lst as su.

---

### Post by james.brantley on 2009-06-17
> **Dysport said:**
> Clearly you can't edit the GRUB menu from windows, but booting from a (X/K/Ed)Ubuntu LiveCD you should be able to edit the menu.lst as su.
 
[SIZE=3]*I installed Ubuntu using Wubi. I have been told this will totally chance the process that needs to be used to rectify my issue. I have changed to boot from cd and have been unable to edit menu.lst (maybe because I use Wubi) as I am only able to view it as a text file using the following script-[/SIZE]
 
[SIZE=3]**sudo bash ~/Desktop/boot_info_script*.sh**[/SIZE]
 
[SIZE=3]Maybe I am doing someting wrong but the live cd will **ONLY **lead me top the initial insallation screen-[/SIZE]
[SIZE=3]"try ubuntu, install, test memory (yes the evil memtest), boot from hard disk."[/SIZE]
 
[SIZE=3]I have been working on this for 13 hours now, if I reformat than I have been defeated. [/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]It apears to me that Wubi might not be a wise way to install.[/SIZE]

---

### Post by Dysport on 2009-06-17
Well seems to me you're halfway there :) 
- In the LiveCD menu select "Try Ubuntu without any change to your computer"
- When you arrived in the gnome environment, open up a terminal (Accessoires ==> Terminal; or [Alt+F2] and "gnome-terminal")
- Make sure your linux partition is mounted (just click on it in the "Places" menu)
- In the terminal type "sudo gedit *NAMEofYOURlinuxDISK*/boot/grub/menu.lst"

Where *NAMEofYOURlinuxDISK* is probably /media/ubuntu or /media/disk or something like that.

From there you can check whether something messed with your GRUB or you can at least post the content of you menu.lst here for further help.

---

### Post by james.brantley on 2009-06-17
> **Dysport said:**
> Well seems to me you're halfway there :) 
- In the LiveCD menu select "Try Ubuntu without any change to your computer"
- When you arrived in the gnome environment, open up a terminal (Accessoires ==> Terminal; or [Alt+F2] and "gnome-terminal")
- Make sure your linux partition is mounted (just click on it in the "Places" menu)
- In the terminal type "sudo gedit *NAMEofYOURlinuxDISK*/boot/grub/menu.lst"

Where *NAMEofYOURlinuxDISK* is probably /media/ubuntu or /media/disk or something like that.

From there you can check whether something messed with your GRUB or you can at least post the content of you menu.lst here for further help.

[SIZE=3]I could not get the data via your method but is this the data that you mean?

 [/SIZE]```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39d23778

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,914,175   468,914,113   7 HPFS/NTFS
/dev/sda2         468,914,176   488,392,703    19,478,528   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 129     3,907,007     3,906,879   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="88FED00FFECFF38A" LABEL="COMPAQ" TYPE="ntfs" 
/dev/sda2: UUID="A8B2D2B2B2D2846A" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="C80CA47B0CA46662" LABEL="JBRANTLEY 1" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/JBRANTLEY 1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/COMPAQ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


  44.0GB: ubuntu/disks/boot/grub/menu.lst
  43.9GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  43.8GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic

```

---

### Post by hal8000 on 2009-06-17
> **james.brantley said:**
> [SIZE=3]*I installed Ubuntu using Wubi. I have been told this will totally chance the process that needs to be used to rectify my issue. I have changed to boot from cd and have been unable to edit menu.lst (maybe because I use Wubi) as I am only able to view it as a text file using the following script It apears to me that Wubi might not be a wise way to install.[/SIZE]

Using Wubi, installs Ubuntu on the same (NTFS partition) as windows. As such, you will neber have the full benefit or security froma a journaled linux partition, and also installing with wubi means that its shared with windows.

I dont think you can reinstall using grub, as the boot loader is part of the windows loader. Its safer to defrag windows (makes apace at the end of the drive) then use XP or Vista disk management to shrink the partition.
Then install Ubuntu and choose the option install in free partition space...and it goes without saying, back up all your important work and data first.

---

### Post by Dysport on 2009-06-17
Sorry, I just learned that my method wouldn't work with wubi as it creates some sort of image instead of a real partition.
Though I've never worked with wubi I read you can just install it again (just the bootloader) without any loss of data.

But here are my recommendations: 
[LIST]
[*]If you want to try Linux use a LiveCD or a Pendrivelinux. 
[*]If you want to use Linux on a regular basis from within Windows (although that is kind of perverted ;)) use VirtualBox - it's free and simple. 
[*]And lastly, if you really want to work with Linux (Ubuntu) - do a proper install with real partitions. You'll most likely save yourself a lot of headaches and it's just as easy as some crippled wubi install. Google for "Wubi boot problem": you'll get an amazing number of results :)
[/LIST]

Oh and BTW: I see in your grub menu.lst that the root is missing, see the empty brackets: > title        Ubuntu 9.04, kernel 2.6.28-11-generic
**root        ()/ubuntu/disks**
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=88FED00FFECFF38A loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic


I believe that's the problem. Maybe someone who knows wubi better can help you fix that under Windows.

---

### Post by mixmaster on 2009-06-17
> **Dysport said:**
> 
But here are my recommendations: 
[LIST]
[*]If you want to try Linux use a LiveCD or a Pendrivelinux. 
[*]If you want to use Linux on a regular basis from within Windows (although that is kind of perverted ;)) use VirtualBox - it's free and simple. 
[*]And lastly, if you really want to work with Linux (Ubuntu) - do a proper install with real partitions. You'll most likely save yourself a lot of headaches and it's just as easy as some crippled wubi install. Google for "Wubi boot problem": you'll get an amazing number of results :)
[/LIST]

Personally I find LiveCD and Pendrive access too slow to use on any sort of regular basis.
Linux in virtualbox works a treat under XP.  It is very useful where there are some programs which simply won't run under linux in any guise and where you are switching between the 2 frequently (in which case dual boot becomes a pain).
If you don't need the switching dual boot is good.  The ubuntu installer will shrink windows partitions for you during the install process.  Or if you are as paranoid as I am simply slap a second drive into the system.
Personally I regard Wubi as a bit of a publicity stunt.  You could use it for a taste of linux but I wouldn't use it for anything serious.

---

### Post by Dysport on 2009-06-17
> **mixmaster said:**
> Personally I find LiveCD and Pendrive access too slow to use on any sort of regular basis.


That's why I only recommended it for a try. It's really useful to get a first impression, but the low performance and the constantly spinning cd-drive are a real pain. 

> **mixmaster said:**
> Personally I regard Wubi as a bit of a publicity stunt.

Dead right, my friend :)


> **mixmaster said:**
> You could use it for a taste of linux but I wouldn't use it for anything serious.

Again, LiveCD or Pendrive is totally sufficient for that purpose.

---

