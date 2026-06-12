---
title: "Booting problems"
date: 2008-12-23
forum: General Help
---

### Post by test_test_testing on 2008-12-23
I got Ubuntu about 2 weeks ago to try it out, so I installed it alongside Win XP Pro using wubi. It was great! Fast, elegant, and a VERY wide range of software to choose from.

Therefore, with a little unoccupied space on my hard drives, I created an ext3 partition with 20gbs of space using gParted and, using LVPM, moved Ubuntu to its permanent home. After a while, it told me to restart.

Firstly, it went through the normal memory checks etc, then a new menu popped up:
> 
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-3-rt
Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
Ubuntu 8.10, memtest96+
Other operating systems:
Microsoft Windows XP Professional
Other operating systems:
Windows
Microsoft Windows XP Professional

Use the ^ and v keys to move your selection etc...

(Microsoft Windows XP Professional does appear twice, not a typo)

If I choose any of the Ubuntu kernels, an error would appear:

> 
Error 17: Cannot mount selected partition
Press any key to continue...


And it would take me back to that menu. If I choose Windows XP, the normal menu that I got before transferring Ubuntu would appear:

> 
Please select the operating system to start:
Microsoft Windows XP Professional
Ubuntu
Use the up and down arrows to select etc.

For troubleshooting and advanced startup options for Windows, press F8.


And now if I choose Ubuntu the loading message would appear as normal:

> 
Press 'ESC' to enter the menu...10 (counting down)


and Ubuntu would boot normally. Also after transferring Ubuntu to a new partition, when I mount the NTFS partition that the virtual disk was on, it would only display the contents of the virtual disk, not the contents of the actual disk itself.

Does anybody here know how to get rid of one of the menus and the error messages? And how to access the actual NTFS partition again? Any help would be greatly appreciated.

EDIT: Just discovered that Ubuntu still seems to be booting off the virtual disk, ran df -h and it showed that dev/sda6 (the NTFS partition with the virtual disk on) had 40gbs of total space, instead of dev/sda3 (the newly created EXT3 partition) with 20gbs of total space. Any ideas?

---

### Post by azmo35 on 2008-12-24
Hi, if you add this(hd0.1) to the ubuntu you can boot the real partition 
(hdo.1)Ubuntu 8.10, kernel 2.6.27-9-generic
(hd0.1)Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-3-rt
Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
(hd0.1)Ubuntu 8.10, memtest96+
the "hd0.0" is the windows install and "hd0.1" ubuntu you can add this on boot time pessing "esc","e" for edit and "e" again [()Ubuntu 8.10, kernel 2.6.27-9-generic_]move the end corsor to begining and add (hdo.1)Ubuntu 8.10, kernel 2.6.27-9-generic now press "b" for booting if this worked change your menu.1st. 
The other two karnels use synaptic to remove them i hope this help you.

---

### Post by test_test_testing on 2008-12-24
Sorry, but that doesn't seem to work... or am I missing something?

Here's my /boot/grub/menu.lst if anybody needs it:

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
# kopt=root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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



title Ubuntu-on-/dev/sda3
root (hd0,2)
configfile /boot/grub/menu.lst



```

EDIT: After a bit of tweaking and a lot of help from several sites, I managed to get it to work. Now the only problem that remains is that when I boot Windows, another menu (the old menu) comes up asking me whether I want Windows or Ubuntu (virtual). How do I get rid of that?

---

### Post by azmo35 on 2008-12-24
Hi,like i said you need add (hd0.1)
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0.1)/ubuntu/disks <LOOK ON THIS EXAMPLE>
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ABC390FBC38F753 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
YOU can do this on boot up pessing a "e" key and again "e" key to move the _ to the point () wher you can type hd0.1 now pess "b" key for boot if work go ahed and edit your menu.1st.
If you look closely your menu.1st windows root (hd0.0) and wubi root (hd0.2) so if you have 2 partitions ubuntu is (hd0.1).

---

### Post by azmo35 on 2008-12-24
:-\"#
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

---

### Post by test_test_testing on 2008-12-24
Sorry I didn't understand your first example. I got it to work now (it was because the hard drive I needed was (hd0,2) not (hd0,1) :lolflag:)

Any ideas on how to get rid of the old menu (asking me whether I want to boot the old virtual Ubuntu) appearing when I try to boot Windows?

(And isn't the file menu.lst not menu.1st? L after the dot)

---

### Post by azmo35 on 2008-12-24
Well now i'm confused in your menu.lst wubi is on (hd0.2) so i suggest you remove wubi install from windows and if the error 17 appear change (hd0.2) for (hd0.1),after this solved opem terminal gksu nautilus navigate to boot/grub/ and copy menu.lst to safe place desctop is ok go ahed and make the change you want save it boot.

---

### Post by test_test_testing on 2008-12-25
Uhhh... I deliberately put Wubi Ubuntu into (hd0,2) ie E:\ because it had most space xD

Anyway, onto more serious problems, I now get a BSOD when trying to boot into Windows. In the main boot screen I get Ubuntu and a list of kernels, and Other operating systems: Microsoft Windows XP Professsional. I choose XP, and then another menu: XP or Ubuntu (virtual - wubi). I choose XP, and it shows the main screen with the blue scrolling bar, then the bar suddenly freezes and then a BSOD appears with:

UNMOUNTABLE_BOOT_VOLUME

Does this involve C:/boot.ini? If so, booting from Ubuntu and loading up boot.ini shows this:

> 
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

c:\wubildr.mbr="Ubuntu"



What's going wrong? Thanks!

---

### Post by azmo35 on 2008-12-26
Sorry mate but if i understand your post above you have 2 **hdd** if so it should i think (hd1.0) but i'm not sure.




[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by test_test_testing on 2008-12-26
No, I have 1 hdd, with 4 partitions now

hd0,0 is Windows boot partition
hd0,1 and hd0,2 are for data and programs, with hd0,2 holding virtual ubuntu
hd0,3 is ext3 partition with ubuntu on.

---

### Post by azmo35 on 2008-12-28
Sorry mate but the **hdd** holding **Wubi/virtual Ubuntu** is hd0.0 the same of Windows where you intall Wubi the first place.


:!:(hd0.1)(hd0.2)for programs fat or ext2 or swap:?:

---

