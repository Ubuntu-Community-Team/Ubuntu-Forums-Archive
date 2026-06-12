---
title: "Dual-Boot (Cannot start vista)"
date: 2009-01-29
forum: General Help
---

### Post by CanOSpam on 2009-01-29
Hi, I just installed ubuntu desktop 8.10 along side my vista home premium and everything went great! except now I can't figure out how to start vista... Any help would be appreciated!

---

### Post by marshall.robert on 2009-01-29
Just before Ubuntu boots you should see a menu. Do you?

---

### Post by CanOSpam on 2009-01-29
I don't. Is that bad?
Also, Thanks for the speedy response time.

---

### Post by marshall.robert on 2009-01-29
Hopefully not, it just means that Ubuntu hasnt found your Vista partition, or is hiding the menu. You can press esc when prompted too to see a menu. I would do that and tell us what you get.

I would love to help you more but unfortunately I have to go and sleep now.

Best of luck.

---

### Post by CanOSpam on 2009-01-29
Ok, I've tried that now. When my computer first starts up it says I can press esc for "boot menu". I pressed it and it doesn't do anything.

---

### Post by bumanie on 2009-01-29
From ubuntu can you go to Applications --> Accessories --> Terminal. In terminal type  > sudo fdisk -luThen put in your password when asked (there is no visual output indicating that you are typing your password, however this is normal), just hit enter at the end of your password and copy the output to the forum.

---

### Post by CanOSpam on 2009-01-29
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c9164c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   409602047   204800000    7  HPFS/NTFS
/dev/sda2       409602048   690333415   140365684    7  HPFS/NTFS
/dev/sda3       817272832   976772831    79750000    7  HPFS/NTFS
/dev/sda4       690345180   817258679    63456750    5  Extended
/dev/sda5       690345243   812005424    60830091   83  Linux
/dev/sda6       812005488   817258679     2626596   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by bumanie on 2009-01-29
Well it looks as though vista is still there and intact. Can you go to terminal again and post the output of>  cat /boot/grub/menu.lst

---

### Post by CanOSpam on 2009-01-29
fdisk: invalid option -- 'c'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

I Knew that vista is there. If I look in to my windows partitions though ubuntu I can see everything intact.

---

### Post by bumanie on 2009-01-29
Can you please post the output of > cat /boot/grub/menu.lst It is likely that vista has not been added correctly, once the list is modified correctly, vista and ubuntu should dual boot.

---

### Post by CanOSpam on 2009-01-29
Well, How can I do that?

---

### Post by bumanie on 2009-01-29
You do it via terminal as instructed, just like you did with sudo fdsik -lu, just changing the command. I gathered you are operating from within an ubuntu installation, if not, that command will not work from a ubuntu live cd, but will work from an installation. Are you on a live cd or an installed ubuntu?

---

### Post by CanOSpam on 2009-01-29
Installed. And I posted the results of that command above already.



EDIT:Ok I redid the command and got the following:

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
# kopt=root=UUID=9f118571-5dd2-47a8-9b23-781d451a61e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f118571-5dd2-47a8-9b23-781d451a61e2

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
uuid		9f118571-5dd2-47a8-9b23-781d451a61e2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f118571-5dd2-47a8-9b23-781d451a61e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9f118571-5dd2-47a8-9b23-781d451a61e2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f118571-5dd2-47a8-9b23-781d451a61e2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9f118571-5dd2-47a8-9b23-781d451a61e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f118571-5dd2-47a8-9b23-781d451a61e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9f118571-5dd2-47a8-9b23-781d451a61e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f118571-5dd2-47a8-9b23-781d451a61e2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9f118571-5dd2-47a8-9b23-781d451a61e2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bumanie on 2009-01-29
Can you try the command again, the output was not anything like it should have been - just try once more to check you didn't make a input error or something, if the same result is produced, I think it would be best to do a fresh install of ubuntu over the present one as an output like that would indicate that grub did not install correctly.

---

### Post by CanOSpam on 2009-01-29
I assume the command i should be using is:
cat /boot/grub/menu.ls

---

### Post by bumanie on 2009-01-29
It's OK what you posted, while I was typing a response is all I need. I'll come back with instruction in a few minutes :).

---

### Post by CanOSpam on 2009-01-29
Alright! Thanks alot!

---

### Post by bumanie on 2009-01-29
This is the end of your present list, as suspected there is no vista entry, so after this line add the red to your list. You edit it by going to terminal > gksudo gedit /boot/grub/menu.lst
Under the following line add the red text (you can copy/paste) and then save it (save is on top left of the page)
 ### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

[COLOR="Black"]Reboot the computer and you should get the choice of booting into ubuntu or vista. [/COLOR]

---

### Post by CanOSpam on 2009-01-29
Alright... rebooting now. Thanks a ton!!!

EDIT: IT worked!!!! Awesome! thanks so much!

---

