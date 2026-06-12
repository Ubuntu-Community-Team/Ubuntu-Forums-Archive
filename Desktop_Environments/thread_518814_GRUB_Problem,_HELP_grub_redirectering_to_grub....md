---
title: "GRUB Problem, HELP grub redirectering to grub..."
date: 2007-08-06
forum: Desktop Environments
---

### Post by reflexion on 2007-08-06
I need Help,

I have WinXp on my first hard drive (sata 100gb) and ubuntu on my usb hard drive (ide 160gb).

When I installed ubunutu, grub installed itself on the removable hd (160gb), so that when I dont have my usb, I cannot boot into windows.

So I tryed to fix it by reinstalling grub on my windows partition with the following command:

sudo grub-install /dev/sda1

this was a BIG mistake.

When I rebooted, I wasnt able to load to windows anymore. When I select Windows, it says :

Grub loading...
Stage 2

and redirect to grub.


I tryed reselecting windows, same problem. But ubuntu works. 
[B]
So I did the fixmbr thing with my windows cd, it didnt changed anhything....[/B]


Help please!!

---

### Post by misconfiguration on 2007-08-06
It seems as if GRUB isn't installed on the MBR
GRUB>grub-install /dev/sda1
GRUB>root (hd0,0)

You will need to do this at the grub prompt, if you can get that far, generally you can edit this information VIA grub interface.

You may need to boot into recovery mode with a boot disk.

---

### Post by reflexion on 2007-08-06
thank you for your fast response,

I need to do this where: when I reboot my computer and hit c at grub prompt?

---

### Post by misconfiguration on 2007-08-06
Press 'i' to interrupt the boot process.

I believe it is C to edit configuration I may be wrong. You just need to get to the GRUB> prompt, after that's finished you should be golden. 

Post back if I'm not clear enough, I'll be glad to help.

---

### Post by reflexion on 2007-08-06
I just rebooted my computer, hit c and got in the grub prompt

I hit grub-install /dev/sda1 and it told me that it was not a command

So I looked for the available commands and entered "install /dev/sda1"

but it responded : "error 15 file not found"

---

### Post by reflexion on 2007-08-06
If it can help :

heres the content of /boot/grub/menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 ro single
initrd		/boot/initrd.img-2.6.20-16-generic


title		Ubuntu, memtest86+
root		(hd1,2)
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

```


here's the output for "sudo fdisk-I"

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12160    97675168+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14097   113226120    f  W95 Ext'd (LBA)
/dev/sdb2           14098       14219      979965   82  Linux swap / Solaris
/dev/sdb3   *       14220       19237    40307085   83  Linux
/dev/sdb4           19238       19457     1767150   82  Linux swap / Solaris
/dev/sdb5               2       14097   113226088+   7  HPFS/NTFS

```


and here's the content for /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb4
UUID=0022b35f-b92f-43d6-bd73-43fae610884d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by reflexion on 2007-08-06
sorry to be that annoying, but I really need help fast!

---

### Post by misconfiguration on 2007-08-06
Sorry I was at lunch,

When you boot the machine you get the grub prompt, do you see your OS choice menu?

When you select XP nothing happens?

Do a fdsik /dev/sdb

press a

press 5 for partition number to set the bootable flag back to XP.

press w to save the partition info, exit fdisk.

Reboot.

---

### Post by reflexion on 2007-08-06
Yes, I do see winxp

here's what happens:

I boot my computer, its written Grub Loading stage 1.5

I go to the grub os selection, I can select ubuntu (which works) and I see XP.

When I hit XP, it writes : starting....

grub loading stage 2

and it gets me back to the os selection menu and I get the same options



Edit : I did what you suggest me, and it did not worked

---

### Post by merlinus on 2007-08-06
Post results of these terminal commands:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by reflexion on 2007-08-06
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12160    97675168+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14097   113226120    f  W95 Ext'd (LBA)
/dev/sdb2           14098       14219      979965   82  Linux swap / Solaris
/dev/sdb3   *       14220       19237    40307085   83  Linux
/dev/sdb4           19238       19457     1767150   82  Linux swap / Solaris
/dev/sdb5   *           2       14097   113226088+   7  HPFS/NTFS

```

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 ro single
initrd          /boot/initrd.img-2.6.20-16-generic


title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by merlinus on 2007-08-06
/boot/grub/menu.lst seems okay, but I notice there is no entry in /etc/fstab for your windows partition.

Perhaps that is the problem?  You might want to post it here again.

-merlin

---

### Post by reflexion on 2007-08-06
here it is, and thank you for your help, very appreciated

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb4
UUID=0022b35f-b92f-43d6-bd73-43fae610884d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by merlinus on 2007-08-06
As you can see, no listing for windows.

Here is excellent info:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by reflexion on 2007-08-06
I am reading this right now

---

### Post by reflexion on 2007-08-06
this tutorial does not seem to work, because I am not able to find the disk in my fstab settings

---

### Post by reflexion on 2007-08-06
using the ntfs loader from ubuntu, I managed to mount my hd. 

heres the fstab config file:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb3 :
UUID=0f6dcb79-b506-4772-bce5-12b8a417d213 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb4 :
UUID=0022b35f-b92f-43d6-bd73-43fae610884d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_CA.UTF-8 0 0

---

### Post by merlinus on 2007-08-06
OK.  Now what happens when you restart.

-merlin

---

### Post by reflexion on 2007-08-06
nothing more....

it seems that grub is install IN my windows partition and that when it comes to load windows, it loads grub....

is it possible?

---

### Post by Cr4ig on 2007-08-06
Have you tried changing your hard disk boot priority? It's a pain switching back and forth every time you switch Os's but if Grub's not working, then its probably the easiest way to get into Windows.

---

### Post by merlinus on 2007-08-06
Don't think so.

Try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).

-merlin

---

### Post by reflexion on 2007-08-06
yes Ive tryed, but it seems that grub is installed on the windows partition.

here's what Ill try:

I will unplug my usb drive, set my boot priority to my internal hard drive, insert my winxp cd and do a fixmbr.

Ill post back in 20 minutes or so

Edit : Ill first try what Merlin is suggesting


Edit 2: Ive done what merlin suggested, I will now reboot

---

### Post by reflexion on 2007-08-06
Merlin's solution didnt worked, I wiil now try the fixmbr thing

come back asap

---

### Post by reflexion on 2007-08-06
I think Im in deep trouble.....

first, it didnt worked,

second, when I did chkdsk, it said that the drive had unreperable errors.... wtf

---

### Post by merlinus on 2007-08-06
From where did you run chkdsk?  And did you add /f to it (fix errors).

-merlin

---

### Post by reflexion on 2007-08-06
i ran it with the xp cd and I did not do the /f thing

---

### Post by merlinus on 2007-08-06
Try again adding /f to the end of the chkdsk line, and see what happens.  If there are errors on the drive, that is why ubuntu will not boot to or mount it.

-merlin

---

### Post by reflexion on 2007-08-06
ok, im trying and coming back

---

### Post by reflexion on 2007-08-06
it told me that the drives contained unreapearable errors.............

again, wtf

help please

---

### Post by merlinus on 2007-08-06
The message says it all, no?  Hopefully you have backups of important data.

If not, you might try a disk recovery tool such as sys rescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

---

### Post by misconfiguration on 2007-08-06
Remember to toggle your bootable flag back to /dev/sda3 before you go an do anything drastic.

fdisk /dev/sda

a
partition number 3
w
exit fdisk

reboot

---

### Post by reflexion on 2007-08-06
ill do waht micon... said, but

how could this happen??

---

### Post by merlinus on 2007-08-06
Just like people, hard disks age, decay, and eventually die.  No particular reason.

Sad, but true....

-merlin

---

### Post by reflexion on 2007-08-06
????

this hd is 4 months old.....

I Highly suspect grub to have break my hd

---

### Post by merlinus on 2007-08-06
Software break a hard drive?  Don't think so....

And if grub is at fault, how many hundreds of thousands of linux users would be up-in-arms!!!!

Maybe you have a windows virus, or spyware.  And just because the drive is new does not mean anything.

I can understand your frustration, but don't start blaming ubuntu.

-merlin

---

### Post by reflexion on 2007-08-06
hahaha,

I managed to solve it.

Apparently, my hard disk was not seen as a NTFS. I think this can be because I tried to install grub on a ntfs system (?). By that, it may have "corrupted" the "NTFS" label.

So I put my xp cd and I tryed this command (in the repair cmd)

FIXBOOT

Guess what??

It fixed it all!!

It reinstalled the boot of windows and rearranged the NTFS "label"

alleluia!!!!

---

### Post by misconfiguration on 2007-08-06
I did notice the HPFS/NTFS label but Linux labels NTFS as that.. That's generally a label for HIDDEN NTFS, congratulations on fixing it mate!!!


:popcorn::popcorn:

---

### Post by reflexion on 2007-08-06
Well,

because my main programs and my main folders are on my windows system, this is good, but there is still a problem.

I cannot access my ubuntu!

First, I need to maually select the drive to boot from.

If I select the windows hd, it boots into windows normally,

If I select the ubuntu hd, it brings up the Grub interface.

But when I select the os in grub, it tells me No such file or directory!



Now, I think that I need to install grub with this command: sudo grub-install hd(linux) ?

but I am VERY affraid that my today's peripeties comes back.

---

### Post by jps67 on 2007-11-07
Well, clearly I'm a year too late, but to future searchers, the problem is probably that the partition's boot sector was overwritten by grub.  This can be done usually by typing "grub-install /dev/hda1" when what was meant was "grub-install /dev/hda" but I got this problem when upgraded from 7.8 to 7.9 Feisty.  WTF?

The solution is to run your (R)ecovery console from your XP Installation CD-ROM, and use the FIXBOOT.exe command, or a program like "DIY DataRecovery DiskPatch" to replace the 512-byte boot sector at the beginning of the partition that got blown away,

---

### Post by Nate.askins on 2007-12-06
here's my story

wanted to install to portable harddrive so i could boot from it.

i had it connected to my laptop during installation, so installed through laptop

laptop, which runs windows, now tries to load GRUB but i get error code 21.

cannot do anything form that point. 

suggestions?  anyway to install just grub and not all of ubuntu?

---

### Post by meierfra on 2007-12-06
Are you getting error 21 even if your portable drive is connected?


Case 1)   You can boot into ubuntu when your portable drive is connected. 

Then just click on  DualTwo in my signatures. If you need help adjusting the numbers, open a terminal (Applications->Accessories->Terminal) and post the output of 

```
sudo fdisk -l
```
and 

```
cat /boot/grub.menu.lst
```
(both "l" are lowercase L)


Case 2)  You cannot boot into ubuntu.

In this case we will first have to sort out what went wrong. Connect the portable drive and boot from the Ubuntu LiveCD
Open a terminal and post the output of "sudo fdisk -l"
If you are able to access your Ubuntu partition on the portable drive (you might have an icon on the desktop, or look in Places->Computer), try to find the file /boot/grub/menu.lst and post its content

---

