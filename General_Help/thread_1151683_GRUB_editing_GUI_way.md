---
title: "GRUB editing GUI way"
date: 2009-05-07
forum: General Help
---

### Post by zedi on 2009-05-07
Mine SUM_StartUpManager doesn`t work. Ticking ->Show text... or other options change nothing. BTW is 640x480 the right resolution? 
So I`ve installed KGRUBEditor and it doesn`t open. $ gksu KGRUBEditor (or kgrubeditor) in terminal gives no results and -> /usr/share/kde4/ doesn`t have bin folder. Search for KGRUBEditor didn`t find anything like a bin file.
Reinstalation didn`t work.
I`m a newbie - can anybody help? Plse!

Edit: error in profile - Ubuntu 9.04 Jaunty Jackalope[/U]

---

### Post by Piccy on 2009-05-07
Try this
[https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

You will find it in the Add/Remove.

BTW. I dont really know what you are trying to say :confused: only that you want a GUI for Grub editing

Can you boot? are you getting error message?

---

### Post by salvachn on 2009-05-07
The resolution depends on the sizoe of your display. I think 640x480 is too poor a resolution. 1024x768 is standard for normal displays, and 1440x900 for Widescreen. As for editing GRUB, you can use VI editor! And the grub menu file is /boot/grub/menu.lst.

---

### Post by jayanramesh on 2009-05-07
> edi  	
GRUB editing GUI way
Mine SUM_StartUpManager doesn`t work. Ticking ->Show text... or other options change nothing. BTW is 640x480 the right resolution?
So I`ve installed KGRUBEditor and it doesn`t open. $ gksu KGRUBEditor (or kgrubeditor) in terminal gives no results and -> /usr/share/kde4/ doesn`t have bin folder. Search for KGRUBEditor didn`t find anything like a bin file.
Reinstalation didn`t work.
I`m a newbie - can anybody help? Plse!

Edit: error in profile - Ubuntu 9.04 Jaunty Jackalope[/u] 
please use this code  > gksudo gedit /boot/grub/menu.lst

---

### Post by salvachn on 2009-05-07
@ jayan ramesh.
Hi. Nice to see people from TN!

---

### Post by zedi on 2009-05-08
Piccy,
 I want to do things which SUM does, but for same reason my doesn't.

salvachn,
We are talking here about booting time before Nvidia loads. Are you sure I should use my native resolution 1680x1050 in grub menu list?

jayanramesh,
I know, I can manually edit menu.lst, but can you give me values for: proper resolution, 5 sec timeout, verbose booting, limit # of kernels to 1  and showing bootloader menu?

To all,
I suspect its something wrong with mine GRUB. After installing Jaunty, I couldn't boot to it - only Intrepid. Menu list had also Hardy, which I wiped out during install. I just copy /boot/grub/menu.lst from Jaunty to Intrepid & it seemed to work until I tried SUM.
Edit:
     Mine GRUB is booting from /hd1,6 (that`s mine Jaunty partition). Shouldn`t it be /hd0,0 ?!!!

---

### Post by zedi on 2009-05-09
Ahoi,
     Is there anybody willing to [SIZE="5"]H E L P[/SIZE] freshly converted Ubuntu lover?

---

### Post by 73ckn797 on 2009-05-09
> **zedi said:**
> Ahoi,
     Is there anybody willing to [SIZE=5]H E L P[/SIZE] freshly converted Ubuntu lover?


Yes.

If you have Ubuntu booting from a second hard drive you may want to have the computer boot from that drive.

You do need to provide some system info in order to get more precise help.

The video settings are not in the "menu.lst" and will have to be configured once booted into Ubuntu.

Post the results in terminal of:

```
blkid
```

if you can get into the system. That will show the setup of the hard drives.

Also post the boot menu from:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by zedi on 2009-05-10
As requested:
[I]zedi@zedi-komp:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="A_DRIVE" UUID="491A-83A1" TYPE="vfat" 
/dev/sdb1: UUID="06D048BDD048B529" LABEL="b_Wins" TYPE="ntfs" 
/dev/sdb5: UUID="27509e3f-ed24-4e0e-8ea7-624f60299e02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="db8527c9-211d-4d16-a0a1-30704af4b0db" TYPE="ext3" 
/dev/sdb7: UUID="d166d20c-2250-4d80-8691-a75dca463b38" TYPE="ext3" 
/dev/sdb8: UUID="6c3baac7-a7ba-46d6-897c-1aa38b841cd4" TYPE="swap" [/I]
________________________________________________________________


my menu.lst ->:
----------------------------------------------------------------------------------
[SIZE="1"][I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/grub_face.xpm.gz

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
# kopt=root=UUID=db8527c9-211d-4d16-a0a1-30704af4b0db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=db8527c9-211d-4d16-a0a1-30704af4b0db

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
# defoptions=splash

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
# howmany=1

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false[/I][/SIZE]

[I]## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		db8527c9-211d-4d16-a0a1-30704af4b0db
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=db8527c9-211d-4d16-a0a1-30704af4b0db ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		db8527c9-211d-4d16-a0a1-30704af4b0db
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=db8527c9-211d-4d16-a0a1-30704af4b0db ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		db8527c9-211d-4d16-a0a1-30704af4b0db
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=27509e3f-ed24-4e0e-8ea7-624f60299e02 ro splash vga=791 rootflags=data=writeback 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=27509e3f-ed24-4e0e-8ea7-624f60299e02 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot[/I]

---

### Post by zedi on 2009-05-11
What happend to famous Ubuntu forum spirit? Why nobody wants to help me?
I found on some forum: boot from Ubuntu CD and do-> 
$ sudo grub-install 
Will that fix my GRUB?

---

### Post by 73ckn797 on 2009-05-12
Have not forgotten you, just do not spend all day watching the forums.

Your sda1 (hd0,0) is not the linux drive according to your drive list. It appears to be a flash drive or something else???

Which drive is Jaunty loaded on. I see several Linux drives. 

Your first grub menu entry is for sdb6 (aka... hd1,5) and the other Ubuntu is listed as sdb5 or, as correctly listed, hd1,4.

There is a program in the repositories that allows a GUI grub editing. I do not have that name at the moment.

---

### Post by zedi on 2009-05-12
Mine sda1 (hd0,0) is 320GB internal FAT drive, which I`m using as storage and if I want transfer anything to Windows (Wins can`t see my Linux drive).
Jaunty is loaded on -> sdb6 (aka... hd1,5)
I tried program in the repositories that allows a GUI grub editing called KGRUBEditor and it doesn`t want to open (see previuos post).

What do you think about, quote: "from the live-cd, open terminal and run -> $ sudo grub-install"?

---

### Post by 73ckn797 on 2009-05-12
> **zedi said:**
> What do you think about, quote: "from the live-cd, open terminal and run -> $ sudo grub-install"?

That is a solution. Super Grub Disk will also likely fix things up also.

---

### Post by salvachn on 2009-05-13
Before getting into your GUI, the resolution doesn't matter. Sorry for the late reply, I had some work outside, so could not log on. Your native resolution must be used only when you're running the GUI. Otherwise, any resolution should do.

---

### Post by salvachn on 2009-05-13
[@ 73ckn797:]("http://ubuntuforums.org/member.php?u=641480")
Is QGRUBEditor the name of that package? Have heard of it once or twice, but yet to use it.

---

### Post by pastalavista on 2009-05-13
The easiest way to fix a meesed up grub is with [SuperGrubDisk]("http://www.supergrubdisk.org"). Burn it, boot from it and tell it how your HD is setup and it's pretty automatic.

---

### Post by salvachn on 2009-05-13
> **pastalavista said:**
> The easiest way to fix a meesed up grub is with [SuperGrubDisk]("http://www.supergrubdisk.org"). Burn it, boot from it and tell it how your HD is setup and it's pretty automatic.

Yes, that's an option too.. I once restored a friend's system using it.. Ease of use makes it a good option for a new user..

---

### Post by zedi on 2009-05-13
salvachn
Used to be QGRUBEditor, now is called KGRUBEditor.

73ckn797
I`m afraid of command line, so I tried Live CD, but after -> *sudo grub-install hd0,0* the result is:
[I]Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.[/I]

When I changed in BIOS to boot from my 500GB Linux drive, there was only Windows, no Ubuntu in menu. 
What exact command should I use and should I change in BIOS to boot from Linux drive?
My guess is: *sudo grub-install /sdb1*, which is NTFS partition.

---

### Post by salvachn on 2009-05-13
zedi.
Thanks for the information. So it works only on KDE? Thats what I think looking at the 'K' in the name.

---

### Post by 73ckn797 on 2009-05-13
*Edit grub, inserting the second line as illustrated below.*

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root         (hd1,5)
uuid        db8527c9-211d-4d16-a0a1-30704af4b0db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=db8527c9-211d-4d16-a0a1-30704af4b0db ro splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by zedi on 2009-05-13
salvachn,
KGRUBEditor suppose to work in Ubuntu, but you have to install a lot of KDE packages (dependencies) with it. It`s in Synaptic, but mine doesn`t want to open in Jaunty.

---

### Post by zedi on 2009-05-13
73ckn797,
You are a legend! S O L V E D! Many thanks!
I don`t need KGRUBEditor anymore & I really dont know, how could I omit one line: [root  (hd1,5)]. Guess, have to be more carefull.

> "I wish my computer would do what I want it to do - not what I tell it to do.  - ?"

---

### Post by 73ckn797 on 2009-05-13
> **zedi said:**
> 73ckn797,
You are a legend! S O L V E D! Many thanks!
I don`t need KGRUBEditor anymore & I really dont know, how could I omit one line: [root  (hd1,5)]. Guess, have to be more carefull.

GREAT!! Glad I was able to help you out.

It took me a few times to figure it out but have used it since. The earlier grubs were inserting it automatically until they decided to use the "uuid" designation, I believe starting with 8.10. I found that alone does not always work, as seems to have been your case also.

---

