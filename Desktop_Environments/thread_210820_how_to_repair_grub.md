---
title: "how to repair grub"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Choad on 2006-07-07
windows wrote over the mbr. how can i repair grub using the standard 6.06 install disk?

i tried a few things but got various errors. i looked up on google but most refered to using the old debian style installer and just skipping the install and going to the end and clicking on the install grub bit.... but that doesnt work with dapper because the installer is new!

---

### Post by txuk on 2006-07-07
Have you tried the grub-install command. Havnt got the ubuntu CD on me, but its in most linux distro's and bootable cd's

Should just be the command.

$> grub-install /dev/hda 

Where hda is the drive you want to install grub on.

As long as the 'boot' folder in your ubuntu install is in the same place as it was (ie, hda2.. as opposed to windows making a new partition before it so it becomes hda3 etc) you should be fine, and have your grub back on reboot.

(Grub install may take a while wihout showing anything on screen for a bit (while detecting devices) so dont panic and just be patient :)

Edit: If you cant get a command line off the ubuntu install disk. or it dosnt have grub-install. You may be best just downloading a linux bootable (On cd) distro (such a knoppix) then booting that from your cd drive, and usin grub-install from there.

Good luck

Regards,
Tx

---

### Post by Choad on 2006-07-07
could not find device for /boot: not found or not a block device


???

i dont think windows changed anything 

hda1 = 20 gig fat32 windows c
hda2 = 30 gig fat32 media drive
hda3 = 5.5 gig ext3 linux root
hda4 = .5 gig swap


hmmmmmzzz

---

### Post by txuk on 2006-07-07
Were you trying exactly that command above?

---

### Post by Choad on 2006-07-07
yes indeed

---

### Post by txuk on 2006-07-07
Ok,

Give this a shot (Im no linux guru so bare with me)

The cd will have made itself a ram drive im guesing (if your not farmilliar with ramdrive its a way of using some of your ram as a standard hard drive... in our case.. useful as you can do read-write operations without touching the hdd)

So, if linux is on /dev/hda3.. try this
[B]
$>mkdir /ubuntumount[/B]

^call this whatever.. and put it wherever you can write too, as long as you remember the path to it..
Next:

**$>mount /dev/hda3 /ubuntumount**  
^ replace '/ubuntumount' with whatever path you chose above.

Next:
**$>chroot /ubuntumount**
^ once again, replace /ubuntumount with the path you chose.

now try the 
**$>grub-install /dev/hda**

again.. lemme know how it goes :)

Regards,
Tx

---

### Post by Choad on 2006-07-07
thats actually what i tried first! :(

if i sudo grub-install then it says 

unable to lookup ubuntu via gethostbyname()

and if i do it without sudo then i get the same error as before

---

### Post by txuk on 2006-07-07
Right, first of all, still in your CHROOT, just check the 'proc' DIR is empty.
[B]
$> ls -la /proc[/B]

if it is, exit out of your chroot: 
**$>exit** (should work)

Now try mounting the 'Proc' subsystem inside the drive your about to CHROOT into.

**$>mount -o bind /proc /ubuntumount/proc**
(remembering to replace ubuntumount again with whatever path you chose)

now once again CHROOT in:
**$>chroot /ubuntumount**

And try again:
**$>grub-install /dev/hda**

Good luck 

Tx

---

### Post by Choad on 2006-07-07
you know what? i think that might just have worked! but i got impatient and decided it would be easier to simply reinstall ubuntu (it was clean install anyway)

thanks for the help.... shame i dont get to find out if that would have worked

---

### Post by txuk on 2006-07-07
Yeah, think it would, just checked with a friend he said it sounded about right (He had to do it a while back).

Anyway, no problem, happy ubuntuing :P

Tx

---

### Post by stvmty on 2006-07-08
FYI I did all the steps above and it didn't work.

Same error: *unable to lookup ubuntu via gesthostbyname()*

So, there is a live distro that I can't use to repair my grub?

---

### Post by Herman on 2006-07-08
Hello there you fellows, you can re-install GRUB lots of ways, here are two of them that I have tested and definitely work for me.

1) From a GRUB shell, can be in an installed system or when running a Live CD such as Dapper 'Desktop' Live/Install,
 Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
(To get a grub shell, after booting your live cd, just open a terminal and enter the command: sudo grub)

2)          Re-install GRUB....................................(with Alternate CD Rescue mode).......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

Don't hesitate to let me know if anything there is not clear enough and I'll help you more.

Regards, Herman :D

---

### Post by mackyman on 2006-07-10
> **txuk said:**
> Right, first of all, still in your CHROOT, just check the 'proc' DIR is empty.

Now try mounting the 'Proc' subsystem inside the drive your about to CHROOT into.

**$>mount -o bind /proc /ubuntumount/proc**
(remembering to replace ubuntumount again with whatever path you chose)


Tx

Thanks a lot! That saved the day for me! =) Took about a hour for me to fix grub this time... Last time it took 5h... so a lot faster this time ^^

Just had to add **mount -o bind /dev /ubuntumount/dev/** to make it work.

---

### Post by bartbes on 2006-07-10
Maybe it's new in the 6.06 DD LTS install cd's but on 5.05 BB install cd's grub-install is somehow packaged
If I had the new cd's (shipping right now) I would have posted more

---

### Post by RTB-UK on 2006-11-03
I found something a little easier....No good to original poster but for other like me who have this problem

Boot from the Live CD. From the console run:

sudo grub

From the new grub command line run ( customized to your system )  the following commands.

>root (hd0,2)          
>setup (hd0)


Replace the partition and hard disks for your system. 

(hd0) = the MBR for the hard disk which is where grub needs to install itself too for it to load on bootup. 

(hd0,2) is the partition which contains your grub files. This could be your root partition or perhaps a boot partition.

Hope this helps.

---

### Post by LtPitt on 2008-03-31
Well...
A lot of info here...

I'm ready to mess with it...

I'd just like to ask...
Is there something I *shouldn't* do to kill my xp?
I had two disks and each disk with two partitions.
Then I've reinstalled XP after a mo/bo change (ubuntu did it alive. yeah!:D) and it killed my grub *argh*!

What can I do to recover my dual boot without destroying my brand new xp installation? (it took me ages ^^')

---

### Post by robelliott2125 on 2008-06-16
Does anyone know how to install a GRUB for Gutsy???

I've followed the advice in these posts:

[http://ubuntuforums.org/showthread.php?t=237128](http://ubuntuforums.org/showthread.php?t=237128)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Although the second link gave me a lazy option, which was a case of installing Super Grub disk in XP, reboot, it then took me into my Ubuntu install.
Just it doesn't seem to offer me XP to select, and its not listed in my GRUB menu.

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
# kopt=root=UUID=701b17f6-0c56-4e57-88f7-35fa036c075f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=701b17f6-0c56-4e57-88f7-35fa036c075f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=701b17f6-0c56-4e57-88f7-35fa036c075f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Hope this info helps.

---

### Post by robelliott2125 on 2008-06-16
Anyone???

---

