---
title: "invalid device string error [grub starting problem]"
date: 2008-07-06
forum: Desktop Environments
---

### Post by ramaswamyps on 2008-07-06
this desktop computer is multiboot system .
i have win98,win2k,xp , pclinuxos,two gentoo installs and now ubuntu-studio-8.04.1
if i format or change some partiton format the ubuntu grub
stops booting .
gives invalid device string error.
i have presently installed the ubuntu grub to boot the main system.
is it possible to repair this error or i have to change the grub of some  other system?

anybody got this error?

---

### Post by logos34 on 2008-07-06
What exactly did you change?

Usually that error message means there's a typo/syntax error of some sort in /boot/grub/menu.lst.

Boot from the live cd, mount ubuntu root, and navigate to menu.lst.  Post it so we can check it out.

also, post

sudo fdisk -l

---

### Post by ramaswamyps on 2008-07-06
padoor ~ #mount /dev/sda9 /mnt/hda9

the problem is i get while chroot is i get error like this.
padoor ~ # chroot /mnt/hda9 /bin/bash
id: cannot find name for group ID 11
root@padoor:/# 

that is while trying to chroot in my gentoo system to update-grub
this example is shown from my laptop ubuntu
/dev/sda9 is ubuntu install.

my menu.lst is as follows
----------------------------------------------------------
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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b ro single
initrd		/boot/initrd.img-2.6.24-19-rt

#title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Gentoo Linux 2.6.23-r9 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/kernel-2.6.23-gentoo-r9 root=/dev/hda6 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 8.04 (8.04) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb7 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title		pclinuxos (on /dev/sdb8)
root		(hd1,7)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdc8 acpi=on 
initrd		(hd1,7)/boot/initrd.img
savedefault
boot
---------------------------------------------------------

the partition /dev/sdb7 ubuntu did not install correctly.
there was a grub install failed.
i want to format this partition ntfs and use it for data.

currently the recovery mode boot says invalid device string and it does not boot.

i have had this error 2 3 times in my laaptop 
i was able to rename menu.lst and use bak copy of it to boot up.

somehow this error comes up even if i did not change fstab or menu.lst in ubuntu.

other system changes also brings out this error.

what can i do to avoid tinkering with this trouble every day??

why the device string changes with other partion format or changes in other system installations?

the grubs in other linux installs dont stick a device string in fstab.

thanks for a reply:)

---

### Post by wired465 on 2008-07-06
> **ramaswamyps said:**
> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
**root**


This looks like an orphaned entry... there should not be a root entry alone like this, especially without a partition identifier (i.e. root (hd0,1)

---

### Post by ramaswamyps on 2008-07-06
ok i will try commenting out root entry.

what makes the device string change ?
looks like it keeps a md5 of the whole system.
let me try if it will correct this error in recovery boot now.:)

for academic interest

can i not replace the kernel line root=/dev/sda8 
instead of the generated boot line by installer?

title Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b ro single
initrd /boot/initrd.img-2.6.24-19-rt

---

### Post by ramaswamyps on 2008-07-06
the recovery kernel entry starts the memtest!!
i dont see why it should.

i tried manual grub lines 

root (hd0,7)
kernel /boot/vmlinuz-2.6.24-19-rt root=/dev/sda8
initrd /boot/initrd.img-2.6.24-19-rt
boot

it boots to kde desktop in verbose  mode.

the recovery boot i cannot do now.

---

### Post by logos34 on 2008-07-07
make another change in menu.lst (near top):

[B]default 0

[/B]I would advise you to continue using the UUIDs wto avoid additional confusion.  If you delete a logical partition, sometimes the remaining partition #s inside the extended change.  But if you just formatted, not sure what happened.

Could you please post your 

sudo fdisk -l

You apparently have two drives

---

### Post by ramaswamyps on 2008-07-07
ramaswamy@ubuntu:~$ sudo fdisk -l
[sudo] password for ramaswamy:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c922f12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1424    11438248+   7  HPFS/NTFS
/dev/sda2            1425        9729    66709912+   5  Extended
/dev/sda5            1425        1612     1510078+  82  Linux swap /Solaris
/dev/sda6            1613        5259    29294496   83  Linux
/dev/sda7            5260        7691    19535008+  83  Linux
/dev/sda8            7692        9729    16370203+  83  Linux

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69706970

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1148     9221278+   7  HPFS/NTFS
/dev/sdb2            1149        4870    29896965    f  W95 Ext'd (LBA)
/dev/sdb5            1149        2296     9221278+   b  W95 FAT32
/dev/sdb6            2297        3188     7164958+   7  HPFS/NTFS
/dev/sdb7            3189        4077     7140861    b  W95 FAT32
/dev/sdb8            4078        4870     6369741   83  Linux

Disk /dev/sdc: 2055 MB, 2055207936 bytes
33 heads, 63 sectors/track, 1930 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0xfc6ac10f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1931     2007023    b  W95 FAT32
ramaswamy@ubuntu:~$

i have a feeling ubuntu grub keeps track of changes in the whole box and keeps changing the device string.

default 0 i dont want.
i want windows to boot up when i switch on and go away for other things in the morning.

the current arrangement works ok .only snag is occationally i have to tackle this device string error.

could you tell me why i am not able chroot into gentoo or other linux shell?

why the group id not recognised?

---

### Post by logos34 on 2008-07-07
> **ramaswamyps said:**
> i have a feeling ubuntu grub keeps track of changes in the whole box and keeps changing the device string.

default 0 i dont want.
i want windows to boot up when i switch on and go away for other things in the morning.


Then you want [B]default 4. 
[/B](fix memtest line--see below)

First off, I noticed some errors:

>  

Uncomment memtest:

[COLOR=Red] #[/COLOR]title        Ubuntu 8.04.1, memtest86+

...

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Gentoo Linux 2.6.23-r9 (on /dev/sda6)
root        (hd0,5)
kernel        /boot/kernel-2.6.23-gentoo-r9 root=/dev/[COLOR=Red]hda6[/COLOR] 
[COLOR=Red][where's initrd line ?][/COLOR]
savedefault
boot

...

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title        pclinuxos (on /dev/sdb:cool:
root        (hd1,7)
kernel        /boot/vmlinuz BOOT_IMAGE=linux root=/dev/[COLOR=Red]hdc8[/COLOR] acpi=on 
initrd        [COLOR=Red](hd1,7)[/COLOR]/boot/initrd.img
savedefault
boot
Gentoo should be 'root=/dev/[COLOR=Black]**s**da6', and pclinuxos '[/COLOR]root=/dev/[COLOR=Black]**sdb**8'.

But I still can't figure out why the device string error message or why the recovery is booting the memtest (!)...or the regular kernel to kde desktop (huh?)....Check the UUID of ubuntu root again (sudo blkid, or sudo vol_id /dev/sda8).  Not sure about chroot in gentoo either
[/COLOR]

---

### Post by Bucky Ball on 2008-07-07
You sound a little more knowledgeable about Grub than myself, but I found this really helpful when I was having some boot probs;

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Worked a treat for me and if it doesn't for you, then probably something deeper down.

Good luck.

---

### Post by ramaswamyps on 2008-07-07
ramaswamy@ubuntu:~$ sudo vol_id /dev/sda8
[sudo] password for ramaswamy:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b
ID_FS_UUID_ENC=ddd89ef7-e8da-4d1f-b6ee-f69190514f4b
ID_FS_LABEL=ubuntu
ID_FS_LABEL_ENC=ubuntu
ID_FS_LABEL_SAFE=ubuntu
ramaswamy@ubuntu:~$

that shows even more complications.
if i am locked out of ubuntu i cannot get this vol id
i dont know what else to look for?

i will check the link you have given.
thanks.
grub has never been that difficult to handle.
but now we have total unexpected errors it is throwing.
lets see. worst comes i can mount the device without vol id and it boots up anyway.

if i cant mount in another sysetem shell it will be same for live cd mount also.

something funny going on here.:(


one more thing to mention is iadded a splash image in the grub.

then the updater poped up to say update of menu.lst is available.
updated to maintainers menu.lst.

nice slash comes up with the boot menu.
currently i copied splash.xpm.gz from gentoo grub.

---

### Post by linuxguru1 on 2009-03-15
I had the same problem about 20 minutes ago. I added a splash in my bootmenu, then everything stopped working. I added the splash using the QGrubeditor tool. Happely the tool made me a backup. I replaced the edited menu.lst with the backup, and now everything works smoothly again :)

Hope that helped...

---

