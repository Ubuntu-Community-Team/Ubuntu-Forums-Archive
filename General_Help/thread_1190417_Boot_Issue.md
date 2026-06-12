---
title: "Boot Issue"
date: 2009-06-17
forum: General Help
---

### Post by Balagast on 2009-06-17
I am slightly new to ubuntu, being a long time windows user.  I recently installed ubuntu 8.04 on my machine to dual boot with XP.

I had XP installed on a 30 IDE HD, and I had a 750 gig SATA drive that I had movies and music on.  I installed Ubuntu 9.04 initially on the SATA drive using the manual partioning tool in the ubuntu install and the install went just fine.  I was able to dual boot between both XP and Ubuntu, but I was having a lot of hardware issue with 9.04 so I decided to install 8.04 instaed.

After installing 8.04 most of my hardware was working just fine, and I was able to set up a lot of the things I was trying to.  I then rebooted and tryed to select the XP partition in GRUB, but when I do it just goes to a black screen and nothing else.  I have to hold the power button down to restart the PC.

Ubuntu still works great, but I would like to be able to get my windows install back for some CAD apps and playing HD movies.

Does anyone have any suggestions?  Thanks ahead of time.

---

### Post by x22 on 2009-06-17
welcome to the forum

sometimes "sudo update-grub" helps in such a case

---

### Post by Balagast on 2009-06-19
I just tried that and got the same thing ...

I was thinking the MBR for XP got messed up perhaps.  If I fix the MBR will I lose GRUB?

---

### Post by mhgsys on 2009-06-19
Well in case grub is on the windows disk, you will lose it indeed.
Anyway;
There's an easy way to reinstall/ recover grub after you fixed the mbr.

This is a good way to do that:


Bootup a live cd, open a terminal and do the following.

```
sudo grub
```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands

```

root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```

quit

```

Reboot:

Anyway; are you sure you have to fix the win mbr?

Can you post your output of /boot/grub/menu.lst 
And the output of fdisk -l

```

sudo gedit /boot/grub/menu.lst

```

```

sudo fdisk -l 
```
 
Also you might have a look here: 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1092259](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1092259)
Specially the script @meierfra is suggesting.



Hope this helps for you
mhgsys

---

### Post by Balagast on 2009-06-19
I will try that after I get home today from work ... thanks for those procedures.  The reason I think the windows MBR needs to be repaired is just from reading through other peoples issues.

The weird thing is I installed 9.04 and had issues to I deleted that install and installed 8.04 instead, but the XP boot issue didn't arise till after the second install.

---

### Post by Balagast on 2009-06-20
Here's the output from menu.lst:

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
# kopt=root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Here's the output from fdisk -l:

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cdc1cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3737    30017421    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0287356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       85104   683597848+   7  HPFS/NTFS
/dev/sdb2           85105       85171      538177+  82  Linux swap / Solaris
/dev/sdb3           85172       86387     9767520   83  Linux
/dev/sdb4           86388       91201    38668455   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f2ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    c  W95 FAT32 (LBA)

---

### Post by Balagast on 2009-06-20
Bump ... anyone got any ideas on what those reports mean?

---

### Post by mhgsys on 2009-06-21
@ Balagast. 

Try changing these lines in 
/boot/grub/menu.lst


```

sudo nano /boot/grub/menu.lst

```

Scroll down to ### END DEBIAN AUTOMAGIC KERNELS LIST

and change 
```

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```
to 
```

title Microsoft Windows XP Professional
rootnoverify (hd0,1)
chainloader +1

```

*Note: You can also just add new lines leaving the old ones in place, that way you could try various ways without having to edit boot/grub/menu.lst everytime.

*Notice* the l in menu.lst is on lower case L, not the number 1.

---

### Post by Balagast on 2009-06-21
I added those lines and when I selected that OS in GRUB is came back with an error saying no such partition existed ...

---

### Post by egalvan on 2009-06-21
In post #4, a suggestion was made to run a script by "meierfra".

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)


This script will read a lot of information, and write it to a text  file on your desktop.

Upload it here.

(put "code" tags around it to make it easier to read.)

This info will give us a much better understanding of your current drives, partitions, etc...

"meierfra" has been around a long while...
he has a deep understanding of boot "stuff"

this is a script that has been tested...
no problems with it...

help us to help you.

---

### Post by Balagast on 2009-06-21
Here are the results of that script:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

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

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cdc1cdb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    60,034,904    60,034,842   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0287356

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,367,195,759 1,367,195,697   7 HPFS/NTFS
/dev/sdb2       1,367,195,760 1,368,272,114     1,076,355  82 Linux swap / Solaris
/dev/sdb3       1,368,272,115 1,387,807,154    19,535,040  83 Linux
/dev/sdb4       1,387,807,155 1,465,144,064    77,336,910  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2E1046A61046753D" TYPE="ntfs" 
/dev/sdb1: UUID="D060E9DE60E9CAF4" LABEL="Media Drive" TYPE="ntfs" 
/dev/sdb2: TYPE="swap" UUID="c2c7f372-79cb-446b-8e09-d4ca737934c5" 
/dev/sdb3: UUID="b937f1e8-e650-4c1e-8a1b-1ce35df79606" TYPE="ext3" 
/dev/sdb4: UUID="b8d74d7b-196f-4fd5-b07d-a86618fad9d2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
/dev/sdb4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
/dev/sdb1 on /media/Media Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title Microsoft Windows XP Professional
rootnoverify (hd0,1)
chainloader +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=b937f1e8-e650-4c1e-8a1b-1ce35df79606 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb4
UUID=b8d74d7b-196f-4fd5-b07d-a86618fad9d2 /home           ext3    relatime        0       2
# /dev/sdb2
UUID=c2c7f372-79cb-446b-8e09-d4ca737934c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 703.6GB: boot/grub/menu.lst
 703.5GB: boot/grub/stage2
 703.6GB: boot/initrd.img-2.6.24-23-generic
 703.6GB: boot/initrd.img-2.6.24-23-generic.bak
 703.5GB: boot/initrd.img-2.6.24-24-generic
 703.6GB: boot/initrd.img-2.6.24-24-generic.bak
 703.5GB: boot/vmlinuz-2.6.24-23-generic
 703.5GB: boot/vmlinuz-2.6.24-24-generic
 703.5GB: initrd.img
 703.6GB: initrd.img.old
 703.5GB: vmlinuz
 703.5GB: vmlinuz.old
```

Thanks for all the help guys.

---

### Post by Balagast on 2009-06-24
Anyone have any thoughts?

---

### Post by Balagast on 2009-06-27
bump ...

---

### Post by mhgsys on 2009-06-28
Sorry for the delay, 

Try this is your menu.lst.
 
```

title Microsoft Windows XP Professional
map                   (hd0,0) (hd1,0)
map                   (hd1,0) (hd0,0)
rootnoverify          (hd1,0)
chainloader    +1

```

See if it boots.

---

### Post by Balagast on 2009-06-30
Well  I tried that and it came up with NTLDR is missing, Press CTRL+ALT+DLT to restart.

Any suggestions??

---

### Post by Balagast on 2009-07-01
OK so I was reading through so other treads trying to figure this out, and I ran across this thread.

[http://ubuntuforums.org/showthread.php?t=1082264&highlight=NTLDR](http://ubuntuforums.org/showthread.php?t=1082264&highlight=NTLDR)

From that it would seem that GRUB is pointing it to the correct partition.  I read it can throw the NTLDR error is the boot.ini file isn't present.  Is it possible that file somehow got removed while installing ubuntu?

Either way, I appreciate the continuing help.

---

### Post by Balagast on 2009-07-01
The more I think about this, shouldn't the windows boot in menu.lst just be:

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1
I'm really new to this aspect of using linux, but just logically that is where windows is installed.

---

### Post by ronaldprettyman on 2009-07-01
> **Balagast said:**
> Well  I tried that and it came up with NTLDR is missing, Press CTRL+ALT+DLT to restart.

Any suggestions??

This is the problem, check your boot.ini file on the windows installation, and get a super grub disk to rewrite the master boot record

It sounds like its curropted. You might want to get your xp disc and go into recovery mode run restoremb writemb, no its
```
C:\> fixboot
C:\> fixmbr
```
Then run your live cd, chroot into your ubuntu installation and fix grub
```
$ sudo dpkg-reconfigure grub
```
Might also need to rewrite grub with
```
grub
root (hd0,0)
setup (hd0)
```

A super grub disk can do all this automatically and rewrite a correct menu.lst for you google it, burn it, and keep it in a safe place, its a great tool to have

---

### Post by Balagast on 2009-07-01
I shall have to try that super GRUB disc ... I would probably have just used my XP disc, but it was asking for an admin password to use the recovery console and I never set one.  Its a really annoying windows glitch that is a pain to fix if you can't get onto the OS (need like 11 floppy discs).

Thanks ... I shall report back after work today.

---

### Post by ronaldprettyman on 2009-07-02
> **Balagast said:**
> I shall have to try that super GRUB disc ... I would probably have just used my XP disc, but it was asking for an admin password to use the recovery console and I never set one.  Its a really annoying windows glitch that is a pain to fix if you can't get onto the OS (need like 11 floppy discs).

Thanks ... I shall report back after work today.

In xp you just need to use a regedit though wine in a live cd to delete the adminstrator's password entry. You can find how to do this on google.

Also if its asking for a adminstrator password in the the recovery console this probably means at one time you set it, in XP pro you set it in the installation, in home you set it though the users control panel or though the command line.

---

### Post by lernatix on 2009-07-02
Sorry to hijack but i'm getting grub error 17 on bootup after i formatted my second hard drive with my hardy install.  Just to clarify,  i can fix this without an XP disc?

---

### Post by ronaldprettyman on 2009-07-02
> **lernatix said:**
> Sorry to hijack but i'm getting grub error 17 on bootup after i formatted my second hard drive with my hardy install.  Just to clarify,  i can fix this without an XP disc?

lol yes you shouldn't need the xp cd to fix this if your trying to fix Linux. Your new drive is probably supersedding your old drive in the count and messing up your numbers. Boot into a live cd and give us a couple output to tell you exactly how to fix it.
First figure out the drives
```
sudo fdisk -l
```
Your need to mount your disk from the live cd and fix the grub and fstab
Start a new thread if you need more help, this one is getting kinda long. It would be uber helpful if you put "Grub Error 17" in the title for people who have this problem in the future. Good luck.

---

### Post by lernatix on 2009-07-02
Thanks Ron,

I managed to borrow a WinXP cd from the boss today.
5 mins later after a "fixboot" and "fixmbr", i'm away!

Now I need to know how to get rid of the grub loader,
it still asks me if I want to load XP or Ubuntu but
the Ubuntu hard drive has been formatted.

Will I be needing to find my Ubuntu CD to remove grub?

---

### Post by ronaldprettyman on 2009-07-02
> **lernatix said:**
> Thanks Ron,

I managed to borrow a WinXP cd from the boss today.
5 mins later after a "fixboot" and "fixmbr", i'm away!

Now I need to know how to get rid of the grub loader,
it still asks me if I want to load XP or Ubuntu but
the Ubuntu hard drive has been formatted.

Will I be needing to find my Ubuntu CD to remove grub?

Once your in XP, super+r>>cmd>>"BOOTCFG /rebuild">>reboot see if that fixed then
once your back in xp, right click my computer and select manage. Go down to disk/partitions and check to see that you only have one, or that all of them are mounted in windows(have a letter association).

I don't know how you formated the ubuntu installation, but I'm fairly certain that Grub looks for the menu.lst on the /boot partition every time it boots.

---

### Post by Balagast on 2009-07-02
> **ronaldprettyman said:**
> In xp you just need to use a regedit though wine in a live cd to delete the adminstrator's password entry. You can find how to do this on google.

Also if its asking for a adminstrator password in the the recovery console this probably means at one time you set it, in XP pro you set it in the installation, in home you set it though the users control panel or though the command line.

Trust me I never set a PW for the administrator, and none of the PW's I ever use for anything work.  I have read its an actual windows XP glitch, and its really annoying.

---

