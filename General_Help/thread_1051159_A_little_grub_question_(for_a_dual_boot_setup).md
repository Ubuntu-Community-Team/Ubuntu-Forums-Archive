---
title: "A little grub question (for a dual boot setup)"
date: 2009-01-26
forum: General Help
---

### Post by jerome1232 on 2009-01-26
I'm planning on dual booting OpenSuse 11.1 and Ubuntu 8.10, currently have only Ubuntu 8.10.

I would like to have a grub menu that has Ubuntu or OpenSuse, when I select either OS it chainloads (is that correct terminology?) the grub that's managed by the respective OS. This way kernel updates will not throw off anything and I could add additional OS's if desired rather easily using the same approach. How would one go about setting that up? I want this primary grub to *not* be managed by either OS.

This is my current setup. I plan on resizing /dev/sda1 to make room for OpenSuse's boot partition, how would I go about setting grub up the way I want?

```
jeremy@direbane:~$ sudo -i
root@direbane:~:# fdisk -lu
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e5e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      578339      289138+  83  Linux
/dev/sda2          578340   490223474   244822567+   5  Extended
/dev/sda5          578403   490223474   244822536   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc036a4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux
```

```
root@direbane:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/direbane/UbuntuRoot
  VG Name                direbane
  LV UUID                mr2tcN-lyCn-tjZQ-lcLr-JIUn-8WOO-nwoTRB
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                150.00 GB
  Current LE             38400
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/direbane/swap
  VG Name                direbane
  LV UUID                2X12cL-55sG-tAAq-eZEh-Jdou-kJST-R2oK5a
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.00 GB
  Current LE             512
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/direbane/OpenSuseRoot
  VG Name                direbane
  LV UUID                2mHTQ7-h0LL-efaW-3gK8-fUya-RNX6-JJ7olk
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                20.00 GB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:2
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/direbane-UbuntuRoot
/dev/mapper/direbane-UbuntuRoot / ext3 relatime,errors=remount-ro 0 1
# /dev/sda1 (/boot)
UUID=1795e423-3d26-4690-8947-677c49c59ab4 /boot ext3 relatime 0 2
# /dev/mapper/direbane-swap
/dev/mapper/direbane-swap none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Storage disc (/dev/sdb1)
UUID=570bfc7f-b5d6-4b28-a5db-c6afae1c37b3 /media/torrents ext3 defaults,relatime 0 2
```

---

### Post by cariboo on 2009-01-26
WHat you are looking for is the configfile option in grub. Usually the last install is the grub version that is used. From what it looks like you installed OpenSuse last, so edit grub like this:

```
title       Ubuntu
uuid        mr2tcN-lyCn-tjZQ-lcLr-JIUn-8WOO-nwoTRB
configfile  /boot/grub/menu.lst
```

The above assumes your Ubuntu installation is on /dev/direbane/UbuntuRoot

Using the configfile options allows you to update your Ubuntu kernel and use the maintainers version of menu.lst and not have to do any editing.

Jim

---

### Post by jerome1232 on 2009-01-26
I actually haven't installed it just yet, I just created that logical volume for it, I have some resizing of partitions to do yet, waiting on a trasncode job to finish up before I start messing with everything.

I'll give that option a try and see how it works for me. As a side note blkid prints out a diff uuid then what's listed for the lv should I use that instead? Can I just refer to it by device path since it's not going to swap around like /dev/sdxx can?

```
# this is from blkid, it was orginally in the fstab

/dev/mapper/direbane-root: UUID="6cfcd08a-e3c2-4f0f-9c76-647215979949" TYPE="ext3" 
```

---

### Post by jerome1232 on 2009-01-26
> **cariboo907 said:**
> WHat you are looking for is the configfile option in grub. Usually the last install is the grub version that is used. From what it looks like you installed OpenSuse last, so edit grub like this:

```
title       Ubuntu
uuid        mr2tcN-lyCn-tjZQ-lcLr-JIUn-8WOO-nwoTRB
configfile  /boot/grub/menu.lst
```

The above assumes your Ubuntu installation is on /dev/direbane/UbuntuRoot

Using the configfile options allows you to update your Ubuntu kernel and use the maintainers version of menu.lst and not have to do any editing.

Jim

Okay that pretty much worked just needed to make a few adjustments. Still can't get one thing going.

my /boot isn't on my root partition so I had to adjust your entry for that, and for some reason I had to adjust Ubuntu's config as well to specify where ubuntu's /boot was. uuid's didn't seem to work for me either, had to use "root (hd#,#)".

```

title          Ubuntu
root           (hd0,0)
configfile     /grub/menu.lst
```

I need to modify Ubuntu's menu.lst to add the "root (hd0,0)" instead of "uuid 2489u32482098" to the top of all of it's entries as well. Otherwise it can't find /vmlinuz-2.6.27-9-generic.

I changed ubuntu's to this but when I run update-grub it doesn't seem to change anything.

```
## default Grub Root Device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

---

### Post by sir_cheats_a_lot on 2009-01-26
alright.. lets see;   is it all on one hard drive just different partitions or are you using multiple drives?

1. If its only one drive; how many partitions are in use by ubuntu, just the standard 3 made by the partition manager at ubuntu's install or did you customize it(made more)?
2.if its just the standard 3 your grub entry for the new OS install should be root (hd0,4) {i think}, and not (HD1,0)

---

### Post by jerome1232 on 2009-01-26
ooops yeah that was a typo, I meant hd0,0 the problem is when I run update-grub, it doesn't seem to actually update the entries.

--edit-- right now I have 4 "partitions"

/dev/sda1 ext3 Ubuntu's /boot
/dev/sda2 Extended partition
-------- /dev/sda5 LVM2
/dev/sda3 ext2 OpenSuse' /boot

I have 1 volume group called direbane
It has 3 Logical Volumes
UbuntuRoot - ext3 - self-explanatory
OpenSuseRoot - ext3 - self-explanatory
swap - self-explanatory

This is the entire menu.lst right now (for ubuntu)

```
cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$FGRZr$lCoZbRGEMCSieEYnCNlxs/
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
# kopt=root=/dev/mapper/direbane-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-9-generic root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
lock
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-9-generic root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
lock
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
lock
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
lock
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-3-rt root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-3-rt
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
lock
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/vmlinuz-2.6.27-3-rt root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
uuid		1795e423-3d26-4690-8947-677c49c59ab4
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And this is OpenSuse' menu.lst
```
cat /mnt/grub/menu.lst
# Modified by YaST2. Last modification on Mon Jan 26 14:48:40 PST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,2)
    kernel /vmlinuz-2.6.27.7-9-default root=/dev/direbane/OpenSuseRoot resume=/dev/direbane/swap splash=silent showopts vga=0x317
    initrd /initrd-2.6.27.7-9-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,2)
    kernel /vmlinuz-2.6.27.7-9-default root=/dev/direbane/OpenSuseRoot showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /initrd-2.6.27.7-9-default

### this is just a comment I threw in here not actually in my menu.lst
### this entry below is a modified version of what's in Ubuntu's menu.lst
### it won't work without the "root (hd0,0)" so I need to get Ubuntu's
### menu.lst to generate entries like this
title           Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
uuid            1795e423-3d26-4690-8947-677c49c59ab4
kernel          /vmlinuz-2.6.27-9-generic root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792
initrd          /initrd.img-2.6.27-9-generic
quiet

### This entry below works but tells me it can't find
### vmlinuz-2.6.27-9-generic, it get's into ubuntu's grub but
### won't load the OS without ubuntu haveing the root (hd0,0)
### which it's refusing to generate for me.
title		Ubuntu
root            (hd0,0)
uuid		1795e423-3d26-4690-8947-677c49c59ab4
configfile /grub/menu.lst

```

---

### Post by sir_cheats_a_lot on 2009-01-26
very odd.  correct me if im wrong though:  isn't it generally a bad idea to install an OS on Logical partitions rather then primary ones?
  These are the kind of headaches that make me happy i dual boot with two drives instead of one ;)

anyhow... perhaps this is the culprit for your grub not actually updating in ubuntu?:
```
## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true
```

 I have noticed too that grub is more stubborn as of late..it didn't like having windows to look at i guess for when i removed and reinstalled it it came back with the same menu that refused to boot to winXP i had before. just goes to black screen that says loading and hangs.
 Anyway, try setting it to false and see what happens *shrugs*  honestly don't have a better idea... worst that might happen is you'll be stuck in command line to manually edit the it back to true. . .i think.  Might do this myself later as im having issues with my windows install, and will have to reinstall it again to see what happens...either that or it'll be used as a storage drive ;)

---

### Post by jerome1232 on 2009-01-26
[solved]

Thanks for the help!!!

That was promising but it looks like actually what that line is doing is password protecting my old kernels. 

Turns out it was my own stupidity! 

Earlier today I had renamed my logical volume for ubuntu from "root" to "UbuntuRoot", and manually adjusted menu.lst to point to /dev/direbane/UbuntuRoot but didn't change it in the automatic part at the top. So when I ran update-grub it was wanting to change it back to the old name and I told it no, so it just stopped and never asked about changing the root portion, it just now dawned on me why it was doing that lol.

So I fixed all of the automatic entries, ran sudo update-grub, overveiwed the changes it would make and okay'd them all. Now everything works.

Just to show the complete working menu.lst's.

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$FGRZr$lCoZbRGEMCSieEYnCNlxs/
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
# kopt=root=/dev/mapper/direbane-UbuntuRoot ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-9-generic root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
lock
root		(hd0,0)
kernel		/vmlinuz-2.6.27-9-generic root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
lock
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
lock
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
lock
root		(hd0,0)
kernel		/vmlinuz-2.6.27-3-rt root=/dev/mapper/direbane-UbuntuRoot ro splash vga=792 
initrd		/initrd.img-2.6.27-3-rt
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
lock
root		(hd0,0)
kernel		/vmlinuz-2.6.27-3-rt root=/dev/mapper/direbane-UbuntuRoot ro  single
initrd		/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

and then the opensuse menu.lst

```
# Modified by YaST2. Last modification on Mon Jan 26 14:48:40 PST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,2)
    kernel /vmlinuz-2.6.27.7-9-default root=/dev/direbane/OpenSuseRoot resume=/dev/direbane/swap splash=silent showopts vga=0x317
    initrd /initrd-2.6.27.7-9-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,2)
    kernel /vmlinuz-2.6.27.7-9-default root=/dev/direbane/OpenSuseRoot showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /initrd-2.6.27.7-9-default

title		Ubuntu
root 		(hd0,0)
uuid		1795e423-3d26-4690-8947-677c49c59ab4
configfile /grub/menu.lst

```

Ubuntu's is much more friendly to hand edit (comments ftw), I'm glad that's the one I had to do the configuring in.

---

