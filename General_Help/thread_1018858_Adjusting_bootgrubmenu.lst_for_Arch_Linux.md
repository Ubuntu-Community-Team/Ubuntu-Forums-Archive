---
title: "Adjusting /boot/grub/menu.lst for Arch Linux"
date: 2008-12-22
forum: General Help
---

### Post by RATM_Owns on 2008-12-22
I just installed Arch Linux. Didn't want to overwrite Ubuntu's menu.lst so I didn't install the bootloader.

So I'm just going to add it to my Ubuntu menu.lst
Assuming that my Arch's / is on /dev/sda3, would this be right:
EDIT: And there are some spaces around in Arch's entries. Do I have to edit them out?
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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,1)/boot/grub/blu.xpm.gz

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
# kopt=root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6

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
# defoptions=quiet splash vga=769

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

title        Ubuntu 8.10, kernel 2.6.27.10-grsec
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27.10-grsec

title        Ubuntu 8.10, kernel 2.6.27.10-grsec (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27.10-grsec

title        Arch Linux
root        (hd0,2)
kernel        /boot/vmlinux26 root=/dev/sda3 ro
initrd        /boot/kernel26.img

title          Arch Linux Fallback
root           (hd0,2)
kernel        /boot/vmlinuz26 root=/dev/sda3 ro
initrd        /boot/kernel26-fallback.img

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-10-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        memtest86+
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```And since I already have a separate /home partition, could I add the same thing to Arch's /etc/fstab as I did Ubuntu's /etc/fstab in the PsychoCat's tutorial?

---

### Post by Herman on 2008-12-24
> I just installed Arch Linux. Didn't want to overwrite Ubuntu's menu.lst so I didn't install the bootloader.
So I'm just going to add it to my Ubuntu menu.lst
Assuming that my Arch's / is on /dev/sda3, would this be right:
EEK! 
You have pasted your arch entries into the middle of your debian automagic (Ubuntu) boot entries!
They'll be deleted next time you receive a kernel update if you leave them there.
 
Ubuntu is based on the Debian distribution of Linux, and we have a really neat script called 'update-grub, which runs automatically whenever we have a new kernel installed during an update from the internet. The update-grub script makes us a new menu.lst file and automatically adds the new boot entries to it for the new kernel.
It saves us having to do all that work by hand every time.
However, if we mustn't put foreign boot entries inside the designated area, (not if we care about them anyway), because update-grub won't know about them, and they'll be accidentally deleted.

You should put them either above the line that says '### BEGIN AUTOMAGIC KERNELS LIST', (above around half way up the file), or else below the line that says, '### END DEBIAN AUTOMAGIC KERNELS LIST' , which should be at the bottom of the file.
```
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27.10-grsec
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27.10-grsec

title        Ubuntu 8.10, kernel 2.6.27.10-grsec (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27.10-grsec

[COLOR=Red][B]title        Arch Linux
root        (hd0,2)
kernel        /boot/vmlinux26 root=/dev/sda3 ro
initrd        /boot/kernel26.img

title          Arch Linux Fallback
root           (hd0,2)
kernel        /boot/vmlinuz26 root=/dev/sda3 ro
initrd        /boot/kernel26-fallback.img[/B][/COLOR]

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-10-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        memtest86+
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
``````
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27.10-grsec
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.27.10-grsec

title        Ubuntu 8.10, kernel 2.6.27.10-grsec (recovery mode)
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/vmlinuz-2.6.27.10-grsec root=UUID=56d199b6-d48d-431e-83ed-ab8f7d1dc2a6 ro  single
initrd        /boot/initrd.img-2.6.27.10-grsec


title        memtest86+
uuid        56d199b6-d48d-431e-83ed-ab8f7d1dc2a6
kernel        /boot/memtest86+.bin

**### END DEBIAN AUTOMAGIC KERNELS LIST**

[B][COLOR=Sienna]title        Arch Linux
root        (hd0,2)
kernel        /boot/vmlinux26 root=/dev/sda3 ro
initrd        /boot/kernel26.img

title          Arch Linux Fallback
root           (hd0,2)
kernel        /boot/vmlinuz26 root=/dev/sda3 ro
initrd        /boot/kernel26-fallback.img[/COLOR][/B]  
```I also deleted all of those extra Ubuntu boot entries for old kernels, but you don't have to, you can keep those entries or delete them, it's up to you.

---

### Post by Herman on 2008-12-24
> EDIT: And there are some spaces around in Arch's entries. Do I have to edit them out? :) No, that should be okay.
> And since I already have a separate /home partition, could I add the same thing to Arch's /etc/fstab as I did Ubuntu's /etc/fstab in the PsychoCat's tutorial? I'm not sure what you mean, can you provide a link, (I know about aysiu's excellent website but I'm not sure exactly what part of it you're referring to)?
Do you mean you want to see if both distros can share the same /home?
Probably they can, but I'm not sure. :)

Regards, Herman :)

---

