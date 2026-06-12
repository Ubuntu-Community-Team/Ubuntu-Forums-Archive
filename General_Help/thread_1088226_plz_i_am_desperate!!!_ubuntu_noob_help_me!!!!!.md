---
title: "plz i am desperate!!! ubuntu noob help me!!!!!"
date: 2009-03-05
forum: General Help
---

### Post by meinvateristnein on 2009-03-05
i started up vista one day and nothing happened ... it said starting up..... and i waited nearly 1 hour before nothing happened..... i have 8.10 and vista dual booted .... i have tryed everything plz help me find a olsution i am desperate for yor help..... ubuntu forums has been good to me before and i hope that it will be again

any help would be great!!!! ASAP!

here is the output of my menu.lst
..........................................................................................................................................................................
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
timeout		100

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
# kopt=root=UUID=68bfe82a-e797-49e2-9b89-c88b98aa5082 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=68bfe82a-e797-49e2-9b89-c88b98aa5082

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

title		Ubuntu 8.10
uuid		68bfe82a-e797-49e2-9b89-c88b98aa5082
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68bfe82a-e797-49e2-9b89-c88b98aa5082 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10,(recovery mode)
uuid		68bfe82a-e797-49e2-9b89-c88b98aa5082
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68bfe82a-e797-49e2-9b89-c88b98aa5082 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		68bfe82a-e797-49e2-9b89-c88b98aa5082
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
rootnoverify		(hd0,0)
savedefault
chainloader	+1
.................................................................................................................................................................................

hereis my output for fdisk -l

............................................................................
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91e191e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080        9729    29318625    5  Extended
/dev/sda5            6080        9240    25390701   83  Linux
/dev/sda6            9241        9729     3927861   82  Linux swap / Solaris

---

### Post by mikewhatever on 2009-03-05
There isn't much to fix unless on this side, unless you get GRUB errors. Something must be wrong with your Vista, and that's for another forum solve.

---

### Post by jwbrase on 2009-03-05
It could be a Grub problem. I got something wrong in Grub last month and ran into the same "Freeze at 'Starting up' message" problem. Unfortunately, meinvateristnein's setup wouldn't cause my problem (which involved Grub not being on the same disk as Windows), and I'm not intimately familiar with Grub, so I can't say what, if anything, is wrong with his menu.lst file.

---

### Post by lykwydchykyn on 2009-03-05
Nothing I can see in menu.lst indicates a configuration problem.   What happened prior to this?  Windows/Ubuntu updates?  

Can you mount up the Windows partition in Ubuntu and see that there are still files there?

---

### Post by Nano_ext3 on 2009-03-05
Can you tell us if you installed vista BEFORE or AFTER ubuntu?  If you installed vista after its more of a trouble then.  If not, then your grub list may be broken.  In my experience, an XP or Vista entry should look as follows (example fyi)

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

The make active is an important part.  As this, as far as I know, makes your XP partition "active" so that the chainloader can load the partition as a bootable partition for the current "session" of XP.   Your partition looks as follows

title Windows Vista
rootnoverify (hd0,0)
savedefault
chainloader +1

I am not so sure about the rootverify and save default, I suggest going with my first example (replace the drive location with your own), which is the same format the grub instructions tell you in the beginning of menu.lst

Alternatively , you may re-install grub, which should auto-load your Vista partition and the correct grub options.  Instructions for that can be found here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


Hopefully this can help you.

Cheers!


-Nano

---

