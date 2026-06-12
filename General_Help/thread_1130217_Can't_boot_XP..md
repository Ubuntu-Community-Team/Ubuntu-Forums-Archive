---
title: "Can't boot XP."
date: 2009-04-19
forum: General Help
---

### Post by Newuser1111 on 2009-04-19
GRUB Won't boot XP.

menu.lst:
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
# kopt=root=UUID=8bb10496-fa6f-4135-809b-4a14d9bc9856 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8bb10496-fa6f-4135-809b-4a14d9bc9856

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

title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04
uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8bb10496-fa6f-4135-809b-4a14d9bc9856 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

#title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic #(recovery mode)
#uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8bb10496-#fa6f-4135-809b-4a14d9bc9856 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu jaunty (development branch), memtest86+
#uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows XP
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1

#title		Windows 98
#rootnoverify	(hd0,1)
#savedefault	--wait=2
#makeactive
#chainloader	/io.sys

#title		Windows 98
#rootnoverify    (hd0,0)
#chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Reinstall Vista
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1
```
(Picture attached)

EDIT:
And I think the Reinstall Vista one might not be working.

---

### Post by codeseer on 2009-04-19
Results.txt please: [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by Newuser1111 on 2009-04-19
> **codeseer said:**
> Results.txt please: [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")I don't think I used it right, the RESULTS.txt is blank.

---

### Post by codeseer on 2009-04-19
```

chmod +x boot*.sh
sudo ./boot*.sh

```

---

### Post by Newuser1111 on 2009-04-19
> **codeseer said:**
> ```

chmod +x boot*.sh
sudo ./boot*.sh

```RESULTS2.txt:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 285940935.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd23d125d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   240,766,154   240,766,092   7 HPFS/NTFS
/dev/sda2         240,766,155   285,940,934    45,174,780   5 Extended
/dev/sda5    *    240,766,218   261,281,159    20,514,942   7 HPFS/NTFS
/dev/sda6         261,281,223   281,796,164    20,514,942  83 Linux
/dev/sda7         281,796,228   285,940,934     4,144,707  82 Linux swap / Solaris
/dev/sda3         285,940,935   288,077,579     2,136,645   b W95 FAT32
/dev/sda4         288,077,580   312,576,704    24,499,125   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ACF8A915F8A8DF38" TYPE="ntfs" 
/dev/sda3: UUID="B1EF-20FD" TYPE="vfat" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda5: UUID="D00CC41E0CC3FE0A" TYPE="ntfs" 
/dev/sda6: UUID="8bb10496-fa6f-4135-809b-4a14d9bc9856" TYPE="ext4" 
/dev/sda7: UUID="e263999f-26d6-4a97-a4fa-f92e03ba9d7b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/djk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=djk)


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
# kopt=root=UUID=8bb10496-fa6f-4135-809b-4a14d9bc9856 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8bb10496-fa6f-4135-809b-4a14d9bc9856

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

title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04
uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8bb10496-fa6f-4135-809b-4a14d9bc9856 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

#title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic #(recovery mode)
#uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8bb10496-#fa6f-4135-809b-4a14d9bc9856 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu jaunty (development branch), memtest86+
#uuid		8bb10496-fa6f-4135-809b-4a14d9bc9856
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

#title		Windows 98
#rootnoverify	(hd0,1)
#savedefault	--wait=2
#makeactive
#chainloader	/io.sys

#title		Windows 98
#rootnoverify    (hd0,0)
#chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Reinstall Vista
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=8bb10496-fa6f-4135-809b-4a14d9bc9856 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e263999f-26d6-4a97-a4fa-f92e03ba9d7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 136.1GB: boot/grub/menu.lst
 135.5GB: boot/grub/stage2
 136.6GB: boot/initrd.img-2.6.28-11-generic
 134.3GB: boot/vmlinuz-2.6.28-11-generic
 136.6GB: initrd.img
 134.3GB: vmlinuz
```

---

### Post by codeseer on 2009-04-19
```
gksudo gedit /boot/grub/menu.lst
```

Change:

```
title		Windows XP
rootnoverify	**(hd0,1)**
savedefault
makeactive
chainloader	+1
```

To:

```

title		Windows XP
rootnoverify	**(hd0,4)**
savedefault
makeactive
chainloader	+1
```

Save. Restart. Try again.

---

### Post by Newuser1111 on 2009-04-19
```
Error 12: Invalid device requested

Press any key to continue...
```

---

### Post by codeseer on 2009-04-19
Mount your XP partition up and check that it has a boot.ini file in the root.

---

### Post by Newuser1111 on 2009-04-19
> **codeseer said:**
> Mount your XP partition up and check that it has a boot.ini file in the root.It doesn't.

---

### Post by codeseer on 2009-04-19
Ok, if I remember correctly, you can put in the Windows XP cd and boot into recovery mode. Then run these:

```
bootcfg /Rebuild
```

```
fixboot C:
```
(I think this is right, it's fixboot something; might have to look at the help by typing 'fixboot /?')

```

map

fixmbr \device\harddisk#

```
(Where # is whatever number 'map' gave you)

You might also have to extract NTLDR and Ntdetect.com from the CD; but we'll get to that if this doesn't work.

---

### Post by Newuser1111 on 2009-04-19
Now Vista and XP don't work.

Vista:
```
Starting up ...

NTLDR is missing
Press Ctrl+Alt+Del to restart
```

XP:
```
Error 12: Invalid device requested

Press any key to continue...
```

---

### Post by codeseer on 2009-04-19
You must have tagged the Vista partition instead of the XP partition with those commands. What options did map give you?

Edit:

I'm thinking since you have a 'shelter' of sorts for operating systems; it may be easiest for you to boot into Vista and load EasyBCD to have it set up the booting of the others.

---

### Post by Newuser1111 on 2009-04-19
I'm just am going to reinstall all of the OSes instead.

---

### Post by codeseer on 2009-04-19
Here's the Vista restoration info: [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

```
bootrec /fixboot
bootrec /RebuildBcd
bootrec /fixmbr
```

---

### Post by Newuser1111 on 2009-04-19
> **codeseer said:**
> Here's the Vista restoration info: [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

```
bootrec /fixboot
bootrec /RebuildBcd
bootrec /fixmbr
```I don't have a Vista disc. (Vista came with the laptop and to reinstall I have to boot the PRESARIO_RP partiton.)

But I've already started installing XP.
(Install XP then Ubuntu then Vista.)

---

### Post by codeseer on 2009-04-19
Gotta love those companies that don't give you the media.

---

### Post by Newuser1111 on 2009-04-19
Now I've installed XP and Ubuntu but I can't get to PRESARIO_RP.
When I try to reinstall Vista it just boots XP.

---

### Post by codeseer on 2009-04-24
> **Newuser1111 said:**
> Now I've installed XP and Ubuntu but I can't get to PRESARIO_RP.
When I try to reinstall Vista it just boots XP.

Might try pointing Grub to that partition or using a boot disk that would be capable of reading whatever file system that partition is and running the setup application.

---

### Post by Newuser1111 on 2009-04-26
> **codeseer said:**
> Might try pointing Grub to that partition or using a boot disk that would be capable of reading whatever file system that partition is and running the setup application.I got recovery DVDs(cost $16).
So now that partition is gone(and the XP and Ubuntu ones are also gone).

I can't put XP back on to it because I installed XP onto another computer(A computer I made from parts I found in my garage).

---

### Post by codeseer on 2009-04-26
That works. I hate companies that don't include the discs. :(

---

