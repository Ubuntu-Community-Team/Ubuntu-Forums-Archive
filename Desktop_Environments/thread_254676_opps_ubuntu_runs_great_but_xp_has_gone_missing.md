---
title: "opps ubuntu runs great but xp has gone missing"
date: 2006-09-10
forum: Desktop Environments
---

### Post by oswaldkelso on 2006-09-10
Hi all I just helped my mate install dapper evey thing went fine and I installed exactly as I did on my other friends panasonic toughbook. Letting gparted do all the hard work. His runs fine and duel boots, but this bell packard ran disk recovery and want to do a clean install. If I try and recover I get "run time error 53" Please be aware this is only the second pc I've ever touched because I use a mac so know very little about windows.

Help greatly appreciated beford his misses kills us lol


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 784 6291456 1b Hidden W95 FAT32
/dev/hda2 785 16362 125130285 7 HPFS/NTFS
/dev/hda3 16363 24038 61657470 83 Linux
/dev/hda4 24039 24321 2273197+ 5 Extended
/dev/hda5 24039 24321 2273166 82 Linux swap / Solaris
baztard@baztard-desktop:~$

---

### Post by confused57 on 2006-09-10
It looks like you're booting into the HP utilites partition(hd0,0), instead of the Windows partition(hd0,1).
   Please post the output of:
```
cat /boot/grub/menu.lst
```
or at least post the Windows entry

If it's showing root (hd0,0), you might want to change it to root (hd0,1), you may also need to change the kernel line to point to hda2.
  You can also test it temporarily by highlighting the Windows entry in the grub menu at startup, press "e" for edit, then change the entries as I've suggested above and see if it boots Windows...if it does, you can make the changes permanent in menu.lst.

---

### Post by oswaldkelso on 2006-09-11
Hi thanks for getting back. Here is the output.

baztard@baztard-desktop:~$ cat /boot/grub/menu.lst
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

baztard@baztard-desktop:~$

---

### Post by BoneKracker on 2006-09-11
Just to follow through for confused, in case you're waiting before trying his suggestion.  The rest of menu.lst looks fine to me.

Try changing this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```
To this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows NT/2000/XP (loader)
root (hd0,[COLOR="Red"]1[/COLOR])
savedefault
makeactive
chainloader +1
```

You might also try "rootnoverify" instead of "root".

---

### Post by oswaldkelso on 2006-09-11
Hi this may sound silly but how do I replace it I can't delete or paste over the existing file? do I duplicate it with a text file of the same name?

---

### Post by anllogui on 2006-09-11
Make: 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

And edit the file with an editor like "vi" or "emacs". Change only the number marked on red by BoneKracker.

So simply is Linux!

---

### Post by oswaldkelso on 2006-09-11
thankyou I'll down load one now which is the best? LOL

---

### Post by oswaldkelso on 2006-09-11
I ran that command in the terminal entered password but got no file? emacs also said no file but I can see it in the directory? and open it and but not edit it? I think emac may have crashed as it would not quit.

---

### Post by anllogui on 2006-09-11
The command:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

is for making a backup of the file. Then you should edit the file:

/boot/grub/menu.lst

whith root permissions, and change what has commented BoneKracker.

Then reboot and try to enter in the windows partition.

And be carefull with this file!! If you change what you shouldn't change, it's possible that you cannot enter in any partition!

---

### Post by rogier.de.groot on 2006-09-11
I'd do this:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo vi /boot/grub/menu.lst
press insert key
move cursor to hd(0,0) part, modify to hd(0,1)
press escape key, type ":wq"
reboot
(sorry for the verbosity, but I don't know if you're used to working with vi)

---

### Post by oswaldkelso on 2006-09-11
Thats fine I've never been a command line person so know nothing almost!!!! 
Does this look ok

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo [COLOR="Red"]emacs[/COLOR] /boot/grub/menu.lst
press insert key
move cursor to hd(0,0) part, modify to hd(0,1)
press escape key, type ":wq"
reboot


I dont know if vi is on the system and could not find it in synaptic so installed emacs

Have entered the above.

up to :wq


Do I need to save first or just close and reboot 

Sorry for being so cautious  but the CL is not my friend, YET

---

### Post by nikhilk on 2006-09-11
There was no nedd of installing emacs, you could have just used nano.

> **oswaldkelso said:**
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo [COLOR="Red"]emacs[/COLOR] /boot/grub/menu.lst
press insert key
move cursor to hd(0,0) part, modify to hd(0,1)
press escape key, type ":wq"
reboot


After typing emacs /boot/grub/menu.lst

1. Do not press the insert key.

2. do
   Ctrl+X followed by Ctrl+S
   to save the file and then

3. do
   Ctrl+X followed by Ctrl+C
   to exit emacs

---

### Post by oswaldkelso on 2006-09-11
I did not know which was the insert key so I just deleted the 0 and typed in the 1

the file looks like this


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows NT/2000/XP (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

so ctrl+s and exit emacs and restart correct?

---

### Post by nikhilk on 2006-09-11
I guess that should do it.
All the best.

---

### Post by oswaldkelso on 2006-09-11
> **nikhilk said:**
> I guess that should do it.
All the best.

Thankyou all fingers crossed :)

---

### Post by BoneKracker on 2006-09-11
Sorry - was away.

Yeah, ubuntu comes with nano already installed.  It's a lot easier to figure out than vi or emacs.

Let us know if this solved your problem.

---

### Post by Najand on 2006-09-11
UBUNTU comes with vim (Vi IMproved) already installed too.

---

### Post by oswaldkelso on 2006-09-11
Well no go I'm afraid when it loads up it list several forms of ubuntu and other operating systems but this was blank.

under the previous settings it said something about xp

I selected other operating system anyway to see if it would boot but nothing so rebooted into ubuntu

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 784 6291456 1b Hidden W95 FAT32 [COLOR="Red"]is this the built in xp restore[/COLOR]
/dev/hda2 785 16362 125130285 7 HPFS/NTFS [COLOR="Red"]is this the xp partition? if so should I edit the menu.lst to hda2?[/COLOR]
/dev/hda3 16363 24038 61657470 83 Linux
/dev/hda4 24039 24321 2273197+ 5 Extended
/dev/hda5 24039 24321 2273166 82 Linux swap / Solaris
baztard@baztard-desktop:~$

any suggestions?

---

### Post by arkangel on 2006-09-11
open a terminal  run  
sudo cfdisk

and attach teh screenshot

---

### Post by oswaldkelso on 2006-09-11
Here

---

### Post by nikhilk on 2006-09-11
Ok which version of Windows are you using?
Is the Windows partition formatted as NTFS?

---

### Post by oswaldkelso on 2006-09-11
Sorry for the slow response I missed the page change duh!!

windows xp and i assume its on the ntfs partiton

I suspect the first is the partitions are the restore xp, ntfs is xp the rest ubuntu.

I take it I should reinstate the original menu.lst file with the "old" version first? (what was hda0.0)

or change it to hda2?

---

### Post by Big_J on 2006-09-11
I didn't read all the posts so sorry if this has been said or is useless...

But shouldn't grub show two windows xp entrees?
One for "d" (factory installed fat partition {recovery}) and one for "c" which is where windows is!

There should be two windows xp entrees in the grub loader, one for windows xp and one that says windows xp but goes to the recovery screen

---

### Post by nikhilk on 2006-09-11
Let the "old" version be. Directly change the menu.lst file and change it to hda2.
That seems to be the solution.
Keep us posted.

---

### Post by oswaldkelso on 2006-09-11
back in 10 min on phone

---

### Post by oswaldkelso on 2006-09-11
I changed the menu.lst to hda.0.2 but it still failed to show xp? I got the same options as before

other operating system blank? 

I'll change the menu.lst to hda.0.0 and see if it can see the xp recovery partition

---

### Post by oswaldkelso on 2006-09-11
Well no go on hda0.0 either so I think it may be hosed?  if I press e to edit the start up selection I only get root to choose from all this before any os is started.

when I run cfdisk I can select using the arrow keys the different partitions

at the momment hda is bootable

it is possable to select the other drives using the arrow keys and make them bootable with the Y/N options? 

if this failed would it be possible to reboot ubuntu to change the settings again or would I be even further up the stream without a paddle

edit

I just checked the fdisk list all the original partitions seem there it also saw my usb drive so maybe there is hope yet?

---

### Post by confused57 on 2006-09-11
Looks like you're getting plenty of good advice, and it looks like your xp is on partition #2...you'll need to edit your menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Copy & paste one line at a time, hit enter after each line is pasted.

Add(copy & paste) the following entry at the very end of the menu.lst file:

```
title           Windows XP
root            (hd0,1)
makeactive
chainloader   +1
```

This "should" boot your windows on hda2.  It should be listed as the last OS entry in your grub menu at startup.

---

### Post by oswaldkelso on 2006-09-11
Thankyou. I have to sleep now as I have work in 7 hours I will go through it when I get back, 14 hours time then I'll have all day to try and fix it. If push comes to shove I'll borrow xp install disks and start afresh. 

Thanks to all who posted, I've learnt more about the linux CL (powerfull or what!) , and Windows (dum as "$%&*) ok maybe I'm dumber LOL in the last 24 hours than in the last 5 years!!!

All thats needed is a nice screen casting app to save my dyslexic head and two typing fingers :)   good night and I'll try again tomorrow

---

### Post by oswaldkelso on 2006-09-12
Tried, failed to see xp. 

to recap

The menu.lst is set to

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/COLOR]

menu.lst.old the original backup is below. 

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

This as is identical to menu.lst_backup 

I can compare the settings and they are identical.

 I have also tried

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1[/COLOR]

Its as if the xp part has lost something so maybe I need to repoint from the windows side (scary thought for a mac user) I'll have a surf on to some xp boards and see what I can come up with.

I think shall reset it to the original hd0,0

cheers

---

### Post by rogier.de.groot on 2006-09-12
What happens when trying to boot XP from hd(0,1) ?? Does it say something about not finding NTLDR (the windows NT bootLoaDeR) ?? Do you get some sort of boot menu when booting from hd(0,0) ??

---

### Post by oswaldkelso on 2006-09-12
Hi no it says nothing about NTLDR all it says is:

ubuntu,kernel2.6.15-26-386
ubuntu,kernel2.6.15-26-386 recovery mode
ubuntu,kernel2.6.15-26-386
ubuntu,kernel2.6.15-26-386 recovery mode
ubuntu,memtest86+
other operating systems

Before I changed the menu.lst file under other operating systems it had xp recovery options. The only option avalible was a clean reinstall. Now no matter what the menu.lst is set to it does not show any xp stuff. Even though when I run fdisk I can see the partitions (see previous screen snap)

To be honest if it was my pc I would not miss xp but my mates misses WILL

---

### Post by rogier.de.groot on 2006-09-12
If the grub menu doesn't show any XP thingies there are probably no entries for XP in menu.lst. Maybe do "sudo cp /boot/grub/menu.lst.old /boot/grub/menu.lst" to put back the copy of the original. Use "sudo gedit /boot/grub/menu.lst" to edit, find the XP entry, copy the whole entry and edit that one to "hd(0,1)" so you have boot entries for both the restore disk & the original winXP disk. And tell us what output you get when trying to boot both...
Also, if you want to restore Window, I suggest installing to a different folder (C:\WINTEMP). This will restore the windows bootloader, and hopefully let you boot the original windows install (and you can then remove C:\WINTEMP).

---

### Post by oswaldkelso on 2006-09-12
> **rogier.de.groot said:**
> If the grub menu doesn't show any XP thingies there are probably no entries for XP in menu.lst. Maybe do "sudo cp /boot/grub/menu.lst.old /boot/grub/menu.lst" to put back the copy of the original. Use "sudo gedit /boot/grub/menu.lst" to edit, find the XP entry, copy the whole entry and edit that one to "hd(0,1)" so you have boot entries for both the restore disk & the original winXP disk. And tell us what output you get when trying to boot both...


xp does show up in the menu.lst

> **rogier.de.groot said:**
> if you want to restore Window, I suggest installing to a different folder (C:\WINTEMP). This will restore the windows bootloader, and hopefully let you boot the original windows install (and you can then remove C:\WINTEMP).


Sorry but I dont know how to do any windows stuff this is only the second pc I've used for more than 20 mins in the last 8 years.

> **oswaldkelso said:**
> Tried, failed to see xp. 

to recap

The menu.lst is set to

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/COLOR]

menu.lst.old the original backup is below. 

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

This as is identical to menu.lst_backup 

I can compare the settings and they are identical.

 I have also tried

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1[/COLOR]

 
All 3 setting above have been tried ubuntu is set to boot on hd0,2 though I have not reinstated the menu,lst.old its been tried at those settings.

the thing that has changed is the fdisk read out the unreadable part was not there originally.

As you can see I could set the ntfs partition to boot?

                                  cfdisk 2.12r

                              Disk Drive: /dev/hda
                       Size: 200049647616 bytes, 200.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 24321

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   Hidden W95 FAT32                  6442.49*
                                      Unusable                             6.14*
    hda2        [COLOR="Red"]Boot [/COLOR]       Primary   NTFS             []             128133.42
    hda3                    Primary   Linux ext3                       63137.25
    hda5                    Logical   Linux swap / Solaris              2327.76






     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

but I am worried that it wont boot into any thing lol


Edit

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 784 6291456 1b Hidden W95 FAT32
/dev/hda2 785 16362 125130285 7 HPFS/NTFS
/dev/hda3 16363 24038 61657470 83 Linux
/dev/hda4 24039 24321 2273197+ 5 Extended
/dev/hda5 24039 24321 2273166 82 Linux swap / Solaris
baztard@baztard-desktop:~$


this is the disk before changing menu.lst as you can see some thing has changed.

In this state I had an option to do a clean reinstall of xp but not recover any of my mates (or more inportantly his misses) data

---

### Post by rogier.de.groot on 2006-09-12
Hmmm... the unusable part is probably just a minor piece of your harddrive that can't be used for a new partition, which is why it's labeled "unusable". As for making hda2 bootable, I wouldn't, since if it CAN be booted from, grub's chainloader would have done so... Or at least it damn well should have.
Can you still read files from both partitions from Ubuntu? If so, could you please find the boot.ini file in C:\ (the WinXP partition) and post it's contents?
At this point, I'd consider grabbing a WinXP install CD and trying to get it to install on C:\WINTEMP like I mentioned earlier, thus (hopefully) restoring the WinXP bootloader, and letting you boot XP. If that works, grub can always be reinstalled without messing up your Ubuntu setup (if you've got anything important on it, that is, if it's just a new installation I'd simply reinstall Ubuntu).
If you don't happen to have a WinXP install CD, a Win2K CD would probably (not sure on this) work too.

PS. If you can still read the WinXP partition, it might be a good idea to backup some of the missus' data to another harddrive or something, if at al possible, since Windows might just decide to kill your old partition during install. Not that it *should* unless you tell it to ofcourse, but hey, it's microsoft...

---

### Post by oswaldkelso on 2006-09-12
As for making hda2 bootable, I did try but it booted into ubuntu as per usuall. I noticed when ubuntu started to boot it flashed up hd0.2
 
I dont know if I Can you still read files from both partitions from Ubuntu? 

This pc had xp pre installed so he has no xp install disks. I'm sure I can get hold of some thought in a few hours.

If I understand you correctly I could reinstate the xp boot setting from an xp install disk and hopefully recover the data.? 

If not I may as well do a clean install. If it comes to that I could partition the drive in my mac 50/50 xp and free space and just install ubuntu to the free space. 

I'll ring around and see if I can get a copy of xp

---

### Post by rogier.de.groot on 2006-09-12
Come to think of it, just booting from the WinXP CD, getting into the recovery console (press "R" at some point, NOT the automated recovery thing which doesn't work) and running CHKDSK (to check the NTFS filesystem for errors), FIXBOOT (to fix the bootloader) and FIXMBR (to fix the master boot record) should pretty much do the trick too. You can skip the CHKDSK part really, if you're sure the filesystem hasn't been messed with, and it's by far the slowest part of the process.
After all that, WinXP should boot again like it's the only OS on the system.
As for reading the Windows partitions from Ubuntu, did you specify any mountpoints for them during the partitioning part of the installation? If you did, those partitions should be mounted at boot and be in the "My Computer" thingy. If not you should be able to mount them, with something like the "Disks" tool in the Administration menu.

---

### Post by oswaldkelso on 2006-09-13
Hi I borrowed some xp disks and my mate loaded it up to the "R" part to see what we would get. If it works great if not partition and start again. After reading the xp licence terms for OEM products I find it a wonder why anyone would want to pay for xp? though.

I'll make sure the hd0,0 is reset and try it in a few hours when my mate comes off work (he's a bit more xp savee than me) We'll see how it goes, ubuntus been running a treat. (I even managed to listen to pay to listen commentary of my football (soccer) team for free :D . I guess didnt key in the linux factor.

I'm even thinking of getting a x86 as a lappy in stead of my usual mac (xp did'nt even enter my head) though I feel ubuntu could learn a few things from osx in terms of ease of use and intergration "Expos'e" is so slick. Easy I suppose when you only have limited hardware to support.

Anyway cheers to all that have tried to help I'll see what happens latter on

---

### Post by oswaldkelso on 2006-09-13
Hi all my mate has come around and he just said the his OEM version of xp had "lost" it's restore point! and that he had not been able to restore from xp. I suspect this is why the option was not there when we rebooted, only the option to do a clean restore.

 He also said his mrs had had a lot of her Baby pic's on the partition so I thought I'd post first to see if this new info helps at all. 

cheers

---

### Post by oswaldkelso on 2006-09-13
Well we ran the xp install disk and pressed "R" for recovery it stopped at a flashing C:   

Waiting for some command? with the only other option to EXIT. 

We did EXIT as we were not sure if it had done the repair but it had not, hench we need to no what to type at the C: prompt 

rogier.de.groot said some thing about the the boot.ini file in C:\ (the WinXP partition) and posting it's contents? but I dont have a foggiest how to get it lol

---

### Post by BoneKracker on 2006-09-14
You can type ? or help or something to get a list of commands you can use.

Did you do a backup of the XP before running the ubuntu install?

---

### Post by rogier.de.groot on 2006-09-14
Most XP recovery console sessions say something like
1: C:\WINDOWS
and then give you a prompt where you can type "1" to start recovering the windows install, or just enter to exit.
After typing "1" it will ask you for the Administrator password.
When you get the regular shell-prompt you just type
FIXBOOT C: <enter>
FIXMBR <enter>
or something similar.

As for reading c:\boot.ini from you windows partition, you just have to mount it. Open a console, type "sudo mount" to see if /dev/hda2 is allready mounted (my dual boot install automagically put my NTFS partitions in /media/hda1 & /media/hdb2) if so you should be able to get to your windows files with any filebrowser.
If they're not mounted do something like "sudo mkdir /media/winxp && sudo mount -t ntfs /dev/hda2 /media/winxp" and launch your filebrowser with "sudo nautilus" since you won't get any permission problems.

---

### Post by oswaldkelso on 2006-09-16
> **BoneKracker said:**
> You can type ? or help or something to get a list of commands you can use.

Did you do a backup of the XP before running the ubuntu install?

It was an OEM with xp builtin with no xp disks

---

### Post by oswaldkelso on 2006-09-16
Thanks for trying but my mate or rather his misses need the pc back so we ended up reinstalling xp from a disk.

We ran the xp repair option "R" but it failed to repair its self. We initalised the xp part of the hard drive and started over.

I'm sure we could have recoverd the data but most had been removed prior to installing ubuntu (just his misses pics which we knew nothing of :-\" )

I am sure that the instalation failed because of an error in the xp part of the drive as my mate said xp "lost" it's restore point! and that he had not been able to restore his data with xp prior to our attemping to install Ubuntu. I suspect that is way it failed though I don't know enough to be sure. 

I still have to setup ubuntu to appear as a start up option but will try to get it done next week.

On a positive front my friend with the Panasonic wants to install Ubuntu on his other laptop and if we can get his fancy printer to work I think he will be pure Ubuntu.

Anyway thanks again to all who offered help and advice.

---

