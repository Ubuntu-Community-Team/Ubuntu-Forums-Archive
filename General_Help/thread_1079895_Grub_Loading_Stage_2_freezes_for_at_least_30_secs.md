---
title: "Grub Loading Stage 2 freezes for at least 30 secs"
date: 2009-02-24
forum: General Help
---

### Post by jjustin01 on 2009-02-24
I have been trying to solve this problem for quite a while now and I don't what else except post for help.

I am dual booting Ubuntu and Vista.

fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93940ead

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+   5  Extended
/dev/sda2   *          63        3887    30724312+   7  HPFS/NTFS
/dev/sda3            3888       19457   125066025    7  HPFS/NTFS
/dev/sda5               1          62      497952   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            3953       14593    85473832+   7  HPFS/NTFS
/dev/sdb2               1        3952    31744408+   5  Extended
/dev/sdb5            1825        2128     2441848+  82  Linux swap / Solaris
/dev/sdb6            2129        3952    14651248+  83  Linux
/dev/sdb7               1        1824    14651185+  83  Linux
```

/dev/sda5 is my /boot partition while swap, /, and /home partitions are on sdb

/grub/device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Let me know what else would useful for you to see and I will post it.  Also, I have already tried "link stage1 to stage2" fix.  Before that, it would hang on "loading stage1.5" for 30 seconds and then on "loading stage2" for another 30 seconds.

---

### Post by cariboo on 2009-02-24
Your problem may be that you don't have any primary partitions on your first hard drive. You may be able to fix that using gparted, but to be sure backup all your data first.

If it was my system, I'd just start from scratch and install Windows on the first primary partition, Use the second primary partition for whatever you have on the second partiton, and install Ubuntu on the third primary partition. Your second drive looks to be OK.

Jim

---

### Post by caljohnsmith on 2009-02-25
> **cariboo907 said:**
> Your problem may be that you don't have any primary partitions on your first hard drive.
I disagree: the first sda HDD has sda2 and sda3, and both of those are primary partitions. Also, I don't see how not having any primary partitions would cause the delay in loading Grub's stage2 file. I'm just curious, but why do you think that? If you have seen evidence of that somewhere, would you please provide a link? I would appreciate it since I would like to know if that has happened to someone before.

**Jjustin01**, I think it would help to first get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup.

---

### Post by jjustin01 on 2009-02-25
Dang, that's one heck of a nice little script.  Below is the output.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 70784 of 
    the same hard drive for the stage2 file. A stage2 file is at this location 
    on /dev/sda. Stage2 looks on partition #5 for /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93940ead

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       996,029       995,967   5 Extended
/dev/sda5                 126       996,029       995,904  83 Linux
/dev/sda2    *        996,030    62,444,654    61,448,625   7 HPFS/NTFS
/dev/sda3          62,444,655   312,576,704   250,132,050   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          63,488,880   234,436,544   170,947,665   7 HPFS/NTFS
/dev/sdb2                  63    63,488,879    63,488,817   5 Extended
/dev/sdb5          29,302,623    34,186,319     4,883,697  82 Linux swap / Solaris
/dev/sdb6          34,186,383    63,488,879    29,302,497  83 Linux
/dev/sdb7                 189    29,302,559    29,302,371  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="264A5F354A5F00CB" TYPE="ntfs" 
/dev/sda3: UUID="785AEC0E5AEBC74A" LABEL="Movies" TYPE="ntfs" 
/dev/sda5: UUID="86ae9a41-b97b-4ed1-8223-9352c010f4e7" TYPE="ext3" 
/dev/sdb1: UUID="10A43EC6A43EADDA" LABEL="SecondaryDrive" TYPE="ntfs" 
/dev/sdb5: UUID="c30ee625-abb8-4928-9a19-8e1d0977b03a" TYPE="swap" 
/dev/sdb6: UUID="4d92c679-50b6-466a-b464-a55b21e5cc24" TYPE="ext3" 
/dev/sdb7: UUID="385155d0-059d-4b22-84ca-15b79d9ddd70" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /boot type ext3 (rw,relatime)
/dev/sdb6 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/SecondaryDrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/Movies type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jj)


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=86ae9a41-b97b-4ed1-8223-9352c010f4e7

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		86ae9a41-b97b-4ed1-8223-9352c010f4e7
kernel		/vmlinuz-2.6.27-11-generic root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		86ae9a41-b97b-4ed1-8223-9352c010f4e7
kernel		/vmlinuz-2.6.27-11-generic root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro  single
initrd		/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=================== sda5: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.27-11-generic
    .0GB: initrd.img-2.6.27-7-generic
    .0GB: vmlinuz-2.6.27-11-generic
    .0GB: vmlinuz-2.6.27-7-generic

=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=86ae9a41-b97b-4ed1-8223-9352c010f4e7

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		86ae9a41-b97b-4ed1-8223-9352c010f4e7
kernel		/vmlinuz-2.6.27-11-generic root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		86ae9a41-b97b-4ed1-8223-9352c010f4e7
kernel		/vmlinuz-2.6.27-11-generic root=UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 ro  single
initrd		/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb7 :
UUID=385155d0-059d-4b22-84ca-15b79d9ddd70 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=86ae9a41-b97b-4ed1-8223-9352c010f4e7 /boot ext3 relatime 0 2
# Entry for /dev/sdb6 :
UUID=4d92c679-50b6-466a-b464-a55b21e5cc24 /home ext3 relatime 0 2
# Entry for /dev/sdb5 :
UUID=c30ee625-abb8-4928-9a19-8e1d0977b03a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/SecondaryDrive ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Movies ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb7: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.27-11-generic
    .0GB: boot/initrd.img-2.6.27-7-generic
    .0GB: boot/vmlinuz-2.6.27-11-generic
    .0GB: boot/vmlinuz-2.6.27-7-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-25
Just as an experiment to see if it makes any difference, have you tried installing Grub to the MBR of your sdb drive and booting the sdb drive on start up? If you haven't tried that and are willing to give it a shot just to see if Grub behaves differently, how about doing:
```
sudo grub
grub> root (hd1,6)
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot the sdb drive, and let me know what happens. We can can work from there.

---

### Post by jjustin01 on 2009-02-25
That worked. I can't boot into my Vista install, but Grub loads instantly.

What next? :)

---

### Post by caljohnsmith on 2009-02-25
Great, glad to hear that worked. Since you can now boot Ubuntu from the sdb drive, there is no reason to keep a boot partition on you sda drive; if you want help modifying Ubuntu so you can remove your sda5 boot partition, let me know. In the meantime, to boot Windows, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Vista entry with:
```
title Windows Vista
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Also, it would be good to restore a Windows MBR to your sda drive since you don't need Grub in its MBR any more, and that way you should be be able to boot directly into Vista if you boot your sda drive on start up (that's good insurance in case something ever happens to your sdb drive):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes or if you run into problems.

---

### Post by jjustin01 on 2009-02-25
Ha ha, I removed the sda5 partition and now I'm getting the good 'ol "Grub Error 15".  Working on that right now.  I think my menu.lst isn't mapped correctly.

---

### Post by jjustin01 on 2009-02-25
I'm having no luck. I removed the sda5 partition. When that happened I got a Grub Error 15 with "Boot from (hd0,5) ext3 sda5UUID". I checked UUIDs in menu.lst and they were still point to the same UUID as sda5 so I changed it to point the sdb7 parition.  This time, while I still get the Grub Error 15 message with no boot, it's at least saying "Boot from (hd0,6) ext3 sdb7UUID" across the top of the screen.

Would it be easier to reinstall Ubuntu and tell it to install Grub on hd1,0?

---

### Post by jjustin01 on 2009-02-25
Reinstalled Ubuntu with Grub on the sdb7 partition.  Editing menu.lst to include the mapping for vista and it's all working perfectly.

@caljohnsmith thanks your help. I really appreciate it. You have made my life much more tolerable now that I don't have to wait so long just get past Grub.  Thank you.

---

### Post by caljohnsmith on 2009-02-25
Glad to hear the reinstallation went smoothly and that your Grub still works without a 30 second delay; cheers and enjoy your dual-boot Ubuntu/Vista setup. :)

---

