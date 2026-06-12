---
title: "Grub Error 15 and boot fails, following reinstallation and partition image flashing!"
date: 2009-04-13
forum: General Help
---

### Post by Pipps on 2009-04-13
I have a major problem and I am currently only able to access Ubuntu from a non-persistent pendrive. I hope someone can help me!

**Background**
I previously ran Ubuntu from on a 3.9GB ext3 partition.
I took a backup of this isntallation using partimage on the sysresccd. The partition image file is approximately 2.4GB in size.
I have used and reinstated this image file many times in the past and it has always worked perfectly.

Today, I reformatted my single local hard-drive and converted it to NTFS, using GParted on the Ubuntu Live USB disc.

I booted Windows XP from CD and installed crappy Windows XP SP3. I know that makes me a wolly, but I need Windows over the next few days to perform specific audio file processing in Steinberg Wavelab.

Once Windows was up and running (as well as can ever be expected) I then booted the Ubuntu Live USB again and installed Ubuntu.
I used GParted within the Ubuntu installation procedure to resize and occupy a 10GB portion of the local hard-drive and to convert this to ext3 as appropriate.
Ubuntu installed, the system restarted, the Grub boot menu presented, with both Ubuntu and Windows XP as available options, and Ubuntu loaded without any problems

I then restarted again and booted the sysresccd and followed the usual tried and test partimage procedure.
I reflashed my 2.4GB Ubuntu image file, as I have successfully done many times in the past when running Ubuntu-only systems.

However, this time, on restarting the system immediately following the partition image reflash, instead of the Grub bootloader cheerfully greeting me, I received the 'Error 15' message. From this point, the system hung, and would not restart.

I am currently only able to access Ubuntu in Live USB mode, and cannot access any of my local partitions or their operating systems.

**Possible reason?**
I am a noob, as you have probably guessed. But I was wondering if this might be a problem with the drive UUIDs? Or am I barking up the wrong tree, here?
I do have a note of the previous sda2 UUID - the one which matches my backed-up partition image.
I also have a note of the UUID from the fresh Ubuntu installtion made when the Grub bootloader was previously working correctly and was displaying the new Windows XP boot option as well.
Would either of these help?

**Please help!**
Can anyone help me and tell me what is wrong please?

---

### Post by Pipps on 2009-04-13
Ok, I have just reinstalled Ubuntu from the Live USB, again.

I have left the previous Windows partition intact.

I have now reorganised my Ubuntu partitions, and my drives are now structured as follows:

sda1 ntfs WinXP 67142MB n/a
sda2 ext3 /boot    98MB primary
sda3 ext3 swap	 1998MB extended
sda4 ext3 /	10783MB primary

In due course, I will post the UUID of my new sda4 '/' partition, which I hope to re-flash to from my old Ubuntu partition image.

I hope this will help. Thank you.

---

### Post by Pipps on 2009-04-13
Yes, it would appear that the UUIDs have changed:

UUID of partition image Ubuntu installation filesystem:
**/dev/sda2: UUID="5ca3cbe9-8f3c-41a7-916d-ed3073e18e15" TYPE="ext3" **

UUID of new Ubuntu installation, which I wish to remove:
**/dev/sda4: UUID="bfe595a9-222d-4350-82ec-d9d49fc087fd" TYPE="ext3"**

I also have a backup of the new fresh Grub bootloader 'menu.lst' file. I have pasted it into the code box below:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,1)
kernel		/last-good-boot/vmlinuz root=/dev/sda4 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

Does any of this information help, in allow me to restore my partition image and allow Grub to boot properly once it has been reinstated?

Is there any way that my Grub bootloader file can be edited so that it will work with my reinstated Ubuntu partition image?

---

### Post by Pipps on 2009-04-13
If I change the UUID for my active Ubuntu installation partition, in the new Grub bootloader file, to match the UUID which I know relates to the partition image which I wish to backup to, would this allow Grub to load at startup and boot my reinstated Ubuntu installation properly?

---

