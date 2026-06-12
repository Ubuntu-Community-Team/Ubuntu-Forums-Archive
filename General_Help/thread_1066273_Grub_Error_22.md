---
title: "Grub Error 22"
date: 2009-02-10
forum: General Help
---

### Post by Tom_T on 2009-02-10
Hi.
I'm Back :)

Different laptop, new problem.

I've just cloned my Acer Aspire One Netboot onto a Virtual PC, so I can have a play without killing my live Netbook.

Cloning went well, but on a reboot of the virtual PC I get Grub Error 22.

The Netbook has Linpus and Ubuntu 8.10..

I've boot the VirtualPC from a 1GB USB key running parted magic.

Here are the results of fdisk -lu:
[IMG]http://oem.adslweb.co.uk/fdisk.jpg[/IMG]

And from sfdisk -d:
[IMG]http://oem.adslweb.co.uk/sfdisk.jpg[/IMG]

Sorry I've posted this as images, but I can't copy and paste between the Virtual PC and my PC !!

Thanks

---

### Post by caljohnsmith on 2009-02-10
Tom_T, it would help to get a better picture of your new setup, so how about booting your Ubuntu Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup. Also, which partition(s) are associated with your Virtual PC? And what are the other partitions on that HDD?

---

### Post by Tom_T on 2009-02-10
Hi
/dev/hda is the usb boot key.

The partitions for the VirtualPC are all on /dev/hdb (64.4GB)

/dev/hdb1 - Linpus Linux Original OS on Netbook
/dev/hdb2 - Ubuntu 8.10 added from LiveUSB
/dev/hdb3 - Linux Swap
/dev/hdb4 - Linux Swap

Not sure which swap belongs to which Linux version !!

results.txt to follow shortly !

Thanks

---

### Post by Tom_T on 2009-02-10
RESULTS.TXT:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc3f3315

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   105,354,269   105,354,207  83 Linux
/dev/sda2         105,354,270   112,085,504     6,731,235  83 Linux
/dev/sda3         112,085,505   118,061,684     5,976,180  82 Linux swap / Solaris
/dev/sda4         118,061,685   120,166,199     2,104,515  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="linpus" UUID="8250323c-6b17-4f6f-8ab9-60e0a96b00aa" TYPE="ext2" 
/dev/sda2: UUID="8db690cf-81fb-4cc9-92d5-df60477c35e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" 
/dev/sda4: TYPE="swap" 
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

========================== sda1/boot/grub/grub.conf: ==========================


default=0
timeout=0
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu

title Linpus Linux RCD
	rootnoverify (hd0,0)
	kernel /boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer
  	initrd /boot/initrd-splash.img


=============================== sda1/etc/fstab: ===============================

/dev/sda1          /                  ext2          defaults,noatime        1 1
none               /dev/pts           devpts        gid=5,mode=620         0 0
none               /dev/shm           tmpfs         defaults               0 0
none               /proc              proc          defaults               0 0
none               /sys               sysfs         defaults               0 0
#none               /tmp               tmpfs         defaults               0 0
/dev/sda2          swap               swap         defaults               0 0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/grub.conf
   2.2GB: boot/grub/stage2
   2.2GB: boot/initrd-splash.img
   2.2GB: boot/initrd-splash-smallnew.img

=========================== sda2/boot/grub/menu.lst: ===========================

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
#color cyan/blue blink-white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/ws_Acer.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8db690cf-81fb-4cc9-92d5-df60477c35e4

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
# defoptions=quiet splash vga=758

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
quiet

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1
quiet

#title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1 (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Linpus Linux RCD (on /dev/sda1)
title		Linpus Linux
root		(hd0,0)
kernel		/boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer 
initrd		/boot/initrd-splash.img
savedefault
boot


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=dfc66e7d-316f-4475-bb4e-c453b9cfabb7 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  54.0GB: boot/grub/menu.lst
  54.0GB: boot/grub/stage2
  54.0GB: boot/initrd.img-2.6.27-7-generic
  54.0GB: boot/initrd.img-2.6.27-9-generic
  54.0GB: boot/initrd.img-2.6.28-rc8-custom-aa1
  54.0GB: boot/initrd.img-2.6.28sickboy-kuki
  54.0GB: boot/vmlinuz-2.6.27-7-generic
  54.0GB: boot/vmlinuz-2.6.27-9-generic
  54.0GB: boot/vmlinuz-2.6.28-rc8-custom-aa1
  54.0GB: boot/vmlinuz-2.6.28sickboy-kuki
  54.0GB: initrd.img
  54.0GB: initrd.img.old
  54.0GB: vmlinuz
  54.0GB: vmlinuz.old

=============================== StdErr Messages: ===============================

sed: can't read sda1/etc/issue: No such file or directory



```

Thanks :)

---

### Post by caljohnsmith on 2009-02-10
OK, so what is your ultimate goal? I'm just wondering why you want to use Virtual PC? You could easily set up a dual boot the way you have your system is configured right now. Also, isn't Virtual PC just for Windows OSes? About your setup, one thing I wanted to mention is that you don't need to have two swap partitions if you are going to dual boot Linpus and Ubuntu; they can share the same swap partition. If you want to dual boot, do you have a preference which distro is in charge of the booting process?

---

### Post by Tom_T on 2009-02-10
Hi
On my NetBook I have dual booting and it works fine.
Long term I would like to add XP to the netbook giving me the choice of
1. Linpus - Fast Boot time etc
2. Ubuntu
3. XP - mainly for the wife.

The idea was to image this to VirtualBox (sorry not virtualpc) and then play with the installation, installing xp knowing if it goes wrong it's not the Netbook that's messed up !!

Once I was happy with add XP to the mix, I would try it on the Netbook !!

I don't mind which OS manages the booting, Currently it's via Ubuntu.

Thanks

---

### Post by caljohnsmith on 2009-02-10
If you eventually want to install XP to that HDD, that's another good reason to delete one of your swap partitions, because currently you have no partitions left to install XP to. Since the Linpus partition currently takes about 50 GB worth of space, are you planning on shrinking it in order to install XP? As long as you plan on installing XP at some point to its own partition, I think if I were you I would just do it now; if we sort out your booting problems now, once you install XP you will have to sort out more booting problems again. I think it would be better to just do it all now. So does installing XP to its own partition now sound like a reasonable plan? If so, how about letting me know what you want to do about making room for XP on your HDD.

---

### Post by Tom_T on 2009-02-10
Installing XP into it's own partition is the plan and shrinking Linpus is how I will free the space on this virtualBox PC.

Thanks

---

### Post by caljohnsmith on 2009-02-10
OK, sounds like a good plan, so to do that you'll need to delete at least one of your swap partitions so you can have a partition for XP. What I would actually recommend is deleting both swap partitions, create a new swap partition at the very end of your drive, and then you can give those extra GB of space to your sda2 Ubuntu partition. Then you could shrink the Linpus sda1 partition and make a new primary partition for XP. Also, once you are done creating the new swap partition, I would recommend doing:
```
sudo mkswap -U dfc66e7d-316f-4475-bb4e-c453b9cfabb7 /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And replace sdaX with the swap partition. Doing the above command will assign the UUID of your Ubuntu's previous swap partition to the new swap partition, so then you don't have to modify any of Ubuntu's system files to use the new swap partition. You will also need to change some of your Linpus system files to use the new swap partition, but we can deal with that after you install XP. Good luck and let me know how it goes.

---

### Post by Tom_T on 2009-02-11
Thanks

Just changing the partitions and creating the new swap.
I'll post details shortly :)

---

### Post by Tom_T on 2009-02-11
Blimey that took a while !!

ubuntu@ubuntu:~$ sudo mkswap -U dfc66e7d-316f-4475-bb4e-c453b9cfabb7 /dev/sda3
Setting up swapspace version 1, size = 2048280 KiB
no label, UUID=dfc66e7d-316f-4475-bb4e-c453b9cfabb7


fdisk -lu
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc3f3315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    42154559    21077248+  83  Linux
/dev/sda2        83778975   121724504    18972765   83  Linux
/dev/sda3       121724505   125821079     2048287+  82  Linux swap / Solaris
/dev/sda4        42154560    83778974    20812207+   b  W95 FAT32

Partition table entries are not in disk order

```

sfdisk -d```

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 42154497, Id=83, bootable
/dev/sda2 : start= 83778975, size= 37945530, Id=83
/dev/sda3 : start=121724505, size=  4096575, Id=82
/dev/sda4 : start= 42154560, size= 41624415, Id= b
```

Gparted View:
[IMG]http://oem.adslweb.co.uk/new_partitions.jpg[/IMG]

I presume that's OK and that I should now boot from my XP CD and install into /dev/sda4

Once I've done that I guess it's sort Grub and the swap for Linpus (is that does via fstab ?)

Any advice before I install XP will be gratefully received ;) 
Thanks

---

### Post by caljohnsmith on 2009-02-11
That looks good, except I would definitely format your sda4 partition to be NTFS rather than FAT32. Once you've done that, fire up the Windows Install CD and point it to the sda4 partition. Let me know how that goes.

---

### Post by Tom_T on 2009-02-12
/dev/sda4 formated as NTFS, XP Pro installed and booting fine.
(I did have the issue of hall.dll not found, but edited the boot.ini and restarted the install)

So how do I reinstate Grub and sort the Linpus swap ??

Once this is complete on my Virtual Box 'Netbook'.. I'll start again and do it on my live netbook !!

Thanks :)

---

### Post by caljohnsmith on 2009-02-12
That's great news, glad that your Windows install went relatively smoothly. So to get Grub back, how about doing the following from the Live CD:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know how far you get when booting Ubuntu. If you can get into Ubuntu, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the end:
```
title Windows XP Pro
root (hd0,3)
chainloader +1
```
Next you'll need to correct your Linpus fstab file:
```
sudo mount /dev/sda1 /mnt && gksudo gedit /mnt/etc/fstab
```
And just change the swap line to use sda3 instead of sda2:
```
/dev/[COLOR="Blue"]sda3[/COLOR]   swap   swap   defaults    0 0
```
Then I think you should be all set, but let me know how it goes or if you run into problems.

---

### Post by Tom_T on 2009-02-12
Thanks again for your help :)

sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

As soon as I enter setup (hd0)
I get: Error 17: Cannot Mount selected partition

Any ideas ??
Thanks

---

### Post by caljohnsmith on 2009-02-12
How about running the Boot Info Script again and posting the results, because that will clarify your new setup without having to run a bunch of individual commands.

---

### Post by Tom_T on 2009-02-12
RESULTS.TXT

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc3f3315

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    42,154,559    42,154,497  83 Linux
/dev/sda2    *     42,154,560    83,778,974    41,624,415   7 HPFS/NTFS
/dev/sda3          83,778,975   121,724,504    37,945,530  83 Linux
/dev/sda4         121,724,505   125,821,079     4,096,575  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="linpus" UUID="8250323c-6b17-4f6f-8ab9-60e0a96b00aa" TYPE="ext2" 
/dev/sda2: UUID="A8505374505347E8" TYPE="ntfs" 
/dev/sda3: LABEL="ubuntu" UUID="8db690cf-81fb-4cc9-92d5-df60477c35e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="dfc66e7d-316f-4475-bb4e-c453b9cfabb7" TYPE="swap" 
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

========================== sda1/boot/grub/grub.conf: ==========================


default=0
timeout=0
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu

title Linpus Linux RCD
	rootnoverify (hd0,0)
	kernel /boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer
  	initrd /boot/initrd-splash.img


=============================== sda1/etc/fstab: ===============================

/dev/sda1          /                  ext2          defaults,noatime        1 1
none               /dev/pts           devpts        gid=5,mode=620         0 0
none               /dev/shm           tmpfs         defaults               0 0
none               /proc              proc          defaults               0 0
none               /sys               sysfs         defaults               0 0
#none               /tmp               tmpfs         defaults               0 0
/dev/sda2          swap               swap         defaults               0 0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/grub.conf
   2.2GB: boot/grub/stage2
   2.2GB: boot/initrd-splash.img
   2.2GB: boot/initrd-splash-smallnew.img

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="0 - Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="1 - Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="3 - Microsoft Windows XP Professional" /fastdetect

=========================== sda3/boot/grub/menu.lst: ===========================

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
#color cyan/blue blink-white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/ws_Acer.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8db690cf-81fb-4cc9-92d5-df60477c35e4

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
# defoptions=quiet splash vga=758

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
quiet

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1
quiet

#title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1 (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Linpus Linux RCD (on /dev/sda1)
title		Linpus Linux
root		(hd0,0)
kernel		/boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer 
initrd		/boot/initrd-splash.img
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=dfc66e7d-316f-4475-bb4e-c453b9cfabb7 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  42.9GB: boot/grub/menu.lst
  43.0GB: boot/grub/stage2
  43.0GB: boot/initrd.img-2.6.27-7-generic
  43.0GB: boot/initrd.img-2.6.27-9-generic
  43.0GB: boot/initrd.img-2.6.28-rc8-custom-aa1
  43.0GB: boot/initrd.img-2.6.28sickboy-kuki
  43.0GB: boot/vmlinuz-2.6.27-7-generic
  43.0GB: boot/vmlinuz-2.6.27-9-generic
  43.0GB: boot/vmlinuz-2.6.28-rc8-custom-aa1
  43.0GB: boot/vmlinuz-2.6.28sickboy-kuki
  43.0GB: initrd.img
  43.0GB: initrd.img.old
  43.0GB: vmlinuz
  43.0GB: vmlinuz.old

=============================== StdErr Messages: ===============================

sed: can't read sda1/etc/issue: No such file or directory


```

Thanks

---

### Post by caljohnsmith on 2009-02-12
OK, I see the issue is your partition numbering changed. How about instead doing:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
And let me know if that works.

---

### Post by Tom_T on 2009-02-12
That worked.. Just rebooting.
Just so I understand.. is hd0,2 /dev/sda3 ??

---

### Post by Tom_T on 2009-02-12
Hmm..

Grub loads and Ubuntu works.
If I try XP I get Error 13: Invalid or unsupported executable format

If I try Linpus it sarts to load and then stops !!

I'll check my editing of menu.lst and /mnt/etc/fstab.

---

### Post by caljohnsmith on 2009-02-12
Since your partition numbering changed, I forgot to let you know what the new Windows Grub entry should be:
```
title Windows XP Pro
root (hd0,1)
chainloader +1

```
And yes, Grub's numbering starts counting from 0 instead of 1, so that:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
...etc.
```

---

### Post by Tom_T on 2009-02-12
Sorted :) XP & Ubuntu now work.

Just need to find out why Linpus won't start.  Any Ideas ?

Thanks again

---

### Post by caljohnsmith on 2009-02-12
So you fixed Linpus' fstab to use the new swap partition? And I don't know if you mentioned it before, but was Linpus booting OK on that computer before you made the partition changes, or has it never booted yet on that computer? You could try the following:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
exit
```
Then pull up your Ubuntu menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add:
```
title Linpus Grub menu
root (hd0,0)
chainloader +1
```
Then let me know if it makes any difference when you boot "Linpus Grub Menu" from Ubuntu.

---

### Post by Tom_T on 2009-02-12
On my netbook Linpus worked fine. This is a cloned virtualBox guest.
I haven't tried it with in the guest as I got the original grub error 22.

Just about to make the changes suggested.

---

### Post by Tom_T on 2009-02-12
Selecting 'Linpus Grub Menu' from the Ubuntu Grub Menu

Starts Linpus and then it stops and sits on the blue loader screen. This is the same as before.
Just wondering if Linpus is tied to the Acer One Hardware.

---

### Post by caljohnsmith on 2009-02-12
It sounds to me like you definitely have a problem with Linpus then and not Grub at this point. I don't know anything about Linpus, so sorry I can't help you with it.

---

### Post by Tom_T on 2009-02-12
**caljohnsmith** Many Thanks for all you help.

I've posted on an Acer One support forum, to see if they know how to sort Linpus.. Hopefully they will advise on Linpus.

Thanks again :)

---

### Post by caljohnsmith on 2009-02-12
You're welcome, and I hope you can sort out your Linpus problem. At least you have Ubuntu and Windows in the meantime. :)

---

### Post by Tom_T on 2009-02-14
I've decided to try this on my live netbook 
(Acer One 1GBb - 160GB Hard Disk)

I've repartitioned, created a new NTFS partition for XP Pro and have installed XP Pro which boots fine.

I think I've updated fstab on Ubuntu & Linpus correctly for the new swap partition.

Currently the netbook is using Microsoft's boot loader and XP boots from that OK, but I can't access Linpus or Ubuntu.

So how do I get grub back ?? It used to be managed by Ubuntu 8.10.

Below is the results.txt from boot_info_script024.sh  

Any ideas ?
Thanks :)

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd91ac89e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   105,354,269   105,354,207  83 Linux
/dev/sda2    *    105,354,270   188,217,539    82,863,270   7 HPFS/NTFS
/dev/sda3         188,217,540   305,556,299   117,338,760   5 Extended
/dev/sda5         188,217,603   305,556,299   117,338,697  83 Linux
/dev/sda4         305,556,300   312,576,704     7,020,405  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060927 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     8,060,926     8,060,864   b W95 FAT32

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="linpus" UUID="8250323c-6b17-4f6f-8ab9-60e0a96b00aa" TYPE="ext2" 
/dev/sda2: UUID="2894F1074FB0A8E3" LABEL="xp" TYPE="ntfs" 
/dev/sda4: UUID="f825797f-053e-4f81-8afe-93b1ae7d6455" TYPE="swap" 
/dev/sda5: LABEL="ubuntu" UUID="8db690cf-81fb-4cc9-92d5-df60477c35e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="4CCB-63DA" TYPE="vfat" 

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
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="0 Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="1 Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="3 Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="4 Microsoft Windows XP Professional" /fastdetect

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
#color cyan/blue blink-white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/ws_Acer.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8db690cf-81fb-4cc9-92d5-df60477c35e4

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
# defoptions=quiet splash vga=758

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
quiet

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1
uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1
quiet

#title		Ubuntu 8.10, kernel 2.6.28-rc8-custom-aa1 (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.28-rc8-custom-aa1 root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.28-rc8-custom-aa1

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8db690cf-81fb-4cc9-92d5-df60477c35e4
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Linpus Linux RCD (on /dev/sda1)
title		Linpus Linux
root		(hd0,0)
kernel		/boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer 
initrd		/boot/initrd-splash.img
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8db690cf-81fb-4cc9-92d5-df60477c35e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=f825797f-053e-4f81-8afe-93b1ae7d6455 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.7GB: boot/grub/menu.lst
 134.7GB: boot/grub/stage2
 134.7GB: boot/initrd.img-2.6.27-7-generic
 134.7GB: boot/initrd.img-2.6.27-9-generic
 134.6GB: boot/initrd.img-2.6.28-rc8-custom-aa1
 134.7GB: boot/initrd.img-2.6.28sickboy-kuki
 134.7GB: boot/vmlinuz-2.6.27-7-generic
 134.7GB: boot/vmlinuz-2.6.27-9-generic
 134.7GB: boot/vmlinuz-2.6.28-rc8-custom-aa1
 134.7GB: boot/vmlinuz-2.6.28sickboy-kuki
 134.7GB: initrd.img
 134.6GB: initrd.img.old
 134.7GB: vmlinuz
 134.7GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-14
To get Grub back, how about doing:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Also, the script was not even able to mount and read your Linpus sda1 partition. I noticed before that the script says the Linpus has a FAT32 Windows XP boot sector despite the fact the partition uses an ext2 file system, but I didn't say anything since the partition mounted OK. Did you by chance run "fixboot" from a Windows CD at some point? I briefly discussed your issue with Meierfra (the author of the Boot Info Script you've been running), and he thought maybe you had run "fixboot" on your Linpus partition by accident; that might explain why the script would read the sda1 boot sector as a FAT32 Windows XP boot sector. So did you ever run "fixboot" at any point?

---

### Post by Tom_T on 2009-02-14
Hi

This is now on my netbook, were before it was a virtualBox PC.

I haven't run fixboot at all on this netbook or the VirtualPC.
I'll try the suggestion for grub and will get back shortly.

Thanks

---

### Post by Tom_T on 2009-02-14
Thanks Grub is back.
Is this the correct entry for Win XP in grub ??

title Windows XP Pro
root (hd0,1)
chainloader +1

---

### Post by Tom_T on 2009-02-14
Linpus won't boot on my netbook.#

It was working before, but not now. The netbook is just sat there flashing the CAPS lock key !!

Any ideas ?

---

### Post by caljohnsmith on 2009-02-14
> **Tom_T said:**
> Thanks Grub is back.
Is this the correct entry for Win XP in grub ??

```
title Windows XP Pro
root (hd0,1)
chainloader +1
```
Yes, that should be the correct entry for Windows. Are you having problems booting Windows? Also, about the problem with mounting and/or booting the Linpus partition, how about doing this while you are in Ubuntu, and please be careful not to make any typos:
```

sudo dd if=/dev/sda1 of=~/Desktop/sda1_boot_sector.bin count=1
sudo dd if=/dev/zero of=/dev/sda1 count=1
sudo e2fsck -fpv /dev/sda1
sudo mount /dev/sda1 /mnt && ls -l /mnt

```
And post the output of all the above commands. The first command will create a really small "sda1_boot_sector.bin" file on your desktop; please save that file in case we need it.

---

### Post by Tom_T on 2009-02-14
I can boot XP & Ubuntu.

Linpus would boot befoew I started this :confused:

Just about to try you suggestions.

---

### Post by Tom_T on 2009-02-14
**sudo dd if=/dev/sda1 of=~/Desktop/sda1_boot_sector.bin count=1**```
1+0 records in
1+0 records out
512 bytes (512B) copied, 0.0396596 s, kB/s
```

**sudo dd if=/dev/zero of=/dev/sda1 count=1**```
1+0 records in
1+0 records out
512 bytes (512B) copied, 0.000504577 s, kB/s
```


**sudo e2fsck -fpv /dev/sda1**```
linpus: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

linpus: Inode bitmap for group 384 is not in group.  (block 2147483647)


linpus: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```


**sudo mount /dev/sda1 /mnt && ls -l /mnt**```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Err what does that mean ? can it be fixed ??

Thanks :)

---

### Post by caljohnsmith on 2009-02-14
OK, try again this time with:
```
sudo e2fsck -fv /dev/sda1
```
And if it asks you to about fixing anything, say yes to all the questions unless using your best judgment you think there is a reason not to, and post back the results.

---

### Post by Tom_T on 2009-02-14
Thanks.

That has finished. I had quite a few delete inode errors, free inodes count wrong for group and inode bitmap differences.

I allowed it to fix them all ! hope that was the right move ;)

End Results :

```
linpus: ***** FILE SYSTEM WAS MODIFIED *****

   81887 inodes used (1.24%)
     130 non-contiguous inodes (0.2%)
         # of inodes with ind/dind/tind blocks: 4585/81/0
 2436603 blocks used (18.50%)
       0 bad blocks
       0 large files

   64547 regular files
    5623 directories
     146 character device files
      52 block device files
       1 fifo
    2279 links
   11506 symbolic links (11464 fast symbolic links)
       3 sockets
```

Do I try and mount linpus now ??

---

### Post by caljohnsmith on 2009-02-14
Yes, try doing the last mount command from post #34 and post the results.

---

### Post by Tom_T on 2009-02-14
**default@default-laptop:~$ sudo mount /dev/sda1 /mnt && ls -l /mnt**```
total 104
drwxr-xr-x  2 root root  4096 2008-08-28 16:23 bin
drwxr-xr-x  3  500  500  4096 2008-10-07 07:31 boot
drwxr-xr-x  2 root root  4096 2008-09-11 12:29 dev
drwxr-xr-x 91 root root  4096 2009-02-14 16:18 etc
-rw-r--r--  1 root root     0 2008-12-30 11:30 halt
drwxr-xr-x  3 root root  4096 2008-06-09 04:31 home
drwxr-xr-x 10 root root  4096 2008-05-08 02:53 initrd
drwxr-xr-x 12 root root  4096 2008-10-10 09:20 lib
drwx------  2 root root 16384 2008-09-11 12:29 lost+found
drwxr-xr-x  2 root root  4096 2009-02-13 09:15 media
drwxr-xr-x  2 root root  4096 2008-03-28 13:26 misc
drwxr-xr-x 18 root root  4096 2008-05-22 04:14 mnt
drwxr-xr-x  2 root root  4096 2008-03-28 13:26 net
drwxr-xr-x  4 root root  4096 2009-01-03 10:26 opt
drwxr-xr-x  2 root root  4096 2008-09-11 12:29 proc
drwxr-xr-x 29 root root  4096 2009-01-11 14:46 root
drwxr-xr-x  2 root root  4096 2008-03-31 14:02 RPM
drwxr-xr-x  2 root root  4096 2009-02-01 13:34 sbin
drwxr-xr-x  6 root root  4096 2008-04-05 17:13 selinux
drwxr-xr-x  2 root root  4096 2007-08-13 15:47 srv
drwxr-xr-x  2 root root  4096 2008-09-11 12:29 sys
drwxr-xr-x  2 root root  4096 2008-09-11 12:29 tmp
drwxr-xr-x 19 root root  4096 2008-08-05 15:53 usr
drwxr-xr-x 19 root root  4096 2008-03-26 20:19 var
```

---

### Post by caljohnsmith on 2009-02-14
Great, Linpus now mounts OK and is accessible, so how about rebooting and see what happens when you try to boot Linpus.

---

### Post by Tom_T on 2009-02-14
Linpus, XP Pro and Ubuntu are working !! :)
Thank you for all your help.

My son has just asked me to do this to his netbook #-o:
Should I ????  Is there an easy way to clone my entire disk and copy it to his ??

---

### Post by caljohnsmith on 2009-02-14
That's great news, glad all your OSes are booting OK now. You could clone your entire HDD to your son's computer I guess, although it seems like Windows will probably give you trouble since it will detect the different computer. You could look at using "clonezilla" for example, or if you want to be a little geeky and do it from the command line, you can do:
```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] of=/dev/[COLOR="Blue"]<destination drive>[/COLOR] statusinterval=10 bs=10M conv=notrunc
```
But you have to be *extremely* careful not to mix up the source/destination drives in the above command, or as you can guess you lose everything on your HDD (you'll get a copy of your son's HDD). Anyway, good luck and let me know how it goes. :)

---

### Post by Tom_T on 2009-02-14
Thanks for all your help.

I've just rebooted and now the netbook won't start !!
No BIOS nothing.  I've removed the battery and will seee how it is in a couple of minutes !

---

### Post by Tom_T on 2009-02-14
Fixed ..
Apparently it's a know issue and a USB BIOS Flash fixed it.
Now running the latest ACER One BIOS.

---

### Post by Tom_T on 2009-02-16
Thanks to the help of caljohnsmith whilst I set my netbook up..

I've just added XP to my son's netbook. Sorted the swap partitions, re added grub and it's all working !!

Only one more to do... my other son is now asking :(

---

