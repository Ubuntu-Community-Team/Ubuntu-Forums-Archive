---
title: "Massive crash, please help."
date: 2009-04-26
forum: General Help
---

### Post by Peleus on 2009-04-26
Hi all, 

I need your help. I've had a massive crash occur to my system at the moment. First things first, my setup. 

I have a single partitioned 250gb hard drive. 80gb linux - Ubuntu 8.10, the rest Windows Vista Ultimate. 

I have grub boot loader which had windows Vista, ubuntu 8.10, ubuntu 8.10 recovery, ubuntu 8.09, ubuntu 8.09 recovery, vista longhorn loader (which was my recovery partition). 

I restarted from windows, not having done anything unusual or installing anything new, because I wanted to look at some code in linux. I looked at code while also updating my system through the update manager. A restart was required for the system, so I finished what I was doing and hit restart. When I went back into the grub loader Vista had suddenly disappeared as an option. 

Ok - wierd. I boot back into linux and look at my grub loader file, yep no Vista option on there. I tried manually adding it back in but still nothing, however I wasn't sure what to reference (hdd 0,1)? 

From here I go back into Ubuntu, thinking of other things I can try. At this stage I spend about 30 seconds in Ubuntu, when panel freezes on me. Cannot access any menu's or terminal at all. Ok - still very wierd, I'll reboot and hopefully that fixes the problem. Reboot occurs, I try and go back into Ubuntu. 

Now once I load ubuntu I get multiple errors at the startup screen (I appologise, I know it's annoying and important but I can't remember wording at this time of posting). Essentially I cannot get into it at all. I also tried 8.10 recovery, 8.09, 8.09 recovery same situation. 

Ok, stress time. My data, that's all I really care about at this point. I'm now talking to you on a live CD of ubuntu, up **** creek. I have managed to back up some ubuntu data as I have access to that partition which has been offloaded onto my USB hard drive. I tried accessing Vista OS however it says it cannot be mounted as it's flag is still in use. I have no idea if the Vista information on the hard drive is actually damaged or not. 

1 - Can anyone please tell me how to override the flags on the Vista hard drive, so I can access my data, and recover before doing a full format. 

2 - Anyone have any idea's wtf happened?

3 - Anyone able to tell me what I should correctly reference in the grub boot loader so I can access, or at least try and load, my Vista Partition. At this point I don't care about the linux partition if that's where the problem is, only the Windows (data reasons). 

4 - Several other very wierd things happening, i.e. here in the live CD I have no spellcheck and everything is showing up as wrong, with wierd dictionary options. This sounds stupid but I have no idea if this is because I'm on a live CD, or because something somewhere has been massively corrupted. 

I have no option for hosting bootmenu somewhere, so I appologise I'll have to post the whole thing here. 

--------------------------------------------------------------------------------------------------------------
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
# kopt=root=UUID=2b02a83b-3ea0-4978-86a5-fbeb521a3efe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2b02a83b-3ea0-4978-86a5-fbeb521a3efe

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

savedefault
makeactive


title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		2b02a83b-3ea0-4978-86a5-fbeb521a3efe
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2b02a83b-3ea0-4978-86a5-fbeb521a3efe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		2b02a83b-3ea0-4978-86a5-fbeb521a3efe
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2b02a83b-3ea0-4978-86a5-fbeb521a3efe ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2b02a83b-3ea0-4978-86a5-fbeb521a3efe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b02a83b-3ea0-4978-86a5-fbeb521a3efe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2b02a83b-3ea0-4978-86a5-fbeb521a3efe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b02a83b-3ea0-4978-86a5-fbeb521a3efe ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2b02a83b-3ea0-4978-86a5-fbeb521a3efe
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		
#root		


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


------------------------------------------------------------------------------------------------------------

Please help :)

---

### Post by bingobingo on 2009-04-26
Just did a upgrade last night now I have a brick on my desk. I was able to reboot and went into Gnome then I logged out and logged in to KDE to check it if all is well. Then I went to log out again to get back to Gnome when during logout the screen went to BIO page, that was strange. I did not know what to do from there so I shut down the computer. That was the last of my computer, I can no longer boot up at all now. All I get is one beep, then two beeps, then three beeps and no screen activation what so ever. I now own a brick. There is no way to reset bios like some post have suggested.

---

