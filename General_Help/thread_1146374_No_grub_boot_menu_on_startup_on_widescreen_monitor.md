---
title: "No grub boot menu on startup on widescreen monitor"
date: 2009-05-02
forum: General Help
---

### Post by Rocko Bonaparte on 2009-05-02
I have a widescreen monitor that runs up to 1920x1200.  Ever since I first used this monitor on an Ubuntu 8.10 setup, I have only seen the grub menu a handful of times.  It was plain text when it came up.  I have since moved to 9.04, but the problem persists.  It isn't the end of the world so I took awhile to fix it.  However, now I'm adding custom options of booting into bash and building my own kernel, so I have a good reason to be able to see what I'm selecting.

Note that if I move the arrow keys blindly at the black screen, I can select the option on the list I want if I know where it roughly is.  Generally, on the occasion I have to boot Vista, I can just hit the down arrow a fistful of times and reach it.

I tried to install splash images to get a graphical boot menu, but that didn't help.  Here's my menu.list
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=73465ac7-1523-4a03-8473-992f002bfdde ro

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


splashimage=(hd0,3)/boot/grub/splash.xpm.gz

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=73465ac7-1523-4a03-8473-992f002bfdde ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=73465ac7-1523-4a03-8473-992f002bfdde ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=73465ac7-1523-4a03-8473-992f002bfdde ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=73465ac7-1523-4a03-8473-992f002bfdde ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```Is there anything I should add to my menu.lst to get something?  I'm fine with a plain text menu if needs be.  When I upgrade the kernel through the software updates, it'll put the new one at the head of the list, which ruins my blind-arrow-key-pressing regime.  Any help is appreciated.

---

### Post by codeseer on 2009-05-02
```

splashimage=(hd0,3)/boot/grub/splash.xpm.gz

```

This exists right?

Do you have any other screens before grub normally comes up? Like a splash screen that you might be able to disable in the BIOS.

---

### Post by Rocko Bonaparte on 2009-05-03
Yes it's there.  I added that while pondering if explicitly adding a splash screen would give me something.  It's a symlink to /boot/grub/splashimages/bike_gua.xpm.gz, and hd(0,3) points to my Linux partition.

I don't get any splash screens before I boot, other than the BIOS initialization screens.  That is the memory check screen which shows the logo in the corner, followed by the hard disk controller screen.  I don't have anything coming up with some kind of video card or company logo at any point in the boot process, other than when ubuntu starts booting.

Just to emphasize that, I do get the Ubuntu loading progress bar screen while it loads, and if I'm booting in a rescue mode I do get text.

---

### Post by codeseer on 2009-05-03
> **Rocko Bonaparte said:**
> Yes it's there.  I added that while pondering if explicitly adding a splash screen would give me something.  It's a symlink to /boot/grub/splashimages/bike_gua.xpm.gz, and hd(0,3) points to my Linux partition.

I don't get any splash screens before I boot, other than the BIOS initialization screens.  That is the memory check screen which shows the logo in the corner, followed by the hard disk controller screen.  I don't have anything coming up with some kind of video card or company logo at any point in the boot process, other than when ubuntu starts booting.

Just to emphasize that, I do get the Ubuntu loading progress bar screen while it loads, and if I'm booting in a rescue mode I do get text.

The way I understand it is the video configuration 'after' selecting a grub entry is entirely different than prior to the selection. As far as I know, the entire video configuration is automatically controlled by the BIOS prior to grub selection. If you have a monitor that does the auto-adjusting stuff, that can cause it. Perhaps try to turn that off if you have it and can; that's why I asked if you were getting any other boot screens, because those boot screens will kick that auto-adjust on monitors in sometimes. Then it's stuck like that until after the grub selection. I'd do a sweep of the BIOS settings to make sure there aren't any screens I could disable, just to be sure.

---

