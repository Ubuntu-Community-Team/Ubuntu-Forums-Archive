---
title: "Grub won't load"
date: 2009-02-17
forum: General Help
---

### Post by Artess on 2009-02-17
I have Windows Vista and Ubuntu on one PC, installed on separate hard drives. I have configured Windows boot menu so that I use it by default to choose OS when loading (used EasyBCD). Everything worked fine until recently when I downloaded latest Ubuntu updates and rebooted then into Windows. When I tried to boot into Ubuntu again a few days later, after choosing OS it said:
```
         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```
waiting for some input. I'm completely unfamiliar with this stuff so I have no idea how can I help this. EasyBCD still detects Linux partitions and bootsectors OK... or at least it seems so.

---

### Post by caljohnsmith on 2009-02-17
Do you have a Live CD you can boot to use for troubleshooting? If so, how about doing that, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Artess on 2009-02-18
that's it:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #738395658 on boot drive #2
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 764691978 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7103f89c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   234,438,655   234,436,608   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3d958d17

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   195,356,671   195,354,624   7 HPFS/NTFS
/dev/sdb2         195,356,672   390,711,295   195,354,624   7 HPFS/NTFS
/dev/sdb3         390,711,296   586,065,919   195,354,624   7 HPFS/NTFS
/dev/sdb4         586,067,265   781,417,664   195,350,400   f W95 Ext d (LBA)
/dev/sdb5         722,394,918   738,395,594    16,000,677  82 Linux swap / Solaris
/dev/sdb6         738,395,658   781,417,664    43,022,007  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92339233

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   234,438,655   234,436,608   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="50AE031FAE02FCEA" LABEL="My files" TYPE="ntfs" 
/dev/sdb1: UUID="3448B6F448B6B3C8" LABEL="Downloads" TYPE="ntfs" 
/dev/sdb2: UUID="1268E35E68E33EDB" LABEL="Games" TYPE="ntfs" 
/dev/sdb3: UUID="668C12478C1211E3" LABEL="Downloads 2" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="1818dbb0-713c-4be1-b32a-efe209a0a524" 
/dev/sdb6: UUID="84a71f29-c761-42db-bac8-9b4f74441fae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="720C701C0C6FDA1D" LABEL="System Disk" TYPE="ntfs" 
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
timeout		0

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
# kopt=root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=84a71f29-c761-42db-bac8-9b4f74441fae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=1818dbb0-713c-4be1-b32a-efe209a0a524 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 391.6GB: boot/grub/menu.lst
 391.5GB: boot/grub/stage2
 391.6GB: boot/initrd.img-2.6.24-21-generic
 391.5GB: boot/initrd.img-2.6.24-21-generic.bak
 391.5GB: boot/initrd.img-2.6.27-11-generic
 391.6GB: boot/initrd.img-2.6.27-7-generic
 391.5GB: boot/initrd.img-2.6.27-9-generic
 391.4GB: boot/vmlinuz-2.6.24-21-generic
 391.5GB: boot/vmlinuz-2.6.27-11-generic
 391.6GB: boot/vmlinuz-2.6.27-7-generic
 391.5GB: boot/vmlinuz-2.6.27-9-generic
 391.5GB: initrd.img
 391.5GB: initrd.img.old
 391.5GB: vmlinuz
 391.5GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-18
> **Artess said:**
> ```

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 764691978 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. [COLOR="Red"]Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst[/COLOR].
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

```
As highlighted in red, it looks like part of the problem is that Grub's stage2 boot file looks on partition #7 (sdb7) for the menu.lst, yet your Ubuntu partition is sdb6. That would explain why you are able to get as far as the Grub command line when you boot Ubuntu from Vista, because Grub gets as far as loading the stage2 file, yet stage2 can't find the menu.lst. How about doing the following from your Live CD (make sure that sdb6 is not mounted anywhere when you run these commands):
```
sudo grub
grub> root (hd1,5)
grub> setup (hd1,5)
grub> quit
```
The other small problem is that your menu.lst needs some tweaking, because all the Ubuntu entries use (hd1,6) which is sdb7 instead of (hd1,5) which is sdb6, so how about doing:
```
sudo mount /dev/sdb6 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd1,5) similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		[COLOR="Blue"](hd1,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=84a71f29-c761-42db-bac8-9b4f74441fae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```
And most importantly, change the "# groot..." line to use (hd1,5) so that your menu.lst won't break the next time you get a kernel upgrade:
```
# groot=[COLOR="Blue"](hd1,5)[/COLOR]
```
Then reboot, choose Ubuntu from your Vista boot menu, and let me know how far you get. We can work from there if necessary.

---

### Post by Artess on 2009-02-18
Thanks a lot! That solved all the problems.

---

### Post by caljohnsmith on 2009-02-18
Glad that worked OK; cheers and enjoy Ubuntu and Vista. :)

---

### Post by Artess on 2009-03-04
I bought a new HDD and rearranged some space on my older ones. So, I get the same trouble again. Here what does boot_info_script say:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #738395658 on boot drive #2
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7103f89c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   234,438,655   234,436,608   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3d958d17

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   781,420,719   781,420,657  42 SFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdb78123c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,048,578,047 1,048,576,000   7 HPFS/NTFS
/dev/sdc2       1,048,578,048 1,953,519,615   904,941,568   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92339233

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   234,438,655   234,436,608   7 HPFS/NTFS

/dev/sdd1 ends after the last cylinder of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="50AE031FAE02FCEA" LABEL="My files" TYPE="ntfs" 
/dev/sdb2: UUID="1268E35E68E33EDB" LABEL="Games" TYPE="ntfs" 
/dev/sdb3: UUID="668C12478C1211E3" LABEL="Downloads 2" TYPE="ntfs" 
/dev/sdb4: TYPE="swap" UUID="1818dbb0-713c-4be1-b32a-efe209a0a524" 
/dev/sdb5: UUID="84a71f29-c761-42db-bac8-9b4f74441fae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="960465E60465CA37" LABEL="Downloads" TYPE="ntfs" 
/dev/sdc2: UUID="B01CF7881CF7483C" LABEL="Movies" TYPE="ntfs" 
/dev/sdd1: UUID="720C701C0C6FDA1D" LABEL="System Disk" TYPE="ntfs" 
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

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo/Log1: No such file or directory
```
What should I change to what this time to make it work again?

---

### Post by Artess on 2009-03-05
hello?

---

### Post by Artess on 2009-03-13
can anyone help me?

---

