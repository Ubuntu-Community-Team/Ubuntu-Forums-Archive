---
title: "Restore GRUB"
date: 2006-08-28
forum: Desktop Environments
---

### Post by rado_london on 2006-08-28
Hi. I had 3 OSs on my laptop- Ubuntu, XP and OS X. I used the GRUB to choose the OS. I had to reinstall XP and then restored GRUB. However now I replaced XP with slackware and what I got when I turn on my pc is LILO. It has two options. One boots up the slack and the other one goes to the GRUB menu. My question is:

How can I make GRUB to be the only boot loader.

The slackware is installed on /dev/hda2

Here is full output of fdisk -l:
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       51688    26050248   af  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda2           51702      103371    26041365   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          103371      155056    26049397+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          103371      153176    25101531   83  Linux
/dev/hda6          153176      155056      947803+  82  Linux swap / Solaris

```

if you need any aditional info I would love to provide it.

Thanks in advance!

---

### Post by bernied on 2006-08-28
Work out which partition has the grub menu.lst on it - if it's the second partition (hda2), then grub calls this (hd0,1).
Go to the grub menu, then hit c to go into the grub command line. Then type
root (hd0,1)     # or whichever it is
setup (hd0)
reboot

That should do the job, unless you got errors at the setup command (if you got the partition wrong).

---

### Post by bernied on 2006-08-28
And you may need to add an entry to your menu.lst for your new slackware install.

---

### Post by rado_london on 2006-08-28
grub should be in /dev/hda5. What are the commands for hda5 or how can I find out which is the correct one I have to use.

---

### Post by bernied on 2006-08-28
I just saw that your slackware install is hda2, so your ubuntu install (and original grub, right?) is on hda5. grub will call this (hd0,2) as it's the third partition on the first disk (I think). To check this you can use tab-completion in the grub-console. So type:
root (hd0,      
then hit TAB and it will give you options. Choose an option and then type:
cat /
then hit TAB and you'll see what at the root of that partition. This way you can find your grub menu.lst using the grub naming system.

If the setup command still doesn't work, you can try modifying the root command to include the boot directory:
root (hd0,2)/boot
but this may not be necessary.

You can also try the command
grub-install 
from within ubuntu. But personally I like the grub command line.

---

### Post by rado_london on 2006-08-28
Done it worked with hd0,4
Now what do I have to do in order to get slackware within the grub menu?

---

### Post by bernied on 2006-08-28
You'll need the slackware kernel location and boot options, and maybe the location of the initrd file, if it is used. Best place to find this is on the lilo configuration file. But I don't know lilo, so don't know where this is found. Somewhere on the slackware partition anyway, so you'll need to mount that. It may already be mounted. Use:
mount
to find out. If not, I'd suggest adding an entry to /etc/fstab because you'll probably want to access it on occasion anyway. So:
sudo nano /etc/fstab
add a line for /dev/hda2 if there isn't one already, choosing a suitable mount point and just choosing defaults for options. (You can change this later)
Then add the mount point
sudo mkdir /wherever/you/decide
Then:
sudo mount /dev/hda2
to mount it.

Then find the lilo config file (can't help you there)

Then edit the menu.lst file:
sudo nano /boot/grub/menu.lst
and add an entry for slackware. You should be able to figure out how to translate the lilo commands to grub, based on what is already in the menu.lst file. If not, post the contents of the lilo config file here and we'll work it out.

---

### Post by bernied on 2006-08-28
I just googled for lilo and found that the default (for Red Hat anyway) is at /etc/lilo.conf

---

### Post by rado_london on 2006-08-28
> **bernied said:**
> I just googled for lilo and found that the default (for Red Hat anyway) is at /etc/lilo.conf

I know where it is. It took me some time to get it with the right permissions. However I added teh slackware to the grub menu but I get kernel panic.
Here is the grub menu.lst:
```
carado@ubuntu:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
#password 88de71e5

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single rootflags=data=writeback

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

## ## End Default Options ##

title           Ubuntu
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Slackware
root            (hd0,1)
kernel          /boot/vmlinuz
boot

#title          Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root           (hd0,4)
#kernel         /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single rootflags=data=writeback
#initrd         /boot/initrd.img-2.6.15-25-386
#boot

#title          Ubuntu, memtest86+
#root           (hd0,4)
#kernel         /boot/memtest86+.bin
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root

#title           Microsoft Windows
#root            (hd0,1)
#chainloader     +1
#boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2

title Mac OS X
root (hd0,0)
makeactive
chainload OS/2 bootloader from the first sector
chainloader +1

```
Here is the lilo.conf file:
```
# LILO configuration file
# generated by 'liloconfig'
#
# Start LILO global section
boot="/dev/hda"
message = /boot/boot_message.txt
prompt
timeout="30"
# Override dangerous defaults that rewrite the partition table:
change-rules
  reset
# VESA framebuffer console @ 1024x768x256
vga="773"
# Normal VGA console
# vga = normal
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769
# End LILO global section
# Linux bootable partition config begins
compact
default=ubuntu

	root="/dev/hda5"
	label="Linux"
  read-only
# Linux bootable partition config ends

image="/dev/hda5"
	root="/dev/hda2"

image="/dev/hda5"
	root="/dev/hda2"



image=/boot/vmlinuz
```

What am I doing wrong?

---

### Post by bernied on 2006-08-28
Well, at least 'kernel panic' means you found the kernel and it is trying to boot. 

Two maybes:
- you need an initrd, like ubuntu uses. Is there an initrd file in the slack /boot directory?
- you need a root=/dev/hda2 option at the end of the kernel line.

And you could throw in a vga=773 on the kernel line as well, to make it true to the lilo conf file.

You're moving away from what I know now, having never run slackware, but we'll get there.

---

### Post by bernied on 2006-08-28
Try the second one first - looks likely after cruising slack sites. The vga= will probably just change the appearance of the boot sequence. You can also use quiet for less messages, ro I think is read only, though not really sure how this works, because it doesn't result in a read-only filesystem. And splash, if it is enables in the kernel, gives some pretty picture at startup.

---

### Post by rado_london on 2006-08-29
its done I had to specify the kernel not only /boot/vmlinuz but /boot/vmlinuz-number. I am in OS X now so once I am in Ubuntu I will post the exact menu.lst output so people will benefit my little and lucky solution. Thanks for the help bro!

---

### Post by bernied on 2006-08-29
No problem.

---

### Post by rado_london on 2006-08-30
Here is the menu.lst:
```
rado@ubuntu:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
#password 88de71e5

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single rootflags=data=writeback

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

## ## End Default Options ##

title           Ubuntu
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Slackware
root            (hd0,0)
kernel          /boot/vmlinuz-ide-2.4.31 root=/dev/hda2 ro
boot

#title          Ubuntu, kernel 2.6.15-25-386 (recovery mode)
#root           (hd0,4)
#kernel         /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single rootflags=data=writeback
#initrd         /boot/initrd.img-2.6.15-25-386
#boot

#title          Ubuntu, memtest86+
#root           (hd0,4)
#kernel         /boot/memtest86+.bin
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root

#title           Microsoft Windows
#root            (hd0,1)
#chainloader     +1
#boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2

title Mac OS X
root (hd0,0)
makeactive
chainload OS/2 bootloader from the first sector
chainloader +1

```

---

### Post by bernied on 2006-08-30
You might want to consider moving that Slackware entry. If you leave it where it is it will get wiped out next time you upgrade your ubuntu kernel, if you use the standard ubuntu methods. When the kernel is upgraded, grub menu.lst entries get updated as well, according to the defaults in the automagic area of the file, and your slackware entry is not included so will get wiped. Just move it so it's outside of this area, like where you have your OS/X entry. You can change those defaults, but you can't get it to look outside the ubuntu boot partition, so you can't get it to update your slackware entry automatically, you'll have to do that yourself if you make changes - like installing a new kernel.
> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

---

