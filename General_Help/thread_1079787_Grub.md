---
title: "Grub"
date: 2009-02-24
forum: General Help
---

### Post by RedSingularity on 2009-02-24
I am trying to boot but i am getting a Grub Error 2.  Can someone point me in the right direction as to the fix?  Thanks.

---

### Post by caljohnsmith on 2009-02-24
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by RedSingularity on 2009-02-24
When i type that i get a message that says "no such file or directory".

---

### Post by deepakbm on 2009-02-24
> **Shadow121 said:**
> When i type that i get a message that says "no such file or directory".

Try reinstalling Grub

---

### Post by RedSingularity on 2009-02-24
Thats what i originally did and it got me to this point.

---

### Post by RedSingularity on 2009-02-25
Oh ok, here is the Info you requested........
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 278657935 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f638

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005c191

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   612,992,204   612,992,142  83 Linux
/dev/sdb2         612,992,205   625,137,344    12,145,140   5 Extended
/dev/sdb5         612,992,268   625,137,344    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b9d708e4-d392-4c20-9dca-28254dfd006a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="6114bdd7-db0a-46d6-80a7-cabf8fd31658" TYPE="swap" 
/dev/sdb1: UUID="0b41bdc8-5b8d-4648-8936-fdcf190e6d1d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="227cb508-8c87-48fb-bc1d-a83e1767b7e8" TYPE="swap" 
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


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        0

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
# kopt=root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b9d708e4-d392-4c20-9dca-28254dfd006a

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Linux Ubuntu 8.10 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
savedefault
boot


========================== sda1/boot/grub/grub.conf: ==========================

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
timeout        5

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
# kopt=root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b9d708e4-d392-4c20-9dca-28254dfd006a

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        hd(0,0)
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet
boot

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a 
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b9d708e4-d392-4c20-9dca-28254dfd006a 
initrd        /boot/initrd.img-2.6.27-7-generic

#title        Ubuntu 8.10, memtest86+
#uuid        b9d708e4-d392-4c20-9dca-28254dfd006a
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
#title        Linux Ubuntu 8.10 (on /dev/sdb1)
#root        (hd0,0)
#kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d 
#initrd        /boot/initrd.img-2.6.27-9-generic
#savedefault
#boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b9d708e4-d392-4c20-9dca-28254dfd006a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6114bdd7-db0a-46d6-80a7-cabf8fd31658 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 142.6GB: boot/grub/grub.conf
   4.0GB: boot/grub/menu.lst
 142.6GB: boot/grub/stage2
 142.2GB: boot/initrd.img-2.6.27-11-generic
 142.2GB: boot/initrd.img-2.6.27-7-generic
 142.2GB: boot/vmlinuz-2.6.27-11-generic
 142.2GB: boot/vmlinuz-2.6.27-7-generic
 142.2GB: initrd.img
 142.2GB: initrd.img.old
 142.2GB: vmlinuz
 142.2GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout        0

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
# kopt=root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d

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

title        Linux Ubuntu 8.10
uuid        0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.





=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=227cb508-8c87-48fb-bc1d-a83e1767b7e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

=================== sdb1: Location of files loaded by Grub: ===================


 219.2GB: boot/grub/menu.lst
 219.2GB: boot/grub/stage2
 219.1GB: boot/initrd.img-2.6.27-11-generic
 219.2GB: boot/initrd.img-2.6.27-11-server
 219.2GB: boot/initrd.img-2.6.27-7-generic
 219.2GB: boot/initrd.img-2.6.27-9-generic
 219.2GB: boot/vmlinuz-2.6.27-11-generic
 219.3GB: boot/vmlinuz-2.6.27-11-server
 219.3GB: boot/vmlinuz-2.6.27-7-generic
 219.3GB: boot/vmlinuz-2.6.27-9-generic
 219.2GB: initrd.img
 219.1GB: initrd.img.old
 219.3GB: vmlinuz
 219.2GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-25
It looks like your Grub is configured correctly, so to get a Grub error 2 under those circumstances is often a result of how you have your HDDs set up in BIOS. How about going into your BIOS and let me know what HDD-related settings you have available, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. Also, do you know which drive you are booting on start up? You have Ubuntu installed to both your 160 GB sda drive and also your 320 GB sdb drive. And lastly, are both your Ubuntu installs new, or did you previously have them booting OK before getting a Grub error 2?

---

### Post by RedSingularity on 2009-02-25
Ok, i will check my HDD info when i get home.  As for the ubuntu installs i will be getting rid of the larger one.  I already have unplugged the SATA cable from the Motherboard.

---

### Post by RedSingularity on 2009-02-25
Ok here are some HDD settings, these are all SATA, i have no IDE HDD's installed.

-LBA/Large Mode: Auto
-Block (Multi-sector transfer)
-PIO Mode: 4
-DMA Mode: Auto
-S.M.A.R.T:  Auto
-32bit data transfer:  Enabled

---

### Post by caljohnsmith on 2009-02-25
Try changing "LBA/Large Mode" to "LBA" instead of "Auto". If you still get a Grub error 2, then also change "DMA Mode" to "off", and let me know if that makes any difference in the booting behavior.

---

### Post by RedSingularity on 2009-02-25
I cant turn DMA off but i can choose different settings in it.  A few people have said to turn it off.  is that option supposed to be in the bios?  Its a new motherboard.  And as for LBA i think i can only disable it but i will check.

---

### Post by jaminux on 2009-02-25
Just a thought.

I had a similar error, and couldn't work out why I was getting it.

I eventually worked out that I had changed the boot order of my hard drives so that the one without the install of Ubuntu was booting.

Might be completely irrelevant, but often the most simple solution is the most likely.

---

### Post by RedSingularity on 2009-02-25
I had the same thing once.  It just turned out to be that simple.  This time, however, I suspected that so i checked to be safe.  I even unplugged the HDD with the other OS installed on it........still no dice.

---

### Post by RedSingularity on 2009-02-25
There is no option to disable the DMA.  I played with it but still no success.  Does the option to turn off the DMA come with the Western Digital Disk that came with my HDD?  Many people have said that turning that off does the trick but i dont have that option.

---

### Post by caljohnsmith on 2009-02-25
So what exact settings do you have under "DMA Mode" and "LBA/Large Mode" in your BIOS?

---

### Post by RedSingularity on 2009-02-25
I have DMA at "auto" and LBA at "auto".  I can change DMA to things like "UDMA-6" and i can change LBA to "disable".  BTW i found this while trying to install grub for the 10000th time.....

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

Those lines with failed next to them got me thinking.  What is that?  Does it have to do with my problem?

---

### Post by caljohnsmith on 2009-02-25
Those "failed" lines in the Grub output you posted are expected, because you installed Grub to (hd0,0) or the boot sector of sda1; whenever you install Grub to the boot sector of a partition, it omits installing its stage1.5 file since the sectors immediately following the partition boot sector are not usually available. Is your Ubuntu install a new install? How about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by RedSingularity on 2009-02-25
Here ya go.......

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299805029   149902483+  83  Linux
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc0cb8896

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   398292991   199145472    7  HPFS/NTFS
```and.......

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=299804967, Id=83, bootable
/dev/sda2 : start=299805030, size= 12771675, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=299805093, size= 12771612, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     2048, size=398290944, Id= 7
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
```
SDB Is a removable disk. (USB)

---

### Post by RedSingularity on 2009-02-25
I saw one of your posts in another area.  You said to do this to check the grub version.

```

grub:
  Installed: 0.97-29ubuntu21
  Candidate: 0.97-29ubuntu21
  Version table:
 *** 0.97-29ubuntu21 0
        500 cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
        500 http://archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```Thats what i got.  Its the ubuntu21 install.  You said it was not compatable?  Got this info [HERE](http://ubuntuforums.org/showthread.php?t=959506&page=2)

---

### Post by RedSingularity on 2009-02-25
THAT DID IT!!!!!  I am back up and running!  I guess i had the older version of grub set on it?  Thanks for all your help!!!!!!!!!!!!!!!!!  :)

---

