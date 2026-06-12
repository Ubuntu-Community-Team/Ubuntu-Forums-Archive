---
title: "Booting XP and Ubuntu"
date: 2009-05-24
forum: General Help
---

### Post by Smartflight on 2009-05-24
Okay, so XP is installed on a NTFS partition (/dev/sda3 extended to /dev/sda5) and the mount point is set to /windows.

GRUB has detected XP but it doesn't boot it.
It says the the format is not executable !
It doesn't work on sda5, it only is able to give a boot error on sda3.

What do I do ?
I need to make a multi boot of XP and Ubuntu.

---

### Post by Legace on 2009-05-24
Open Terminal, type in **blkid** and post output here.
Also, post a copy of **/boot/grub/menu.lst** (open the file with Text Editor).

---

### Post by Smartflight on 2009-05-24
The output:

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="008f2dc9-64c2-41d0-8fd6-d98566475b09" TYPE="ext4" 
/dev/sda2: UUID="06788DCF788DBE45" LABEL="Data" TYPE="ntfs" 
/dev/sda4: UUID="5839f59c-f0b6-4e62-9694-36c873fe0a9a" TYPE="swap" 
/dev/sda5: UUID="D284734F847334D7" LABEL="XP" TYPE="ntfs"
```

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
# kopt=root=UUID=008f2dc9-64c2-41d0-8fd6-d98566475b09 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=008f2dc9-64c2-41d0-8fd6-d98566475b09

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        008f2dc9-64c2-41d0-8fd6-d98566475b09
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=008f2dc9-64c2-41d0-8fd6-d98566475b09 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        008f2dc9-64c2-41d0-8fd6-d98566475b09
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=008f2dc9-64c2-41d0-8fd6-d98566475b09 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        008f2dc9-64c2-41d0-8fd6-d98566475b09
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Microsoft Windows XP Professional
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader    +1

```

I changed the partition from (hd0,4) to (hd0,3) and (hd0,5) whilst in GRUB.
Neither of them work.

---

### Post by Legace on 2009-05-24
If I remember correct, Windows MUST be on a primary partition for it to boot.. You need to "lie" to windows that it's on a primary partition, so you need to add the map lines.

Try to edit menu.lst so that the windows entry. Open Terminal, type in:
```
sudo gedit /boot/grub/menu.lst
```

Then replace current Windows entry with following:
```
title        Microsoft Windows XP Professional
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader    +1
```

Finally save, and reboot :)

---

### Post by Smartflight on 2009-05-24
I did as you said..
But it gave the same errors..with all - (hd0,3) , (hd0,4) , (hd0,5)

---

### Post by Legace on 2009-05-24
> **Smartflight said:**
> I did as you said..
But it gave the same errors..with all - (hd0,3) , (hd0,4) , (hd0,5)

Hmm.. Is it possible for you to do the following:
- Copy the files from sda2 to sda1
- Format sda5 and sda2
- Copy the files you copied from sda2 (and the files which are now on sda1) to sda5
- Install Windows on sda2
- Reinstall GRUB (as windows will overwrite GRUB with its own bootloader)

---

### Post by Smartflight on 2009-05-24
That is not possible.
I have no space for anything on my HDD.
I'm looking forward to buy an external one, but till then, is there anything else I can do ?

---

### Post by Legace on 2009-05-24
You could always install Windows on top of Ubuntu (sda1) and then install Ubuntu to sda5 :)

---

### Post by Smartflight on 2009-05-24
Ehh..
I'll reinstall Xp soon then..
Not in a mood today..!
School up anyway, extra classes you see, for 10th graders.

Thanks !

---

