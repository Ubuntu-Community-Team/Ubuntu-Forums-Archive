---
title: "Dual booting windows problem"
date: 2005-12-03
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-12-03
Hey,

I'm trying to dual boot windows 2000 and Ubuntu breezy.

I installed windows first (ntfs) on an 80 gig partition.

I then installed ubuntu breezy on an 80 gig partition.

Ubuntu breezy boots fine.

When I try and boot windows I get the error:

Stop:  Inaccessible_boot_device

Any ideas?

Thanks.

Aaron

---

### Post by aysiu on 2005-12-03
Did you install Grub to the MBR?

---

### Post by 11hjpphty76lkjj on 2005-12-04
Yes, I believe so, I did the default action.

Thanks.

Aaron

---

### Post by aysiu on 2005-12-04
[QUOTE=kalosaurusrex]
When I try and boot windows I get the error:

Stop:  Inaccessible_boot_device[/QUOTE] Are you able to boot to Ubuntu? If so, can you post the output of these terminal commands? ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by BLTicklemonster on 2005-12-04
I installed ubuntu on a slaved drive with xp in master.

Yes, I installed grub on the master. And no I can't boot to windows, either. Kinda frustrating that ubuntu does that. BUT, I'm giving it another shot.

Here's my stuff:

```
bill@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9634    77385073+  83  Linux
/dev/hdb2            9635       10011     3028252+   5  Extended
/dev/hdb5            9635       10011     3028221   82  Linux swap / Solaris
bill@ubuntu:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

bill@ubuntu:~$

```

---

### Post by GrumpyBob on 2005-12-04
This happened to me on my work PC.  Interestingly, I could boot Win2k at first, it was the third boot that failed with an inaccessible boot device error.

The bad news is that I could not rescue the situation.  I tried the Win2k rescue/repair console, but fixboot and fixmbr did not sort the situation out.

I could still mount the windows drive on Ubuntu, so I copied all the data and formatted the drive to reinstall Windows (this time WinXP).

Robert

---

### Post by BLTicklemonster on 2005-12-04
I can't even see the other drive from here. I found a way once before where you could mount the other drive, but I can't find the link.

---

### Post by aysiu on 2005-12-04
[QUOTE=BLTicklemonster]I can't even see the other drive from here. I found a way once before where you could mount the other drive, but I can't find the link.[/QUOTE] [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by aysiu on 2005-12-04
[QUOTE=BLTicklemonster]
Yes, I installed grub on the master. And no I can't boot to windows, either. Kinda frustrating that ubuntu does that. BUT, I'm giving it another shot.[/quote] Your Grub menu looks good to me. What error do you get when you try to boot to Windows? I'm wondering if it's a two-separate-hard-drives problem, as it seems both you and kalosaurusrex have that setup (two hard drives).

I'm dual booting on one hard drive that's partitioned, and it works just fine.

---

### Post by tomwell on 2005-12-04
I have 2 hard drives and i get no probs... Ubuntu on slave and Windows on primary... 

I even access a fat32 partition on my primary drive from ubuntu...

Peace

Tom

ps: Aysu great new Avatar... ;o)

---

### Post by 11hjpphty76lkjj on 2005-12-04
Sorry for the delay..(I was sleepin')

I have one hard drive partitioned to about 80 gigs for each OS.  I installed W2K first, and it booted fine.  Then I installed Ubuntu, and Ubuntu boots fine, but W2K does not.  They are both clean installs, so I don't have any data I need to recovery.  I only have W2K or I would try XP.  But I don't feel like spending any more money on microsoft.  I only want to dual boot so that I can game and such.

I don't know where to go from here, perhaps re-install W2k, then Re-install the ubuntu grub?

Thanks again.   Glad to see that I'm not the only one at least!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-12-04
By the way, here is my fdisk and menu.list:
```

kalosaurusrex@coreprime:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/hda2           10200       19208    72364792+  83  Linux
/dev/hda3           19209       19457     2000092+  82  Linux swap / Solaris
kalosaurusrex@coreprime:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory
kalosaurusrex@coreprime:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-10-k7
boot

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1




```

---

### Post by 11hjpphty76lkjj on 2005-12-04
So if I'm going to re-install Windows, which seems to be the next course of action, how do I not mess up ubuntu?  I just got it all setup darn it.  I know I should have checked the windows thing before hand, alas... will (i'm assuming it will) windows mess up the GRUB? and if so how do I re-install it?  install cd, expert, install grub?

Aaron

---

### Post by BLTicklemonster on 2005-12-04
[QUOTE=aysiu][http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)[/QUOTE]
Thanks, got it mounted. I don't see anything that is dated at the time I did the installation in my xp root directory. Didn't grub write somthing to it?

Here's my boot.ini:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

---

### Post by BLTicklemonster on 2005-12-04
[QUOTE=tomwell]I have 2 hard drives and i get no probs... Ubuntu on slave and Windows on primary... 

I even access a fat32 partition on my primary drive from ubuntu...

Peace

Tom

ps: Aysu great new Avatar... ;o)[/QUOTE]


Then would you please

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

and copy and paste the results here, please so we can compare them?

---

### Post by BLTicklemonster on 2005-12-04
Just rebooted, and here's what it says:

```
Booting 'Microsoft Windows XP Professional'

root (hd 0,0)
File system type unknown, partition type 0x7

save default
make active
chainloader +1
```

Typed by hand, so it may be off a wee bit, but that's what it says.

---

### Post by tomwell on 2005-12-04
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2   *         524        7271    54203310    7  HPFS/NTFS
/dev/hda3            7272        9729    19743885    c  W95 FAT32 (LBA)

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14759   118551636   83  Linux
/dev/hdb2           14760       14946     1502077+   5  Extended
/dev/hdb5           14760       14946     1502046   82  Linux swap / Solaris
``` ```

tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

#title          Ubuntu, kernel 2.6.12-9-386
#root           (hd1,0)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root           (hd1,0)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
#initrd         /boot/initrd.img-2.6.12-9-386
#boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Hope that helps guys...

Peace 

Tom

---

### Post by BLTicklemonster on 2005-12-04
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2   *         524        7271    54203310    7  HPFS/NTFS
/dev/hda3            7272        9729    19743885    c  W95 FAT32 (LBA)

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14759   118551636   83  Linux
/dev/hdb2           14760       14946     1502077+   5  Extended
/dev/hdb5           14760       14946     1502046   82  Linux swap / Solaris
tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

#title          Ubuntu, kernel 2.6.12-9-386
#root           (hd1,0)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root           (hd1,0)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
#initrd         /boot/initrd.img-2.6.12-9-386
#boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

...whew.

gotta learn to hit that #  thing up there when you put stuff like that in there, you out get :) all over the place, lol.

---

### Post by tomwell on 2005-12-04
[QUOTE=BLTicklemonster]...whew.

gotta learn to hit that #  thing up there when you put stuff like that in there, you out get :) all over the place, lol.[/QUOTE]


sorry?? what do you mean by that?? 

I hope its not too long but you did say to copy and paste all the output of the commands...LMAO!!!

Peace

Tom

---

### Post by BLTicklemonster on 2005-12-04
[QUOTE=tomwell]sorry?? what do you mean by that?? 

I hope its not too long but you did say to copy and paste all the output of the commands...LMAO!!!

Peace

Tom[/QUOTE]


In your post, this

tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

has these dudes :cool: 

But if you put a [ followed by the word code then ] at the beginning of a pasted script, then the same but with a / before the word code at the end

```
 [**code] [/**code]
```
(don't ask me how I got away with that, lol.

, it looks like this

```
tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
```

without the :cool:  dudes. See?

BUT, thank you for posting! I don't see anything that would make yours work, and mine not work. Maybe the brain can find it?

---

### Post by wellmt on 2005-12-04
Here is a method of using two hard drives, with Windows on one disk and Linux on the other. What I like about it is that I can reinstall Linux whilst leaving the Windows drive alone. Not sure if it will help you in this case but someone might find it useful.

1. Setup Windows on your primary hard drive as normal (if not already done)
2. Take out the Windows hard drive and set it as slave using jumpers and put back in to PC
3. Set your other drive to primary using Jumpers. Put into PC and install Ubuntu on it. Install GRUB as normal to the MBR of the linux drive.
4. Ubuntu will detect your Windows drive and add it to the boot menu - but the menu entry won't work as Windows expects to be the primary drive. It's easy to fix through, all you do is change the grub menu entry for windows.

$sudo gedit /boot/grub/menu.lst

Find the windows section in the file and add the bit in italics IIRC. This basically causes grub remap the secondary drive as primary and vice versa temporailly, allowing Windows to boot as normal. 


# Windows
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
[I]map		(hd0) (hd1)
map		(hd1) (hd0)[/I]
chainloader	+1

---

### Post by BLTicklemonster on 2005-12-04
And there's no way to edit anything at this point? With bunt as the slave and xp as the master already? I can redo ubuntu, I haven't spent that much effort on it, except setting up my logitech mouse was way more complicated this go around, and I thought I'd never get the ati video drivers set up right... but I can install ubuntu again if that's all it takes, and there's no way to edit anything with them already set up with xp/master, ubuntu/slave.

---

### Post by disk0bug on 2005-12-04
[QUOTE=aysiu]Your Grub menu looks good to me. What error do you get when you try to boot to Windows? I'm wondering if it's a two-separate-hard-drives problem, as it seems both you and kalosaurusrex have that setup (two hard drives).

I'm dual booting on one hard drive that's partitioned, and it works just fine.[/QUOTE]

I'm having the same problem but with Windows XP.  When I load XP, I got a blue screen saying "unmountable_boot_volume"

My grub looks like his and was installed on the MBR... but I'm running on only 1 disk.  I got WinXP on Partion 1 and Ubuntu on partition 2 (ext3).

How do I get my windows back?   :confused: 

BTW, I tried to installed 'lilo' instead but it doesn't work.  Grub is always there.

---

### Post by BLTicklemonster on 2005-12-05
[QUOTE=wellmt]Here is a method of using two hard drives, with Windows on one disk and Linux on the other. What I like about it is that I can reinstall Linux whilst leaving the Windows drive alone. Not sure if it will help you in this case but someone might find it useful.

1. Setup Windows on your primary hard drive as normal (if not already done)
2. Take out the Windows hard drive and set it as slave using jumpers and put back in to PC
3. Set your other drive to primary using Jumpers. Put into PC and install Ubuntu on it. Install GRUB as normal to the MBR of the linux drive.
4. Ubuntu will detect your Windows drive and add it to the boot menu - but the menu entry won't work as Windows expects to be the primary drive. It's easy to fix through, all you do is change the grub menu entry for windows.

$sudo gedit /boot/grub/menu.lst

Find the windows section in the file and add the bit in italics IIRC. This basically causes grub remap the secondary drive as primary and vice versa temporailly, allowing Windows to boot as normal. 


# Windows
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
[I]map		(hd0) (hd1)
map		(hd1) (hd0)[/I]
chainloader	+1[/QUOTE]



For the heck of it, I changed menu.lst to reflect your suggestion, and changed the drives, but did not install ubuntu, rather I changed every instance in menu.lst for the ubuntu drive from 

(0,0)
to
(1.0)

And windows will now boot. But, as you can imagine, ubuntu doesn't. But I see where this will work if ubuntu is loaded on the slave.

I think I'll do it, though I hate messing up everything I've done so far.

Thanks. Perhaps someone will find an angle from this point and post what to edit in ubuntu prior to switching that will let it work?

---

### Post by BLTicklemonster on 2005-12-05
Okay, that's too wierd. menu.lst still had the map changes...  how'd you do that wellmt?

Okay, so I guess I'm good to go now? Haven't rebooted to see what happens yet. Just upgraded, and installed the k7 kernel first off for a change. woot. Now for the ati drivers and logitech mouse settings. If I'm lucky, I'll get to pull my finger nails out first.


Thanks wellmt :cool:

---

### Post by tomwell on 2005-12-05
[QUOTE=BLTicklemonster]In your post, this

tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

has these dudes :cool: 

But if you put a [ followed by the word code then ] at the beginning of a pasted script, then the same but with a / before the word code at the end

```
 [**code] [/**code]
```
(don't ask me how I got away with that, lol.

, it looks like this

```
tom@tom-ubuntu:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
```

without the :cool:  dudes. See?

BUT, thank you for posting! I don't see anything that would make yours work, and mine not work. Maybe the brain can find it?[/QUOTE]

Obviously a site admin has edited my post so thank you very much, was about to do so when i saw your post this morning.... Now i know to use the code thingy when inputing a lot of text...

Sorry to all...

Peace

Tom

ps: the Dudes are cool though.. LOL

---

### Post by BLTicklemonster on 2005-12-05
Aysiu fixed it for you. No prob, just makes it easier. Now you know! muahaha

This is great to know the mapping trick, because I installed ubuntu on my son's machine with windows as slave, now I know how to make it dual boot.

---

### Post by wellmt on 2005-12-06
BLTicklemonster, thanks, glad to have helped :D

---

### Post by GrumpyBob on 2005-12-06
[QUOTE=disk0bug]I'm having the same problem but with Windows XP.  When I load XP, I got a blue screen saying "unmountable_boot_volume"

My grub looks like his and was installed on the MBR... but I'm running on only 1 disk.  I got WinXP on Partion 1 and Ubuntu on partition 2 (ext3).

How do I get my windows back?   :confused: 

BTW, I tried to installed 'lilo' instead but it doesn't work.  Grub is always there.[/QUOTE]

This happened to my work PC a week or two ago.  This was a Win2k machine I was setting up as a dual boot.  The windows boot was  fine the first time I tried it.  While using it for the second Win boot, it said it had found new drives and asked if I wanted to install drivers.  I declined.  The third attempt to boot Win2k failed with the inaccessible_boot_device error screen.  The windows partiton was fine as judged by my ability to mount it under Linux.

I couldn't find anything wrong with the grub setup.  I tried using the Win2k CD repair console.  Fixboot and Fixmbr did not solve the situation, despite the attentions of one of out IT dept.  In the end we copied across all my data, wiped the hard drive and did a clean install of WinXP.

I don't know if this is a factor, but the PC had one of those hidden partitions with system restore data on it.

Robert

---

### Post by BLTicklemonster on 2005-12-06
Window's system restore is nothing more than a meat locker for viruses and spyware. What good is restoring your system to infected status? I always kill restore in ME or XP.

---

### Post by jdamico on 2006-10-31
> **kalosaurusrex said:**
> Hey,
 
I'm trying to dual boot windows 2000 and Ubuntu breezy.
 
I installed windows first (ntfs) on an 80 gig partition.
 
I then installed ubuntu breezy on an 80 gig partition.
 
Ubuntu breezy boots fine.
 
When I try and boot windows I get the error:
 
Stop: Inaccessible_boot_device
 
Any ideas?
 
Thanks.
 
Aaron
 
*********************
 
Regarding STOP error 0x0000007B
INACCESSIBLE_BOOT_DEVICE
 
I had a similar problem as well, originally blaming it on GRUB, etc. I found it interesting that the boot process got so far along before failing. (The black and white win2k progress bar across the bottom of the screen finished and the logo screen popped up and that progress bar made it halfway through before failing.) How could I suddenly lose my boot device after I had already loaded a logo image from the disk? Certainly that was not in MBR!
 
Rewriting MBR didn't help anyhow.
 
Taking a hint from a user who resolved the problem by manually forcing his BIOS to LBA from AUTO, I attempted this with no success.
 
 

Along the same line, however, I finally applied the fix in the following article and so far it seems to be working.[INDENT][[FONT=Courier New]http://support.microsoft.com/kb/305098[/FONT]]("http://support.microsoft.com/kb/305098")[/INDENT]

The article is entitled: "48-Bit LBA Support for ATAPI Disk Drives in Windows 2000" In short, it requires using regedt32.exe to open the registry and add the following:[INDENT][FONT=Courier New][SIZE=2]To enable 48-bit LBA large-disk support in the registry: [/SIZE][/FONT][/INDENT][INDENT][FONT=Courier New][SIZE=2]1. [/SIZE][/FONT][FONT=Courier New][SIZE=2]Start Registry Editor (Regedt32.exe).[/SIZE][/FONT][/INDENT][INDENT][FONT=Courier New][SIZE=2]2. [/SIZE][/FONT][FONT=Courier New][SIZE=2]Locate and then click the following key in the registry: [/SIZE][/FONT][/INDENT][INDENT]**[FONT=Courier New][SIZE=2]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Atapi\Parameters[/SIZE][/FONT]**[/INDENT][INDENT][FONT=Courier New][SIZE=2]3. [/SIZE][/FONT][FONT=Courier New][SIZE=2]On the **Edit** menu, click **Add Value**, and then add the following registry value: [/SIZE][/FONT][/INDENT][INDENT][FONT=Courier New][SIZE=2]Value name: **EnableBigLba**[/SIZE][/FONT][/INDENT][INDENT][SIZE=2][FONT=Courier New]Data type: REG_DWORD[/FONT][/SIZE][/INDENT][INDENT][SIZE=2][FONT=Courier New]Value data: 0x1 [jdamico note: set checkbox to hexidecimal and just enter "1" on the line][/FONT][/SIZE][/INDENT][INDENT][FONT=Courier New][SIZE=2]4. [/SIZE][/FONT][FONT=Courier New][SIZE=2]Quit Registry Editor.[/SIZE][/FONT][/INDENT]The problem seems to occur on large hard drives (i.e. bigger than 137 GB) Mine is nominally 250 GB, with a 40 GB NTFS partition followed by my big Linux ext3 partition and a 2-ish GB swap partition.
 
Upon reboot it checked my disk and fixed some new "errors" and rebooted itself. So far I haven't detected any real damage, however. I loaded Ubuntu 6.10 RC and everything seems to be fine once again.
 
Not sure if it will help others, but it has eliminated my frustration---at least for the time being.
 
jdamico
 
PS When I say it resolved the problem, what I mean to say is that I blew away Linux and installed my Windows partition from a pre-linux install backup image. On its own it booted fine.
 
Then I made the changes described.
 
Then I re-loaded Ubuntu. In the past it would fail at that point. Now it continues to work. Unfortunately, however, I lost my original Linux installation which I had not yet backed up. (I was having trouble with Mondo-archive anyhow. This is a good excuse to start again.)

---

