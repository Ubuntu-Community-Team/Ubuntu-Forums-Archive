---
title: "windows refuses to load in XP/Ubuntu dual boot after three weeks"
date: 2009-06-10
forum: General Help
---

### Post by TheLastAlive on 2009-06-10
At first I had windows, but I grew very tired of self executing viruses.  So I realised I could switch over to ubuntu without having to give up commercial games or without having to deal with the reduced performance of virtual machines and emulators.

So I downloaded the bootdisk, burned it, and poped it in the drive.  I resized the windows partition to around 200 gigabytes and created a new 800 gigabyte partition for ubuntu.  Both on my terabyte HDD.  Both partitions booted fine.

So I used ubuntu for around three weeks.  But today, when I went to install a game on windows for the first time, it attempts to boot up and then switches over to a blue screen for a fraction of a second and then restarts.  I try to repair or reinstall XP on the windows partition and the windows bootdisk is unable to recognize that there is even a HDD in the computer.

Ubuntu boots fine, and I haven't done anything to windows since the day I lasted booted it.  Can someone please help me understand what the problem is?

---

### Post by merlinus on 2009-06-10
Obviously there a number of possibilities.  One is that your xp boot disk is corrupt.

Post output of these terminal commands:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by TheLastAlive on 2009-06-10
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98a398a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26113   209752641    7  HPFS/NTFS
/dev/sda2           26114      121601   767007360    5  Extended
/dev/sda5           26114      120662   759464811   83  Linux
/dev/sda6          120663      121601     7542486   82  Linux swap / Solaris

```


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
# kopt=root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f661d69d-f989-4d2f-9290-ec2a34e31593

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by TheLastAlive on 2009-06-11
bump

---

### Post by merlinus on 2009-06-11
Hi.  Do you have more than one hdd?  I am asking because sudo fdisk -l is only showing sdb1-5, and not sda at all.

In any event, grub is looking for windows on sda1, so the entry in menu.lst should be changed from:

title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

to 
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1

Try this and see if it works.

If you indeed have two hdds, then we may have to add a map statement as well.

---

### Post by synapsys on 2009-06-11
Try hitting f8 after selecting windows for boot up and choose to 'disable automatic restart on error' option or whatever it's called. This way you can view the blue screen error and write down what it says. You can google the error or post it here, without that it's a little hard to diagnose. There are only about 8 million different reasons why winblows will give you a blue screen of death.

---

### Post by nacho32 on 2009-06-11
can you even boot windows in safe mode? f-5 key press a bunch of times after choosing windows. Windows repair is pretty much a joke never use that option. Sounds like the problem is a corrupt windows system installing a game should have no matter on this. I would reinstall windows fresh not repair,

---

### Post by synapsys on 2009-06-11
Oh... missed that... merlinus is right there is no sda and sdb is only showing up as 100.2 GB. TheLastAlive said they had a terabyte drive.....

By the way... what game is it? maybe you don't need windows at all....

---

### Post by TheLastAlive on 2009-06-11
I do have more then one HDD, three to be exact, but all the information was put onto the terabyte drive.

the first one is my terabyte SATA drive, the second one is my 100 gigabyte IDE drive, and the third one is my 168 gigabyte (I think) IDE drive.  I normally never have the lesser two plugged in.

and its immposible to reinstall windows because the windows bootdisk can't recognize my terabyte drive any more for some reason.  and I assume that's what the error is when I boot.

and no I can't boot windows in safe mode.

and I know which games have linux support.  heh heh, ID Software is cool..

---

### Post by merlinus on 2009-06-11
Again, sudo fdisk -l is only showing sdb.  Are you using all three hdds, and if so, what is the booting order?

Also, you say the the 1T hdd has all the data.  Does this mean it contains the oses as well, or are they both on sdb, as indicated in the fdisk command?

---

### Post by TheLastAlive on 2009-06-11
Both operating systems are on separate partitions on the one terabyte drive.

And the terabyte is the master HDD.

and I unplugged the 100 gigabyte drive as it doesn't have anything on it and it was just complicating the situation.  I updated the sudo fdisk -l output after I did this.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98a398a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26113   209752641    7  HPFS/NTFS
/dev/sda2           26114      121601   767007360    5  Extended
/dev/sda5           26114      120662   759464811   83  Linux
/dev/sda6          120663      121601     7542486   82  Linux swap / Solaris

```

---

### Post by merlinus on 2009-06-11
Since sudo fdisk -l is not showing that hdd, then clearly something is amiss.  Where did you run that command from?

You can try booting with the live cd, and then open a terminal and run it again.

You also might try removing the other two hdds, and run from the 1T.

---

### Post by colau on 2009-06-11
> **TheLastAlive said:**
> Both operating systems are on separate partitions on the one terabyte drive.

And the terabyte is the master HDD.

and I unplugged the 100 gigabyte drive as it doesn't have anything on it and it was just complicating the situation.  I updated the sudo fdisk -l output after I did this.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98a398a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26113   209752641    7  HPFS/NTFS
/dev/sda2           26114      121601   767007360    5  Extended
/dev/sda5           26114      120662   759464811   83  Linux
/dev/sda6          120663      121601     7542486   82  Linux swap / Solaris

```

With the ubuntu live cd 
```

sudo fdisk -l

```
See what happens.

---

### Post by TheLastAlive on 2009-06-11
what do you mean its not showing the HDD?  Its showing the 1TB HDD that windows is located on.

---

### Post by colau on 2009-06-11
> **TheLastAlive said:**
> what do you mean its not showing the HDD?  Its showing the 1TB HDD that windows is located on.
Boot with ubuntu 9.04 live cd.
From terminal
```

sudo fdisk -l

```

---

### Post by TheLastAlive on 2009-06-11
I booted with the ubuntu bootdisk, and executed the command.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98a398a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26113   209752641    7  HPFS/NTFS
/dev/sda2           26114      121601   767007360    5  Extended
/dev/sda5           26114      120662   759464811   83  Linux
/dev/sda6          120663      121601     7542486   82  Linux swap / Solaris
```

The exact same output was outputed.

---

### Post by merlinus on 2009-06-12
Post results of:

```

cat /boot/grub/menu.lst

```

with only sda (1T hdd) mounted.  That will hopefully give info about grub and the bootup choices.

---

### Post by TheLastAlive on 2009-06-12
the results of sudo cat /boot/grub/menu.lst
(unless you meant to also do that after booting off the bootdisk)

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
# kopt=root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f661d69d-f989-4d2f-9290-ec2a34e31593

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f661d69d-f989-4d2f-9290-ec2a34e31593 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f661d69d-f989-4d2f-9290-ec2a34e31593
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by merlinus on 2009-06-12
At this point, it would seem that something is wrong with your xp install on sda1.  If your xp disk refuses to work, what about the version that is on one of your other hdds?

---

### Post by TheLastAlive on 2009-06-12
only the one version.  The problem is, if the XP install disk can't detect my drive, I can't even reinstall XP.

---

### Post by merlinus on 2009-06-12
OK.  Understood.  I wonder if xp is capable of recognizing TB hdds?

You might try supergrub to boot xp, but if the installation is corrupted, it won't be of any use.  Probably worth a try...

There is also an outside chance that your xp install disk is corrupted.  Perhaps you can borrow one from a friend to try?

Failing that, windows 7 seems to be already available.

---

### Post by TheLastAlive on 2009-06-12
well it installed the first time.  I think I'm just going to give up, thanks for your help.  I'll figure it out.

---

