---
title: "grub wierdness"
date: 2009-01-27
forum: General Help
---

### Post by donald7777 on 2009-01-27
Hello everyone. I recently did a restore to my ubuntu and now whenever i boot up grub tells how much memory is free at the top, and my ubuntu splash screen now only lasts for half the boot time, and the screen fills with the messages of the system booting up. How do i fix this. it also semi occurs when i boot xp. you can see the test the menu.lst uses for xp to boot . eg cant remember but at the bottom there is the chainloader +1

---

### Post by Svensk023 on 2009-01-27
that has happened to me before, although not meaning to solve the problem this was a nice suprise of a fix for me

If you have more than one CPU u can have boot process run parallel to eachother by doing as follows

```
sudo gedit /etc/init.d/rc
```

look for the line that reads 

CONCURRENCY=None 

and change it to

CONCURRENCY=shell

also at your next boot you can create a readahead profile which will also help with boot time by doing as follows:

at the boot menu hit the "e" key
use the cursor to highlight "kernel", then hit "e" again.
use the right arrow key to move to the end of the line and add the word "profile"

it will read:

"ro quiet splash profile"
then hit "enter" and then "b" to boot your computer. This boot **will** take a bit longer than normal, but after the boot re-start your computer and see if that helped, it should have improved you boot time and hopefully fixed your splash screen blip (no that there is anything seriously wrong with what youre experiencing)

---

### Post by mb_webguy on 2009-01-27
I'd just like to thank Svensk023 for his suggestion of setting the value of concurrency in the /etc/init.d/rc to "shell" for multi-core computers.  I've been using Linux for years, but haven't had any experience running it on multi-core computers until I got my current laptop, and I hadn't seen that suggested before.  I just tried it, and... wow!  Startup was so fast, the login process actually took longer!

---

### Post by Svensk023 on 2009-01-27
> **mb_webguy said:**
> I'd just like to thank Svensk023 for his suggestion of setting the value of concurrency in the /etc/init.d/rc to "shell" for multi-core computers.  I've been using Linux for years, but haven't had any experience running it on multi-core computers until I got my current laptop, and I hadn't seen that suggested before.  I just tried it, and... wow!  Startup was so fast, the login process actually took longer!

haha im glad that it helped you out! its encouraging to know that my advice helped at least one person :D

---

### Post by caljohnsmith on 2009-01-27
**Donald7777**, it would help to get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. Also please post the output of:
```
cat /etc/initramfs-tools/conf.d/resume
```
And we can work from there if you want.

---

### Post by donald7777 on 2009-02-14
will try sorry about the log wait havent been near internet for a while

---

### Post by donald7777 on 2009-02-14
ok that speed up everything except the text still shows nad the splash screen still disappers.

---

### Post by donald7777 on 2009-02-14
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28c428c3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   249,682,229   249,682,167   7 HPFS/NTFS
/dev/sda2         249,682,230   312,576,704    62,894,475   5 Extended
/dev/sda5         249,682,293   304,769,114    55,086,822  83 Linux
/dev/sda6         304,769,178   312,576,704     7,807,527  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="C66C98096C97F283" TYPE="ntfs" 
/dev/sda5: UUID="1d8c3497-c0fb-445e-b557-53339deddd78" TYPE="ext3" 
/dev/sda6: UUID="05109b92-e535-49c8-858a-d37653a09666" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,noatime,nodiratime,errors=remount-ro,data=writeback)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/donald/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=donald)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sda5/boot/grub/menu.lst: ===========================

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
color dark-gray/black blink-light-blue/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/Deepspace-night.xpm.gz

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
# kopt=root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1d8c3497-c0fb-445e-b557-53339deddd78

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
# defoptions=splash vga=791 rootflags=data=writeback

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
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1


========================== sda5/boot/grub/grub.conf: ==========================

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
color dark-gray/black blink-light-blue/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/Deepspace-night.xpm.gz

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
# kopt=root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1d8c3497-c0fb-445e-b557-53339deddd78

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
# defoptions=splash vga=773

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
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro  splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro  splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1d8c3497-c0fb-445e-b557-53339deddd78 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1d8c3497-c0fb-445e-b557-53339deddd78
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1d8c3497-c0fb-445e-b557-53339deddd78 /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# /dev/sda6
UUID=1af0658c-2549-4f9a-a790-15410d283d13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 148.8GB: boot/grub/grub.conf
 148.8GB: boot/grub/menu.lst
 148.8GB: boot/grub/stage2
 148.9GB: boot/initrd.img-2.6.27-7-generic
 148.8GB: boot/initrd.img-2.6.27-9-generic
 148.7GB: boot/vmlinuz-2.6.27-7-generic
 148.7GB: boot/vmlinuz-2.6.27-9-generic
 148.8GB: initrd.img
 148.9GB: initrd.img.old
 148.7GB: vmlinuz
 148.7GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

 sdb .

```

---

### Post by donald7777 on 2009-02-14
here is the resume outpost form terminal
RESUME=UUID=1af0658c-2549-4f9a-a790-15410d283d13

---

### Post by caljohnsmith on 2009-02-14
It looks like the problem is your swap UUID changed. How about doing:
```
sudo swapoff -a
sudo mkswap -U 1af0658c-2549-4f9a-a790-15410d283d13 /dev/sda6
```
Reboot, and let me know if you get the Ubuntu splash screen or not.

---

### Post by donald7777 on 2009-02-15
just at work right now will try when i get home. what would cause that. if i restored from a image wouldnt the uuid be the same?

---

### Post by donald7777 on 2009-02-15
that solved it thankyou. now comes a stupid question why wouldnt ubuntu say it cant find/use the swap partion. you would think that would be portant especially for a laptop.

---

### Post by caljohnsmith on 2009-02-15
> **donald7777 said:**
> that solved it thankyou. now comes a stupid question why wouldnt ubuntu say it cant find/use the swap partion. you would think that would be portant especially for a laptop.
Glad to hear your swap partition is working again. I agree that Ubuntu should alert the user when it can't find the swap partition, but unfortunately it doesn't right now. Anyway, cheers and hope things go smoother now for your Ubuntu install.

---

