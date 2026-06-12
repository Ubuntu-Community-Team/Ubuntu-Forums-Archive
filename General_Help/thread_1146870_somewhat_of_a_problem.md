---
title: "somewhat of a problem"
date: 2009-05-03
forum: General Help
---

### Post by Zom-b on 2009-05-03
okay, here's the deal, ubuntu will load up fine ONLY if I stop and load it in recovery mode first, after I hit esc and then pick the recovery mode and then let it go through it's loading screen and hit resume load, it works fine, but otherwise it gets past grub and sits there at a black screen, forever, the led for the hdd activity is lit but no matter how long I wait nothing happens, I was just wondering if there was either a ways I could automate the whole recovery mode thing or if there was somethings I could try to fix make it to where I didn't have to do recovery everytime, thanks in advance.

---

### Post by doas777 on 2009-05-03
> **Zom-b said:**
> okay, here's the deal, ubuntu will load up fine ONLY if I stop and load it in recovery mode first, after I hit esc and then pick the recovery mode and then let it go through it's loading screen and hit resume load, it works fine, but otherwise it gets past grub and sits there at a black screen, forever, the led for the hdd activity is lit but no matter how long I wait nothing happens, I was just wondering if there was either a ways I could automate the whole recovery mode thing or if there was somethings I could try to fix make it to where I didn't have to do recovery everytime, thanks in advance.
if you hold the ctrl button, does the boot move on?

---

### Post by BslBryan on 2009-05-03
Did you use Wubi?

---

### Post by Zom-b on 2009-05-03
@doas777: I will try that right now

@BslBryan: no I am using grub

---

### Post by Zom-b on 2009-05-03
no. holding ctrl doesn't move the boot along at all

---

### Post by geirha on 2009-05-03
At the grub menu, select the regular boot choice, hit **e** to edit it, select the kernel line and hit **e** to edit it. Remove the words "quiet" and "splash" from the end of the line and hit enter. Hit **b** to boot with this modified entry. Any change?

---

### Post by Zom-b on 2009-05-03
> **geirha said:**
> At the grub menu, select the regular boot choice, hit **e** to edit it, select the kernel line and hit **e** to edit it. Remove the words "quiet" and "splash" from the end of the line and hit enter. Hit **b** to boot with this modified entry. Any change?

nope didn't work, and it only had quiet there, when I hit esc to choose recovery mode theres the regular but, and recovery mode, and it looks like it's repeated 3 times. do you think that is affecting it?

---

### Post by geirha on 2009-05-04
Hm. Could you post the content of /boot/grub/menu.lst?

---

### Post by Zom-b on 2009-05-04
> **geirha said:**
> Hm. Could you post the content of /boot/grub/menu.lst?

#menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by geirha on 2009-05-05
There is quiet and splash on the regular entries there. Try editing /boot/grub/menu.lst and remove the quiet and splash from the first entry and reboot.
```
export EDITOR=gedit    # or whichever is your favorite texteditor
sudoedit /boot/grub/menu.lst

```

Remove the quiet and splash from this entry of the latest kernel version (2.6.24-24)
```

title Ubuntu 8.04.2, kernel 2.6.24-24-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro [COLOR="Red"]quiet splash[/COLOR]
initrd /boot/initrd.img-2.6.24-24-generic
quiet

```

---

### Post by Zom-b on 2009-05-05
> **geirha said:**
> There is quiet and splash on the regular entries there. Try editing /boot/grub/menu.lst and remove the quiet and splash from the first entry and reboot.
```
export EDITOR=gedit    # or whichever is your favorite texteditor
sudoedit /boot/grub/menu.lst

```

Remove the quiet and splash from this entry of the latest kernel version (2.6.24-24)
```

title Ubuntu 8.04.2, kernel 2.6.24-24-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro [COLOR="Red"]quiet splash[/COLOR]
initrd /boot/initrd.img-2.6.24-24-generic
quiet

```

AHHH, thanks I saw taht somewhere else, but the code with the highlighted text made it way easier thanks!

---

