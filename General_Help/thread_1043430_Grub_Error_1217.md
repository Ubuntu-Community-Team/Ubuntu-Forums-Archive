---
title: "Grub Error 12/17"
date: 2009-01-18
forum: General Help
---

### Post by Captain CutLess on 2009-01-18
Grub is messed up, and I can't boot into any of my operating systems (right now, I'm on an Ubuntu LiveCD).

When I try booting up, I get error 17.  I think I should also point out that I get that error before I even see the menu with all the OSes.

After looking at some old threads, I tried reinstalling grub using the LiveCD that I'm on right now, but that doesn't work and I get error 12:  Invalid device requested.

Outputs to things, if they are necessary:

**fdisk -l**
```

omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf0bbf0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1150     9237343+   7  HPFS/NTFS
/dev/sda2   *        1151        9765    69192796    7  HPFS/NTFS
/dev/sda3            9765       14593    38788101+   5  Extended
/dev/sda5           10678       14426    30113811   83  Linux
/dev/sda6           14427       14593     1341396   82  Linux swap / Solaris

```

**cat /media/disk/boot/grub/menu.lst**
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
# kopt=root=UUID=39649a7a-73c8-4ab7-a257-fca0c0b45d35 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=39649a7a-73c8-4ab7-a257-fca0c0b45d35 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
password --md5 $1$Fh8Sp$Nov7yx2xntd73SgJ22aMZ1
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=39649a7a-73c8-4ab7-a257-fca0c0b45d35 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic
password --md5 $1$Fh8Sp$Nov7yx2xntd73SgJ22aMZ1

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
password --md5 $1$Fh8Sp$Nov7yx2xntd73SgJ22aMZ1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Actual Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1
password --md5 $1$Fh8Sp$Nov7yx2xntd73SgJ22aMZ1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
root		(hd0,0)
savedefault
makeactive
chainloader	+1
password --md5 $1$Fh8Sp$Nov7yx2xntd73SgJ22aMZ1

```

**sudo grub** (and certain commands from it):
```

grub> find /boot/grub/menu.lst
 (hd0,5)

grub> root (hd0,5)
root (hd0,5)

grub> setup (hd0,5)
setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested

```

What bothers me is that (hd0,5) corresponds to my swap partition.  I have no idea why and no idea how to fix it.

---

### Post by caljohnsmith on 2009-01-18
In order to get a clearer picture of your setup related to your Grub problem, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

