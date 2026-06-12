---
title: "[SOLVED] I want to install XP on separate HD in my linux pc"
date: 2008-01-26
forum: Desktop Environments
---

### Post by discmaster on 2008-01-26
How do I go about installing XP on a separate HD in my pc? I already have Ubuntu running on 325 GB SATA drive, & I want to install XP on an 80 GB IDE drive I have. What are my options, best/easiest trouble free way to go about this?

I have searched google for answers, but all I seem to find are solutions dated back to 2005-2006.

Thanks for your help! :popcorn:

---

### Post by logos34 on 2008-01-26
here's an oldie but goodie:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by discmaster on 2008-01-26
Thanks logos, that's beautiful! Even contains links to boot cross platform IDE/SATA. Guess I have my work cut out for me this weekend! I will report back upon successful completion of the task at hand. :grin:

---

### Post by discmaster on 2008-01-27
Help! 

I guess I am doing something wrong here; I have set my IDE drive (XP destination) to 1rst boot in BIOS, the SATA (linux) drive to boot 2nd. I can get the windows setup to run, format the IDE disc, accept F8 agreement, etc., but when the pc reboots after formatting w/ NTFS system, it just goes thru the same sequence all over again; Format drive, accept agreement, etc. 

I can't get past this part & get on with the windows install. Help! :confused:

---

### Post by discmaster on 2008-01-27
Ok, made a bit of progress here; I unplugged the SATA (linux) drive & installed xp on the IDE drive. Seemed to be the only way I could make it work. I now have xp installed on that IDE drive, connected as primary master. I reconnected the SATA drive, but at this point I cannot determine how to properly setup the dual boot.

All I am ending up with is either booting to xp or linux; in other words, I do not get a "selection" menu during boot. Can y'all help me out, using the most "noobish" language possible? Sorry, but I getr confused easily with this stuff!

Thanks much,
dm :)

:popcorn:

---

### Post by discmaster on 2008-01-27
I got this from another thread, but I don't know if it is correct for my setup; I would need to change "professional" to "home" , but would the rest of it work? I am afraid of messing things up badly...
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1

---

### Post by discmaster on 2008-01-27
Well, I managed to screw this thing up bad, I think. I ran this -
gksudo gedit menu.lst

& somehow managed to delete the entire contents of it, because now when I open it up, it is nothing but a blank page. Help me get it back?!?! :(

**EDIT - FALSE ALARM - I was able to retrieve it! WHEW!**

---

### Post by discmaster on 2008-01-27
I still don't understand how to eidt it properly; do I need to change one of those hd0 hd1 entries since I have linux on a SATA drive, & XP on an IDE? Or just copy it over as it is listed above?

---

### Post by discmaster on 2008-01-27
What I have done thus far;

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
> title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I have tried several different variants of this which I have located on a few different threads on here, but no matter what I edit the menu.lst to do, it still ignores the IDE XP install & boots directly to ubuntu. I can go into the BIOS & set the IDE drive to boot, & xp will boot fine, but of course I would rather do it this way.

What can I do to fix this? For some reason, I am given no menu or options at boot to select which OS I want to use. 

:confused: Thoroughly Confused Here!!! :confused:

I just did what it said to do!!! ](*,)

---

### Post by TimMcE on 2008-01-27
There may be an easy solution to this, depending on what exactly you want to do with XP.  Download VMWare Server from [http://www.vmware.com](http://www.vmware.com) (it's free), and during the initial set up, tell it to use your second hard drive to store any OS that you install.  Then just install XP under VMWare, and you're good to go.  The nice thing about this is that you can have Ubuntu and XP running at the same time, so you can watch a movie while you wait for XP to boot. ;)

I'd recommend against taking this route if you plan to use XP for playing games, since the VMWare 3D graphics drivers are kind of crappy.  Otherwise, I can't be much help, I'm afraid.  I tried doing something similar myself, and wound up just nuking both Ubuntu and XP, then installing XP first, and Ubuntu second, since Windows doesn't seem to like it when it doesn't get to go first.

---

### Post by logos34 on 2008-01-27
> **discmaster said:**
> What I have done thus far;

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST

I have tried several different variants of this which I have located on a few different threads on here, but no matter what I edit the menu.lst to do, it still ignores the IDE XP install & boots directly to ubuntu. I can go into the BIOS & set the IDE drive to boot, & xp will boot fine, but of course I would rather do it this way.

What can I do to fix this? For some reason, I am given no menu or options at boot to select which OS I want to use. 

Add the xp drive to /boot/grub/device.map:

> (hd1) /dev/hda

In menu.lst, make sure **timeout** is set for at least a few secs, and **hiddenmenu** is commented out (#).  

Even though you have 'makeactive' in the windows stanza, you may also have to flag the XP partition as 'boot' (*) before it will start up. 

gksudo gparted

>right-click hda1>manage flags>set as boot

remove boot flag on ubuntu root partition (linux doesn't need it)

---

### Post by bulldog on 2008-01-28
Hi discmaster,
It's not so hard to do,and you where on the right trail.
But to help you,I need some infoo.
Can you post for me the output of the fdisk command with both hdd's connected?
```
sudo fdisk -l
``` its a small L not a one.
Can you post your menu.lst so I can see what you dis already?
```
gksu gedit /boot/grub/menu.lst
```

After the windows install,you have to change the hdd boot order in the BIOS,and set the Sata with Ubuntu as the first boot device,and your windows IDE hdd as the second boot device.
If you do so you can only boot Ubuntu and won't see windows at all,BUT by adding some lines into your menu.lst,you can boot windows too.
The lines to add you already found,but if you're unsure I can help you with that one.
I wait for your reply.

regards,bulldog

---

### Post by discmaster on 2008-01-28
> tr@tr:~$ sudo fdisk -l
[sudo] password for tr:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81a381a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2   *        3648        6079    19535040   83  Linux
/dev/sda3            6080        7991    15358140   83  Linux
/dev/sda4            7992       30401   180008325    5  Extended
/dev/sda5            7992        8257     2136613+  82  Linux swap / Solaris
/dev/sda6            8258       30401   177871648+  83  Linux

Disk /dev/hda: 81.9 GB, 81964302336 bytes
60 heads, 63 sectors/track, 42350 cylinders
Units = cylinders of 3780 * 512 = 1935360 bytes
Disk identifier: 0xcee8cee8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       42342    80026348+   7  HPFS/NTFS
/dev/hda2           42343       42348        9922+   f  W95 Ext'd (LBA)
tr@tr:~$ 

Following is the menu.lst - At this point, it may look very bad to you, because I have been trying different things I have found on different sites...

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=07b7fcb6-280b-4ba7-963e-ae53b806b8b3 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=07b7fcb6-280b-4ba7-963e-ae53b806b8b3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=07b7fcb6-280b-4ba7-963e-ae53b806b8b3 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by logos34 on 2008-01-28
> **discmaster said:**
> Following is the menu.lst - At this point, it may look very bad to you, because I have been trying different things I have found on different sites...

Just as I thought, hiddenmenu is enabled, which is why the grub menu doesn't show up:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

you want 

> **[COLOR="Red"]#[/COLOR]**hiddenmenu

Also, where's the windows entry?  either you cut off the bottom portion of menu.lst with the windows stanza or it's not saving changes (you need to be root user):

gksudo gedit /boot/grub/menu.lst

The windows entry you posted was correct.

---

### Post by discmaster on 2008-01-28
logos,

I will remove the # from hiddenmenu. Actually, it wasn't there to begin with, I misunderstood another thread & added it. But I still didn't get the selection menu initially, when that was correct. Are you saying this is what I need to do?
> title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Do I paste that in above the line
###BEGIN AUTOMAGIC KERNEL LIST
?

---

### Post by logos34 on 2008-01-28
> **discmaster said:**
> I will remove the # from hiddenmenu. Actually, it wasn't there to begin with, I misunderstood another thread & added it. But I still didn't get the selection menu initially, when that was correct. Are you saying this is what I need to do?

**#hiddenmenu** is what you want, so put the hash mark back.  By putting a '#' (comment) you're telling grub, 'disable hiddenmenu option--I want to see it.'

You might also want to increase the 'timeout' line.  


Put XP BELOW 'automagic' section:
> 

### END DEBIAN AUTOMAGIC KERNELS LIST

 title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


If none of this works, I'm fresh out of ideas

---

### Post by discmaster on 2008-01-28
Uh Ohh... I have a problem; I added the aforementioned text & now I can't get booted into linux. The linux drive is selected as first boot in the BIOS, & I can also select it from a boot menu by pressing F8 during startup.

However, even after I select the correct drive, XP is the one that loads. What have I done? :confused:

---

### Post by logos34 on 2008-01-28
> **discmaster said:**
> Uh Ohh... I have a problem; I added the aforementioned text & now I can't get booted into linux. The linux drive is selected as first boot in the BIOS, & I can also select it from a boot menu by pressing F8 during startup.

However, even after I select the correct drive, XP is the one that loads. What have I done? :confused:

You put it inside the automagic seciton at the top--default is set to 0.  Take it out and put it at the bottom, OUTSIDE that section.

---

### Post by discmaster on 2008-01-28
Put it the whole way at the bottom, after ### END DEBIAN AUTOMAGIC KERNELS LIST ?

**EDIT _ Sorry, I see you already answered that! **

---

### Post by Rome.konig on 2008-01-28
hey i read your questions and i had the same problem before. 

i have a raid set up and a few IDE's in my box right now. i don't use windows anymore i'm all linux now but this is how i was able to resolve my problem.

1st. i installed ubuntu into one of my IDE drives and made sure it booted up correctly. [ i installed ubuntu in a slave drive, not the master that windows would use as c: drive] for some reason windows like to be the master of things...  

2nd.  Next i installed windowsXP in the master drive (c: drive) and waited for it to finish. 

3rd. the boot sequence is pretty tricky, if your Master drive boots first, it will go directly to windows without acknowledging the slave drive contanting linux. 
~So i would advise to make your boot sequence, LINUX>WINDOWS>ETC

linux should give you an option to boot linux or windows. even though its installed in your slave drive.

-have fun
_rome

---

### Post by discmaster on 2008-01-28
logos,

Ok, that is working! I now get "press esc to enter boot selection menu" when I boot. There is one slight issue, still... If I don't press F8 during boot, the pc still goes right to xp. I have the linux HD selected in the BIOS as the first boot drive, but for some reason, the XP drive is the one that is initalizing first.

Any ideas why?

---

### Post by discmaster on 2008-01-28
**Another False Alarm! ** :redface:

Somehow, from all the booting/rebooting I have been doing, the BIOS did get changed so that the XP drive was booting first. I changed that, now all is working normally. I get the Selection menu upon boot now, & all looks good.

Thanks to all for the assistance; for some reason, I was just unable to grasp the concept of doing this!

:popcorn:

Good job guys! =D>

---

### Post by logos34 on 2008-01-28
> **discmaster said:**
> **Another False Alarm! ** :redface:

Somehow, from all the booting/rebooting I have been doing, the BIOS did get changed so that the XP drive was booting first. I changed that, now all is working normally. I get the Selection menu upon boot now, & all looks good.

Thanks to all for the assistance; for some reason, I was just unable to grasp the concept of doing this!

:popcorn:

Good job guys! =D>

no problem.  glad it's working now.  Mark as 'Solved' (>thread tool)

---

