---
title: "the composite extension is not available"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by knc1983 on 2008-01-13
I recently installed ubuntu and i'm new to linux overall so i don't know much, i'm trying to get desktop effects working.

I have installed advanced desktop effects settings, but everytime i try to enable them i get the error the "composite extension is not available"

i'm using ati x850 XT graphic card, i have enabled restricted drivers manager, and ATI binary X.Org driver.

Thats all i know, i tried searching some had posted there xorg.conf so i will do the same, and i only know how to get xorg from these forums, so if you need more info you will have to tell me how to retrieve it, 

thanks :)

```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
        Identifier      "DELL E193FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)"
        Monitor         "DELL E193FP"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier        "Default Layout"
        Screen                "Default Screen"
        InputDevice        "Generic Keyboard"
        InputDevice        "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice        "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


```

---

### Post by dracker on 2008-01-13
You have to put this on a console:

```

sudo aptitude install xserver-xgl

```

Introduce your password and wait a bit until it installs, then reboot and try again.

---

### Post by knc1983 on 2008-01-13
> **dracker said:**
> You have to put this on a console:

```

sudo aptitude install xserver-xgl

```

Introduce your password and wait a bit until it installs, then reboot and try again.
, i did this now but now i have 2 problems, it now says desktop effects could not be enabled, and i get real slowness moving around the screen.

---

### Post by knc1983 on 2008-01-13
I decided to install ubuntu again, without installing any updates, now the "wobble effect" is working and before it didnt so maybe compiz will work now, i'm installing it now without the other upgrades.

---

### Post by Forlong on 2008-01-13
Remove Xgl again:
```
sudo aptitude remove xserver-xgl
```

Then go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and make sure the proprietary driver is _not_ enabled.

Then do this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Finally reboot and try again.
If it still doesn't work, post the output of ```
compiz
``` in a terminal as well as your xorg.conf again.


edit: Oh, OK.

---

### Post by knc1983 on 2008-01-13
I installed ubuntu again, and before i updated ubuntu i turned on the effects then ran the update and everything is working, but now i have 2 ubuntu's installed, how do i go about deleting the other installation of ubuntu.

---

### Post by Forlong on 2008-01-14
> **knc1983 said:**
> I installed ubuntu again, and before i updated ubuntu i turned on the effects then ran the update and everything is working, but now i have 2 ubuntu's installed, how do i go about deleting the other installation of ubuntu.
How did you install the first and how the second one?
Which "mode" did you chose in the installation process when asked for a way of partitioning your harddrive?

---

### Post by knc1983 on 2008-01-14
> **Forlong said:**
> How did you install the first and how the second one?
Which "mode" did you chose in the installation process when asked for a way of partitioning your harddrive?

I choose the first one, for free space and when i boot up there is 2 ubuntu's listed, the top one is the new installation that has everything working good and the second one has the graphic problem that i want to delete.

---

### Post by Forlong on 2008-01-14
OK... let's have a look at **/etc/fstab**

---

### Post by knc1983 on 2008-01-14
Hopefully this is correct.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=98069fd3-3520-4430-b85a-54508461fccd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=7eb358b6-68ca-4531-ad0e-a15656a6279a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


```

---

### Post by Forlong on 2008-01-14
OK, please post your **/boot/grub/menu.lst** as well.

btw: did you try booting in that other install of Ubuntu?

---

### Post by knc1983 on 2008-01-14
-

---

### Post by knc1983 on 2008-01-14
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
# kopt=root=UUID=98069fd3-3520-4430-b85a-54508461fccd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98069fd3-3520-4430-b85a-54508461fccd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98069fd3-3520-4430-b85a-54508461fccd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=32a6df3a-a65c-4010-a39f-9c50731f18c0 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=32a6df3a-a65c-4010-a39f-9c50731f18c0 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Forlong on 2008-01-14
OK, now another output please:
```
ls /dev | grep sda
```

It looks like there is no other Ubuntu install on your harddrive after all. But let's try to make sure.

---

### Post by knc1983 on 2008-01-14
> **Forlong said:**
> OK, now another output please:
```
ls /dev | grep sda
```

It looks like there is no other Ubuntu install on your harddrive after all. But let's try to make sure.

```

ls /dev | grep sda
sda
sda1
sda2
sda3
sda4
sda5
sda6
sda7
sda8
sda9



```

Thanks for the help. i think you are correct.

i have 4 partitions, 2 dvd/rw then there is 12.2GB ubuntu & filesystem.

that equals 8 so there is anther partition but that could be portable usb device?

---

### Post by Forlong on 2008-01-14
Oh, OK. Why aren't those in the fstab?

Let's see what kind of partitions those are:
```
sudo fdisk -l
```

(I'm going to bed now, so I'll answer you tomorrow)

---

### Post by knc1983 on 2008-01-14
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bd8bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806    7  HPFS/NTFS
/dev/sda2            7814       19452    93490267+   f  W95 Ext'd (LBA)
/dev/sda3            4796        6391    12819870   83  Linux
/dev/sda4            6392        7813    11422215   83  Linux
/dev/sda5            8022       16230    65938761    7  HPFS/NTFS
/dev/sda6           16231       17238     8096728+   7  HPFS/NTFS
/dev/sda7           17239       19452    17783923+   7  HPFS/NTFS
/dev/sda8            7883        8021     1116454+  82  Linux swap / Solaris
/dev/sda9            7814        7882      554179+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Forlong on 2008-01-15
Alright, now here's the deal:

[LIST][*]/dev/sda1 &#8592; that's your Windows partition
[*]/dev/sda2 &#8592; that's an extended partition (meaning the followindg partitions are "in" there)
[*]/dev/sda3 &#8592; supposedly that's the old Ubuntu install 
[*]/dev/sda4 &#8592; here is the Ubuntu install you are using *right now*
[*]/dev/sda5 &#8592; NTFS (partition for Windows)
[*]/dev/sda6 &#8592; NTFS (dto.)
[*]/dev/sda7 &#8592; NTFS (dto.)
[*]/dev/sda8 &#8592; Swap file
[*]/dev/sda9 &#8592; Swap file[/LIST]

So all you need to to in order to get rid of the old Ubuntu install is formatting **sda3**

Do you know how to do that? If not, better ask, because otherwise you could mess up the allocation table.

---

### Post by knc1983 on 2008-01-18
> **Forlong said:**
> Alright, now here's the deal:

[LIST][*]/dev/sda1 &#8592; that's your Windows partition
[*]/dev/sda2 &#8592; that's an extended partition (meaning the followindg partitions are "in" there)
[*]/dev/sda3 &#8592; supposedly that's the old Ubuntu install 
[*]/dev/sda4 &#8592; here is the Ubuntu install you are using *right now*
[*]/dev/sda5 &#8592; NTFS (partition for Windows)
[*]/dev/sda6 &#8592; NTFS (dto.)
[*]/dev/sda7 &#8592; NTFS (dto.)
[*]/dev/sda8 &#8592; Swap file
[*]/dev/sda9 &#8592; Swap file[/LIST]

So all you need to to in order to get rid of the old Ubuntu install is formatting **sda3**

Do you know how to do that? If not, better ask, because otherwise you could mess up the allocation table.

Looks like that happen, i thought i could just delete the ones myself but i was wrong, so i had to install ubuntu again.

This time it shows 1 ubuntu and my other partions, so everything is working fine again, thanks for the help Forlong, i also went to your site and it helped me out a lot with compiz so thanks again.

---

