---
title: "No Grub menu!?"
date: 2009-05-15
forum: General Help
---

### Post by webaake on 2009-05-15
Firstly, I don't do dual boot and Xubuntu 9.04 boots just fine. But, there's no Grub menu and pressing esc doesn't present one either. I've had this problem on this computer since Feisty and also on Hardy, and now Jaunty.

Some background: There's an onboard VGA-chip that I don't use but BIOS is set to boot AGP first.

My menu.lst: ## timeout sec
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
# kopt=root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89

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
# defoptions=video=vesafb vga=0x311

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro video=vesafb vga=0x311  
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I'd really like it to work becasue I'm trying to compile my own kernel and without the option to choose kernel at boot time I could end up between a rock and a hard place.

It's such a hazzle booting from Live CD, mounting filesystem and edit menu.lst if it goes wrong, which it does.

---

### Post by quixote on 2009-05-17
Even though it's supposed to default to the first partition in the list, maybe it would help matters if you made it explicit.  It's worth a try anyway.  This would go at the beginning.```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

Likewise with hiddenmenu.  Maybe actually commenting it out will do something.
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Be nice if it was this simple!

---

### Post by webaake on 2009-05-17
Thanks for the input but it didn't work to comment out hiddenmenu with ## but I vhanged the time out to 30 secs and the boot up really stopped for 30 secs. Which gave me the insight that there's no contact between the computer and the monitor during this period.

If I've understood everything correctly the initial boot starts with the initframs ram-disk image? And if I could activate the framebuffer driver from within that, I'd probably get the grub menu?

I've already activated vesafb in order to have tty's (ctrl+alt+f1) and beeing able to see the boot process line by line. This was not possible on my hardware when starting out with Feisty, then Hardy and now Jaunty.

So, the question now is; how do I activate the vesafb framebuffer driver in initframs at boot, or rather "pre-boot"?

---

### Post by quixote on 2009-05-17
I can't begin to answer that question, but hopefully somebody more knowledgeable will stop by.

---

### Post by JKyleOKC on 2009-05-17
This may be a bit off topic, but I ran into a somewhat similar problem after changing out the monitor on my wife's machine. The new monitor had both VGA and DVI connectors; the old one had been DVI only. The new monitor refused to come on until I cabled BOTH connectors to the video card! It now uses the analog input via the VGA cable through the start of the boot process, then automatically switches to digital via DVI once the BIOS code has done its thing.

That same machine has a Logitech wireless keyboard and mouse package that uses a common receiver via USB. Again, neither of them work until the BIOS has turned control over to the loader and the USB ports have been activated. This means that I cannot access BIOS until I connect a PS/2 keyboard to the box, since the normal keyboard is dead during the early stages of booting.

Some BIOSes have settings to enable USB connections early, to avoid this problem, but this machine does not. You might be the victim of a similarly brain-damaged BIOS...

---

