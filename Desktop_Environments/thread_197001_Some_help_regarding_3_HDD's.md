---
title: "Some help regarding 3 HDD's"
date: 2006-06-15
forum: Desktop Environments
---

### Post by frup on 2006-06-15
Ok this is quite complicated for me.
I have 3 HDD's a 40GB and 2 80GB. Ubuntu is on the 40GB. Another Linux is on one 80GB and Windows is on the other (well not really it doesnt work... its just NTFS basically lol).
When installing Ubuntu i think i messed up grub... i havent cared untill now but am in the mood to try fix this... each OS was basically installed when it was in HDA1. when i try put all 3 in i get a grub error. 2 works ok. Right now i have both linuxs in the other being linspire which sux. I cant boot in to linspire even though it shows on the grub list... it shows the linspire splash and then on comes the ubuntu log in screen. :S... in this mode if i log in alot of things dont work either.

What i would like to do is get all 3 plugged in at once and work. 
This windows is broken too and i dont really care about the two 80GB drive as long as i can keep the data... eg my 25GB of mp3s WHICH i cant copy on to the 40GB as its more space than the 40GB has.

That means i need to have both in before i can format one. i would like one then to become my /home partition. can i make both in to /home partitions? if i cant make them both part of /home in a way that works well, what would be the best place to mount the other one too?

My CD drive is pretty screwy too so preferably a way to do this that wont destroy anything. If necessarily i realise i could take the ubuntu drive out, copy everything to the linspire drive... format the XP drive there and copy everything back and then go from there blaah blaah blaah... but like i said i dont want to use the CD as it doesnt work most of the time (this is a hardware issue)

IF these drives are both formatted will i get the grub error? i think i have gotten error 25 and 21 from screwing around with this. 

Is rieserFS a good filesystem? what would the advantages of keeping this be? if people think i should keep linspire working how do i fix it... note i only really used this for a month because i downloaded it for free and hadnt heard of ubuntu at that stage.

Why is it my CD drive (well its a DVD ROM) doesnt work now... it already happened to my CDRW when i was using windows... i think it might be power surges from the motherboard... it starts to make scratchy noises and then just freezes when being used... sometimes disapears from the My computer area, sometimes shows. 

i know this long and probably sounds stupid. thanks for any help in advance.

---

### Post by frup on 2006-06-15
anyone? please

---

### Post by Ramses de Norre on 2006-06-15
What harddrives are it (ata or sata), how are they arranged (master slave stuff) and which one do you boot from? What's in /boot/grub/menu.lst? Some more info is needed.. Can you mount the drives when only two are connected?

---

### Post by frup on 2006-06-15
Yes when two are in, ubuntu as Primary master any other as Primary slave it works fine. They are ATA. its when i add one as a Secondry master or secondry slave it goes funny

This is the menu.lst for Ubuntu
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Linspire 5.0.59 on /dev/hda1 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Redetect (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Diagnostics (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot
```
This is the linspire Menu.lst
```
# Generated by jiffyboot version 7.0.53. If this file is edited, the
# system will stop modifying it.  To allow the system to resume
# management of this file, remove it and run /sbin/jiffyboot

default=0
timeout=10
color cyan/green magenta/green
splashimage=/boot/grub/bootsplash.xpm.gz

title Linspire 5.0.59 on /dev/hda1
root (hd0,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hda1 rootdev=0x0301  ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Redetect
root (hd0,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hda1 rootdev=0x0301  ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Diagnostics
root (hd0,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hda1 rootdev=0x0301  ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title MS Windows® XP on /dev/hdb1
root (hd1,0)
chainloader +1
```

---

### Post by Ramses de Norre on 2006-06-15
And which of the two is used by grub?
Also did you check the jumpers? A disk with jumper set to master doesn't work when plugged in as slave..

---

### Post by frup on 2006-06-15
OK well i just plugged in all 3 HDD's for the first time since using dapper... it has worked... initially it said Hard Disk Error but then for some reason it started working... so hopefully that which i feel was the hardest part, is fixed.
note when it says detecting IDE drives theres a message below saying something like no secondary conducter cable 80 or something... it disappears to fast for me to read.
Ubtuntus grub is on the MBR... ubuntu is all i can get in to.

But as long as this works i now would like to know
1. how to fix linspire so it runs (because i just remembered Lsongs updates ipods and rythem box doesnt seem to work... ipod 60gb video.)
2. If this works i only need one /home partition... as one drive will be for Linspire. i have a website bookmarked to do this.

so things are getting easier :D

---

### Post by frup on 2006-06-15
This is how Menu.lst looks now also... i dont know if it has changed yet
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Linspire 5.0.59 on /dev/hda1 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Redetect (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Diagnostics (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot
```

EDIT
the drives weren't mounted by default. i have just run the Disks tool... right now i am just doing chown -R username /windows (the mount folder) so i can access this.

---

### Post by Ramses de Norre on 2006-06-15
The linspire section uses the same root directory as the ubuntu one, make it look like this: ```
title Linspire 5.0.59 on /dev/hda1
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Redetect
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Diagnostics
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)
```

Am I correct Linspire is on the primary slave? Otherwise this wont work=)

---

### Post by frup on 2006-06-15
crap... i edited the linspire grub without backing up and just realised you meant ubuntus... does this matter?
otherwise i will just take the data off linpsire and format ext3

---

### Post by CatKiller on 2006-06-15
[QUOTE=frup]note when it says detecting IDE drives theres a message below saying something like no secondary conducter cable 80 or something... it disappears to fast for me to read.
[/QUOTE]

This isn't actually a problem - It means either you're using a 80-conductor cable on the secondary IDE channel when you don't have to (because your drive doesn't use it) or because you aren't using one when you do have to (because the drive requires it to operate at higher data-transfer rates). Once you've got everything else sorted out, you can fit whichever type of cable you aren't using now to the secondary IDE channel and the message will go away. Not too much of a problem in the meantime though.

---

### Post by Ramses de Norre on 2006-06-15
[QUOTE=frup]crap... i edited the linspire grub without backing up and just realised you meant ubuntus... does this matter?
otherwise i will just take the data off linpsire and format ext3[/QUOTE]

I guess you just made a back up of them by posting them in this thread ;)

---

### Post by frup on 2006-06-15
serves me right for being tired :D lol
ok just to reiterate... that fix you gave me was for ubuntus menu.lst not linspires?... i edited linspires not ubuntu's.

i've done some really stupid things tonight lol. but i have been lucky so far to be able to fix everything i messed up. 

i noticed that on ubuntus grub i have so many options! shouldnt some of these not be there... i dont know what the k7 is... i think i downloaded of synaptic a k7 file but i tought that was a nvidia thing... my motherboard is a gigabite k7 triton or someting with amd athlon that is why i did that... also my breezy entry appear to be there :S

the redetect loads ubuntu after doing some stuff with some notices that fail. i thought (but am probably wrong) this tried to check grub was right.

i now have 1 40gb ubuntu drive HDA an 80gb Linspire drive HDB and an 80gb ext3 drive HDD i was going to use this guide [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) but it seems that this might not apply... using ubuntus disks thing i managed to mount it as home (screwing up my pc until i restarted and it unmounted) i have now backed up home so if i mount this again like this and copy the home_backup over this will function properly? then just edit fstab to add it as home permanantly later no?

this is ubtunus fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
#/dev/hdd1 /windows ntfs nls=utf8,umask=0222 0 0
#windows is now gone forever
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
adding 
/dev/hdd1       /home               ext3    defaults,errors=remount-ro 0       1
will make home work?
how would i make the rieserfs mount 
/dev/hdb1    /linspire                reiserfs  rw                                  0 0
?
also i've noticed hdd is my cd drive too... is this why its behaving badly?...although this happened before too.
this is my fstab for linspire which will most likely need changing
```
/dev/root    /                reiserfs  rw                                  0 0
none         /proc            proc      defaults                            0 0
none         /sys             sysfs     defaults                            0 0
none         /proc/bus/usb    usbfs     defaults                            0 0
none         /dev             devfs     rw                                  0 0
none         /dev/pts         devpts    rw                                  0 0
none         /dev/shm         tmpfs     rw                                  0 0
# jiffymount: added at 10:16 05-Mar-2006 for /dev/hdb1
/dev/hdb1    /mnt/hdb1        ntfs      noatime,user,exec,dev,suid          0 0
# jiffymount: added at 10:16 05-Mar-2006 for UUID=b9d2f9e9-680e-4957-bdd4-d04cf7bf2d62
UUID=b9d2f9e9-680e-4957-bdd4-d04cf7bf2d62 /mnt/hdc1        reiserfs  noatime,user,exec,dev,suid          0 0
# jiffymount: added at 10:17 05-Mar-2006 for /boot/linux-swap.swp
/boot/linux-swap.swp none             swap      sw                                  0 0
# jiffymount: added at 10:17 05-Mar-2006 for /mnt/hdc1/boot/linux-swap.swp
/mnt/hdc1/boot/linux-swap.swp none             swap      sw                                  0 0
/dev/fd0     /mnt/floppy1     supermount dev=/dev/fd0,fs=vfat,--,noauto,user,exec 0 0
# jiffymount: added at 15:21 05-Mar-2006 for /dev/cdroms/cdrom0
/dev/cdroms/cdrom0 /mnt/cdrom0      supermount dev=/dev/cdroms/cdrom0,fs=iso9660,--,noauto,user,exec 0 0
```



my current menu.lst for ubuntu
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Linspire 5.0.59 on /dev/hda1 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Redetect (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Diagnostics (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot
```
 and linspire (the one i edited)
```
title Linspire 5.0.59 on /dev/hda1
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Redetect
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Diagnostics
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)
```

---

### Post by frup on 2006-06-15
sorry to keep bugging everyone with this...

---

### Post by frup on 2006-06-16
please help me :(

---

