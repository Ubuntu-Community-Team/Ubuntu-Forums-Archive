---
title: "Bricked my Grub"
date: 2009-01-30
forum: General Help
---

### Post by JustinAlf on 2009-01-30
Long story short, my Grub is fubar. 

 I have 2 partitions, a 20 and a 60 gig.  The 60 is where all my primary files are.  Somehow, I messed it up.  I did this many times before, downloaded supergrub, and fixed it.  But now, I cannot.  I installed 8.10 on the 20 gig partition, and I can access all my files from the 60 gig.  But no matter how I try and boot into the 60, I cannot.  

Here is what I got

60 Gig is under, (hd 0,1)
20 Gig is under, (hd 0.5)

How can I get the kernal infor, UUID, and everything else needed to get my primary partition bootable from Grub again?

Thanks for any help.

---

### Post by caljohnsmith on 2009-01-30
When you say you can't boot into your 60 GB partition, can you be more specific? Do you get a Grub menu on start up, but choosing the 60 GB partition entry gives a Grub error? Or do you get a Grub error before seeing the Grub menu? I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD if necessary), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by JustinAlf on 2009-01-30
Well, I have a new grub menu now that I installed on the 20.  But, when I used supergrub to go into the Grub menu, I would select that partiion and see my grub menu.  I would then try to boot into it, and it would give me a grub error 15, file not found.

---

### Post by JustinAlf on 2009-01-30
Here is what I got:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 8634431 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,194,174   117,194,112  83 Linux
/dev/sda2         117,194,175   154,304,324    37,110,150   5 Extended
/dev/sda5         117,194,238   154,304,324    37,110,087  83 Linux
/dev/sda3         154,304,325   156,296,384     1,992,060  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ef61213f-0e9e-4aeb-9d3a-6f8390255ed4" TYPE="ext3" 
/dev/sda3: UUID="c0059c68-d96e-4cdd-b308-f1d324628605" TYPE="swap" 
/dev/sda5: UUID="0a15120a-bbd4-4eef-933e-c0ea9a130baa" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

=========================== sda1/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Thu Jan 29 19:21:54 CST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,0)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1
    root (hd0,0)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part1 resume=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part3 splash=silent showopts vga=0x361
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1
    root (hd0,0)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x361
    initrd /boot/initrd
=============================== sda1/etc/fstab: ===============================

/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part3 swap                 swap       defaults              0 0
UUID=ef61213f-0e9e-4aeb-9d3a-6f8390255ed4 /                    ext3       relatime,errors=remount-ro 1 1
/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part2 /home                ext3       acl,user_xattr        1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda1: Location  of files loaded by Grub: ===================


   4.3GB: boot/grub/menu.lst
   4.4GB: boot/grub/stage2
   4.3GB: boot/initrd.img-2.6.27-10-generic
   4.3GB: boot/initrd.img-2.6.27-11-generic
   4.4GB: boot/initrd.img-2.6.27-7-generic
   4.3GB: boot/initrd.img-2.6.27-8-generic
   4.4GB: boot/vmlinuz
   4.3GB: boot/vmlinuz-2.6.27-10-generic
   4.3GB: boot/vmlinuz-2.6.27-11-generic
   4.4GB: boot/vmlinuz-2.6.27.7-9-default
   4.4GB: boot/vmlinuz-2.6.27-7-generic
   4.4GB: boot/vmlinuz-2.6.27-8-generic
   4.3GB: initrd.img
   4.3GB: initrd.img.old
   4.3GB: vmlinuz
   4.3GB: vmlinuz.old

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
# kopt=root=UUID=0a15120a-bbd4-4eef-933e-c0ea9a130baa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a15120a-bbd4-4eef-933e-c0ea9a130baa

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
uuid		0a15120a-bbd4-4eef-933e-c0ea9a130baa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a15120a-bbd4-4eef-933e-c0ea9a130baa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0a15120a-bbd4-4eef-933e-c0ea9a130baa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a15120a-bbd4-4eef-933e-c0ea9a130baa ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0a15120a-bbd4-4eef-933e-c0ea9a130baa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		openSUSE 11.1 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part1 resume=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part3 splash=silent showopts vga=0x361 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Failsafe -- openSUSE 11.1 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/disk/by-id/ata-TOSHIBA_MK8046GSX_28KDTQNQT-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x361 
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0a15120a-bbd4-4eef-933e-c0ea9a130baa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=c0059c68-d96e-4cdd-b308-f1d324628605 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


  69.7GB: boot/grub/menu.lst
  69.6GB: boot/grub/stage2
  69.4GB: boot/initrd.img-2.6.27-7-generic
  69.2GB: boot/vmlinuz-2.6.27-7-generic
  69.4GB: initrd.img
  69.2GB: vmlinuz

---

### Post by caljohnsmith on 2009-01-30
While you are in your sda5 Ubuntu install, how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
Delete the OpenSUSE entries at the end of the menu.lst, and replace them with:
```
title OpenSUSE Grub Menu
root (hd0,0)
chainloader +1
```
Reboot, select "OpenSUSE Grub Menu" from your Grub menu, and let me know exactly what happens.

---

### Post by timcredible on 2009-01-30
[super grub disk]("http://supergrubdisk.org") will re-do grub if you need.

---

### Post by JustinAlf on 2009-01-30
It entered me into another grub menu, clicked enter, and then the error 15 happened.

I'm thinking this has something to do when I tried to install  openSUSE on the 20 G.  It compleatly re-routed my grub.  Is there a way I can just manually type in the UUID in grub to get my sda1 back working?  BEcuase I can access and use all the files on sda1, but must boot the sda5.  I fell we are close to fixing this, just need a little more help.

---

### Post by caljohnsmith on 2009-01-30
OK, how about trying this:
```
sudo mount /dev/sda1 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And change your OpenSUSE entries as follows:
```
title openSUSE 11.1
root (hd0,0)
kernel /boot/vmlinuz [COLOR="Blue"]root=UUID=ef61213f-0e9e-4aeb-9d3a-6f8390255ed4 resume=UUID=c0059c68-d96e-4cdd-b308-f1d324628605[/COLOR] splash=silent showopts vga=0x361
initrd /boot/initrd

title Failsafe -- openSUSE 11.1
root (hd0,0)
kernel /boot/vmlinuz [COLOR="Blue"]root=UUID=ef61213f-0e9e-4aeb-9d3a-6f8390255ed4[/COLOR] showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x361
initrd /boot/initrd
```
Reboot, try OpenSUSE again from your Grub menu, and let me know if you still get the Grub error 15.

---

### Post by JustinAlf on 2009-02-11
Again, Error 15 file not found.  But I can still access every single file off of that partition.

---

### Post by caljohnsmith on 2009-02-11
OK, how about following the directions in post #8 to pull up your OpenSUSE menu.lst, and then change the first entry to:
```
title openSUSE 11.1
root (hd0,0)
kernel [COLOR="Blue"]/vmlinuz[/COLOR] root=UUID=ef61213f-0e9e-4aeb-9d3a-6f8390255ed4 resume=UUID=c0059c68-d96e-4cdd-b308-f1d324628605 splash=silent showopts vga=0x361
initrd [COLOR="Blue"]/initrd.img[/COLOR]
```
Also add another entry after that:
```
title openSUSE 11.1 2.6.27-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=ef61213f-0e9e-4aeb-9d3a-6f8390255ed4 resume=UUID=c0059c68-d96e-4cdd-b308-f1d324628605 splash=silent showopts vga=0x361
initrd /boot/initrd.img-2.6.27-11-generic
```
Then reboot, and let me know what happens when you boot both of the OpenSUSE entries from above.

---

