---
title: "Error 17 with grub loader"
date: 2007-12-02
forum: Desktop Environments
---

### Post by haneya on 2007-12-02
hi guys 

i have a problem with the boot loader grub (error 17) i was trying to browse the ubuntu drive from windows xp and after restarting the computer i got this error what i have to do 
plz some one hlp me and give me a simple way cuz am beginner i linux and i dont want to format any thing thx

---

### Post by meierfra on 2007-12-02
I would first check whether your ubuntu partition is still intact. Boot from the Ubuntu LifeCD and try to access the ubuntu partition. You might  have  an icon on the Desktop.  If not   look  in Places->Computer.  

Also open a terminal (Application->Accessories->Terminal) and post the output of 

```
sudo fdisk  -l
```

---

### Post by njparton on 2007-12-02
Grub wasn't installed correctly or to the correct location.

Try installing with only 1 hard drive installed.  If you're trying to dual boot from the same hard drive that's different and post back if so.

---

### Post by haneya on 2007-12-02
ya my ubuntu still there in hd0,7

---

### Post by meierfra on 2007-12-02
> ya my ubuntu still there in hd0,7

More details please.

Could you access your files? 

 If yes, open the file /boot/grub/menu.lst  on the ubuntu partition  and post its content.

 Post the output of "sudo fdisk -l"

---

### Post by haneya on 2007-12-02
i installed windows xp first then i installed ubuntu so they was working perfectly but it seems i did some thing wrong

---

### Post by haneya on 2007-12-02
yes i can 
menu.lst content
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
# kopt=root=UUID=26d0c941-1acf-4be0-9a6c-a1e9586e8434 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=26d0c941-1acf-4be0-9a6c-a1e9586e8434 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=26d0c941-1acf-4be0-9a6c-a1e9586e8434 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=26d0c941-1acf-4be0-9a6c-a1e9586e8434 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=26d0c941-1acf-4be0-9a6c-a1e9586e8434 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
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
and sudo... result
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        9729    57175335    f  W95 Ext'd (LBA)
/dev/sda5            2612        9055    51761398+   7  HPFS/NTFS
/dev/sda6            9056        9179      995998+  82  Linux swap / Solaris
/dev/sda7            9180        9729     4417843+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885184 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   7  HPFS/NTFS

```

---

### Post by meierfra on 2007-12-02
Your partition table got screwed up. "sda4" is missing. Testdisk (see my signature) should be able to fix it.

---

### Post by haneya on 2007-12-02
but ti was workin before and why is sda3,sda4 are necessary

---

### Post by merlinus on 2007-12-02
Even if sda4 is missing, according to fdisk -l, sda7 is a linux partition.  

So perhaps changing the linux kernel stanzas to (hd0,6) in menu.lst will be useful.

---

### Post by meierfra on 2007-12-02
```
Een if sda4 is missing, according to fdisk -l, sda7 is a linux partition. 
So perhaps changing the linux kernel stanzas to (hd0,6) in menu.lst will be useful.
```

That's what I wanted to suggest first and already had written detailed instruction. But then I decided that it would be better to fix the problem, then to work around it. Something has screwed up the partition table. And  I really think it should be fixed.

---

### Post by haneya on 2007-12-02
but how can I change it (read only file ) and which part i have to change ??

---

### Post by meierfra on 2007-12-02
Just in case here are the detailed instuctions I had typed. (This should let you boot into ubuntu even though you partition table is screwed)



Do this in a termimal

```
sudo grub
```

and at the "grub>"  prompt:

```
root (hd0,6)
setup (hd0)
quit
```

Next you need to edit menu.lst

Open the file via

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda7 /ubuntu
cd  /ubuntu/boot/grub
sudo cp menu.lst menu.lst.backup
gksudo  gedit  menu.lst

```

Change

"#groot(hd0,5)" to  "#groot(hd0,6)"

Change

"root(hd0,5)" to  "root(hd0,6)"  (five times)

Save the file.
Reboot and everything should be fine

---

### Post by meierfra on 2007-12-02
Just I second. There are a couple of typos. I will fix them.

---

### Post by meierfra on 2007-12-02
O.K. all typos are fixed.

---

### Post by merlinus on 2007-12-02
@meierfra

I am not certain that the partition table is fried.  I run a very similar setup.  Windows (NTFS) is on sda1.  sda2 is an extended partition containing sda5-9.  There is no sda3 nor sda4.

sda5 is ntfs and the rest are ext3 (sda9 is /swap).

---

### Post by haneya on 2007-12-02
Working amazing :) thanks guys

---

### Post by merlinus on 2007-12-02
Glad to hear it!

Have fun, and post back with any other issues.

---

### Post by meierfra on 2007-12-02
> @meierfra

I am not certain that the partition table is fried. 

You are right of course (I have been sitting on the  computer for long, My brain is screwed, not the partition table).

---

### Post by meierfra on 2007-12-02
merlinus: welcome back. Where have you been?

---

### Post by merlinus on 2007-12-02
> **meierfra said:**
> merlinus: welcome back. Where have you been?

Hi, and thanks for asking!  I never really returned from a week-long kayaking trip on Navajo Lake in mid-September.  Life on the Internet left a great deal to be desired, so I spent as much time as possible paddling on the Rio Grande, communing with towering rock cliffs, hawks, beavers, waterfowl, coyotes, and even an eagle.

But now that the snow is flying, time to re-group and prepare for winter.

So my thoughts have returned to the ubuntu forums, and the excellent connections I have made.

He's baaaaaaack....
:guitar:

---

### Post by meierfra on 2007-12-02
haneya:   There is a tiny chance that "swap" is not working.

Type "free" in a terminal. Make sure that the last line looks something like

Swap:      2273156          0    2273156

and not

Swap:      0          0    0

---

### Post by mrcbldn on 2007-12-14
I installed XP over my native Vista, obviously the grup installation was covered from Windows bootloader.

Following this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")

I was able to reinstall grup into linux partition (hd0,2); when I rebooted my computer I saw rightly grub menu, if I choosed Windows boot everything was ok but if I choosed Linux Partition appeared:

"Error 17: Cannot mount selected partition"

I choosed 'e' on linux entry into grup menu; the first voice appeared as root (hd0,3) but I saw that the ext2fs partition was into 2!!!
So I changed it into root(hd0,2) with 'e' option.

After the changed it i pressed 'b' (boot); then my linux starded!!!

:guitar:

The changes was not persistant, so after boot, I needed to permanent change the grup configuration.
I went into /boot/grub/menu.lst and I changed the entries for linux into root (hd0,2) (they where to (hd0,3) )

Now everything works well but I still does not understand how my new xp install dropped an existent partition!!
Unlikely I have not the output of previous fdisk command :-(

---

