---
title: "Reorder GRUB on Triple boot: Ubuntu, XP, Xubuntu"
date: 2009-05-06
forum: General Help
---

### Post by Nathan Otis on 2009-05-06
I wanted to see what the differences were between Ub.... and Xub... So I took my dual boot and turned it into a triple boot.

My issue now is that I'd like Ubuntu to be the default OS, but currently Xubuntu is first on the list.

I opened up a terminal and entered:
```
sudo gedit /boot/grub/menu.lst
```

But I only see one kernal listed along with Windows (see copied menu.lst below)

#################################
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
#################################

How can I make Ubuntu the default OS again?

Thanks.

---

### Post by exutable on 2009-05-06
I'm not really familiar with this but try this

go into terminal

sudo grub

find /boot/grub/stage1

and post what that gets you

---

### Post by Nathan Otis on 2009-05-06
Short and sweet:

```
grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

grub>
```

---

### Post by caljohnsmith on 2009-05-06
It sounds like the issue is that Grub is using the menu.lst from the other installation you weren't booted into when you posted the menu.lst in your first post. If you boot into your other Ubuntu install, or access its menu.lst by mounting its partition, I think you will see the menu.lst that Grub displays on start up. If you have problems though and would like help sorting it all out, how about first downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by Nathan Otis on 2009-05-07
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2          30,716,280   117,258,434    86,542,155   5 Extended
/dev/sda5          30,716,343   101,659,319    70,942,977  83 Linux
/dev/sda6         114,270,408   117,258,434     2,988,027  82 Linux swap / Solaris
/dev/sda7         101,659,383   113,611,679    11,952,297  83 Linux
/dev/sda8         113,611,743   114,270,344       658,602  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders, total 53464320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    53,464,319    53,464,257  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="18A0054DA00532B4" TYPE="ntfs" 
/dev/sda5: UUID="394136cb-4e75-4ddf-806a-41da223ec840" TYPE="ext3" 
/dev/sda6: UUID="3007a9a0-fb8b-4462-a0fb-6c3e3cee5bee" TYPE="swap" 
/dev/sda7: UUID="751a56fb-aa8a-44b4-9bce-ffebccdecbd3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="0915557b-c676-4265-8b68-762e98ccd3cc" TYPE="swap" 
/dev/sdb1: UUID="7293ff72-570c-4875-b7e1-ae36cc33c3d9" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/nathanotis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathanotis)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=394136cb-4e75-4ddf-806a-41da223ec840

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
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		394136cb-4e75-4ddf-806a-41da223ec840
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=394136cb-4e75-4ddf-806a-41da223ec840 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3007a9a0-fb8b-4462-a0fb-6c3e3cee5bee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.8GB: boot/grub/menu.lst
  51.8GB: boot/grub/stage2
  51.8GB: boot/initrd.img-2.6.28-11-generic
  51.9GB: boot/vmlinuz-2.6.28-11-generic
  51.8GB: initrd.img
  51.9GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=751a56fb-aa8a-44b4-9bce-ffebccdecbd3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=751a56fb-aa8a-44b4-9bce-ffebccdecbd3

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
uuid		751a56fb-aa8a-44b4-9bce-ffebccdecbd3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=751a56fb-aa8a-44b4-9bce-ffebccdecbd3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		751a56fb-aa8a-44b4-9bce-ffebccdecbd3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=751a56fb-aa8a-44b4-9bce-ffebccdecbd3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		751a56fb-aa8a-44b4-9bce-ffebccdecbd3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=394136cb-4e75-4ddf-806a-41da223ec840 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=751a56fb-aa8a-44b4-9bce-ffebccdecbd3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0915557b-c676-4265-8b68-762e98ccd3cc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  53.4GB: boot/grub/menu.lst
  53.4GB: boot/grub/stage2
  53.4GB: boot/initrd.img-2.6.28-11-generic
  53.5GB: boot/vmlinuz-2.6.28-11-generic
  53.4GB: initrd.img
  53.5GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-05-07
According to the Boot Info Script, your Xubuntu install on sda7 is the one whose menu.lst gets loaded on start up by Grub. If you want to change your menu.lst so that you boot into Ubuntu on sda5 by default rather than Xubuntu on sda7, you'll need to boot into Xubuntu and modify its menu.lst. If you change the "default 0" line in the menu.lst to "default 4", you should then boot into Ubuntu on sda5 by default on start up. Let me know how that goes or if you run into problems. 

John

---

### Post by Nathan Otis on 2009-05-09
> **caljohnsmith said:**
> According to the Boot Info Script, ... If you change the "default 0" line in the menu.lst to "default 4", you should then boot into Ubuntu on sda5 by default on start up. Let me know how that goes or if you run into problems.

John, thanks for the help. Once I really looked at the menu.lst file and saw where the "default 0" option was, it was a really easy change to make. I had to make it default 5 to get Ubuntu rocking by default, but like I said... Easy.

Thanks again. This one is solved!

---

### Post by lswb on 2009-05-09
Just FYI in case you didn't know, xfce and gnome (or other desktop environments) can coexist in the same OS partition, it is not necessary to use a whole separate installation. The login manager will have a way to choose which DE your session will use.

---

### Post by Nathan Otis on 2009-05-09
Very interesting. I wasn't aware. I wanted to try Xubuntu largely because I have read that xfce is a lighter desktop. I'll have to look deeper into how to set up multiple desktop environs.

Thanks!

---

### Post by Nathan Otis on 2009-09-20
Hello, all... I'm bringing this thread up again rather than starting a new one, since all this info applies. I hope that's preferred.

Now that I know I can simply add the Xubuntu-Desktop to Ubuntu, I would like to uninstall Xubuntu from this machine and reclaim that portion of HDD for Ubuntu.

Can this be done without a reinstall of the Ubuntu OS?

Thank you.
n.

---

