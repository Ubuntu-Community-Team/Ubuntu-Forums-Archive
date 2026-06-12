---
title: "GRUB Help"
date: 2009-05-26
forum: General Help
---

### Post by dyno0919 on 2009-05-26
Hi all. I'm kind of new to this whole Linux thing and I'm having some troubles.  I installed Ubuntu to a partition and Ubuntu works great. But when I try to dual boot in to Windows 7, it says error 29: Unable to write to disk, or something of the sort.  I thought I'd try to reinstall GRUB and now i get an error when I  type the make command. 
"gcc -I. -I./. -I. -Iinclude -I./include -Wall -W -DGRUB_LIBDIR=\"/usr/local/lib/grub/i386-pc\" -g -O2 -DGRUB_UTIL=1  -MD -c -o grub_emu-grub_script_tab.o grub_script.tab.c
./normal/parser.y: In function ‘grub_script_yyparse’:
./normal/parser.y:59: error: expected ‘;’ before ‘}’ token
make: *** [grub_emu-grub_script_tab.o] Error 1" is what it says.  If anyone could help with either problem, it would be much appreciated.

---

### Post by dpsleep on 2009-05-26
first, you really shouldent try to build from source unless you know what you are doing, very easy to break a system this way. could you post your /boot/grub/menu.lst.

---

### Post by dyno0919 on 2009-05-26
Thanks for the quick reply, here's my menu.lst:

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
# kopt=root=UUID=89d28660-37dd-4769-8c73-06ff5194f5e1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=89d28660-37dd-4769-8c73-06ff5194f5e1

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
uuid        89d28660-37dd-4769-8c73-06ff5194f5e1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=89d28660-37dd-4769-8c73-06ff5194f5e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        89d28660-37dd-4769-8c73-06ff5194f5e1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=89d28660-37dd-4769-8c73-06ff5194f5e1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        89d28660-37dd-4769-8c73-06ff5194f5e1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

---

### Post by dpsleep on 2009-05-26
so do you have windows 7 and vista installed?

so it looks like most likely the boot flag is not set on that partition

try sudo cfdisk

goto the entry that says ntfs with no boot set in the flags

if it says boot on the same line as ntfs, thats not the problem, otherwise hit enter and boot should appear

use the right arrow and goto write, hit enter then type yes

then quit

---

### Post by dyno0919 on 2009-05-26
Yeah but I can't use it or windows 7 because i get that error 29

---

### Post by dpsleep on 2009-05-26
read my edit...

---

### Post by dyno0919 on 2009-05-26
This is probably a supernoob question, but you were right and it says that there is no boot. When i go to write it says it may destroy data. Is everything going to be ok or should I back stuff up >.<

---

### Post by dyno0919 on 2009-05-26
Alright I went ahead with it, restarted my computer, and it still has this error 29.

---

### Post by dpsleep on 2009-05-26
ok, try this. reboot. when it gives you the error press e to edit, goto the line that says savedefault press d for delete then b for boot

---

