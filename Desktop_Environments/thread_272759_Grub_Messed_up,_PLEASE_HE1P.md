---
title: "Grub Messed up, PLEASE HE1P"
date: 2006-10-06
forum: Desktop Environments
---

### Post by spacecowboy706 on 2006-10-06
Using Ubunbtu 6.06

I followed this Ubuntu Forum How to guide exactly step by step:

[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

and now i can no longer boot up my ubuntu. I cam curently using the live cd.

When I start the screen it goes through its normal start up process and where it would generally say "starting Grub 1.5" or whatever it now says "Error 18". 

I have already tried using the live cd option to reinstall Grub located here:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

but when i get to step 4 of DO NOT FORMAT THEM i click on the forward button and it says i cannot proceed with formatting the "/" ... so that guid doesnt work or im doing it wrong.

Somebody please help me out here... I dont want to have to reinstall Ubuntu as I have already spent allot of time customizing the menu's and such. I will be waiting patiently for someone to help as I cant do anything with this computer until this problem is resolved.

---

### Post by divague on 2006-10-06
use this guide, this worked for me

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by lemonsCC on 2006-10-06
are you using the altenate iso?  you have to use this to reinstall GRUB

---

### Post by spacecowboy706 on 2006-10-06
Im here till it is done... as this pc will be a paperweight if i cant fix it.... so please dont leav me hanging... im followingth guide selected and i am stumped.

at this step:
find /boot/grub/stage1

i get back:
 (hd0,4)
 (hd1,0)

and now i am supposed to do this:

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

root (hd?,?)

i am obviously supposed to substitute the "?" in the command with either (hd0,4) or (hd1,0) and i am not sure which one to use....

I dont want to mess up my windose xp hard drive nor my ubuntu hard drive, so which one do i use.... I do know that i have two hard drives.. a 127GB with winxp as (hda) and a 78gb with ubuntu (hdb).

PS.... In the bios i am booting from the smaller Ubuntu drive (hdb)

Please assit me here?

---

### Post by divague on 2006-10-06
check your bios and see which disc is your pc booting from, there you should install grub. I always do that if i don't know where to install grub.

---

### Post by spacecowboy706 on 2006-10-06
In the bios i am booting from the smaller Ubuntu drive (hdb).... which one of  these:

(hd0,4)
(hd1,0)

is the one i need to use?

---

### Post by spacecowboy706 on 2006-10-07
gues i have been abandoned.. so i tried to use both of them.

I was able to finally get the grub screen and when i select Ubuntu i get error 17.

anybody else feel free to jump in.

---

### Post by confused57 on 2006-10-07
Boot up with the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".
Please post the output of this command.



Ubuntu on your hdb drive is root (hd1,0)...you'd then enter:
setup (hd1)
quit

This will setup grub to the mbr of your hdb drive, following the instructions in the link you used:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you happened to install grub to your Windows drive mbr, you can restore the Windows mbr by following this guide(can you boot the Windows drive by selecting it to boot first in bios?):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You mentioned you have a Windows drive and an Ubuntu drive, but I'm wondering if you also have Ubuntu installed on your Windows drive, i.e. root (hd0,4)?  Might be best for you to post the output of the first command above(sudo fdisk -l) before you try any of the other suggestions.

---

### Post by spacecowboy706 on 2006-10-07
here is the ouptut you requested:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/hda2           16709       19457    22081342+   5  Extended
/dev/hda5           16709       17472     6136798+  83  Linux
/dev/hda6           17473       17612     1124518+  82  Linux swap / Solaris
/dev/hda7           17613       19457    14819931   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9494    76260523+  83  Linux
/dev/hdb2            9495        9729     1887637+   5  Extended
/dev/hdb5            9495        9729     1887606   82  Linux swap / Solaris
ubuntu@ubuntu:~$

and then ....

grub> find /boot/grub/stage1
 (hd0,4)
 (hd1,0)

grub> root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Grub is now working but any one of the entreies in the menu i select i get error 17.

---

### Post by confused57 on 2006-10-07
Can you boot first from the hda drive, since you installed grub to its mbr?

---

### Post by spacecowboy706 on 2006-10-07
when i boot from **hdb** this is now what i get:

booting "ubuntu, kernel 2.6.15-27-386"
root (hd1,0)
filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-27-386 root dev/hdb1 ro quiet splash

error 17 cannot mount selected partition
press any key to continuie....


when i boot from **hda** this is now what i get:

Grub Loading stage 1.5
Grub Loafing, Please Wait
Error 18

Please dont leave me hanging i have as long as neeed to resolve this and i am very grateful for your help... if you have to leave please let me know and i will just reinstall everything (as a last resort cause i have allot of stuff on my ubuntu drive i dont want to lose) 

PS.... i have always booted from hdb if that helps.

---

### Post by spacecowboy706 on 2006-10-07
edited my last reply.

---

### Post by confused57 on 2006-10-07
OK, let's try this...boot to hdb first, when you get to the grub menu, highlight the Ubuntu entry, press "e" for edit, change the root (hd1,0) to
root (hd0,0)...see if this boots into Ubuntu.
This change isn't permanent if it works, you'll have to change it in your /boot/grub/menu.lst.

Here's a reference to grub error 18:
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)
Linux may be detecting your hard drives differently from how your bios does.

---

### Post by spacecowboy706 on 2006-10-07
Oh I love you so much :-D  now that worked.....

> you'll have to change it in your /boot/grub/menu.lst

how do we do that?

---

### Post by confused57 on 2006-10-07
Open a terminal, enter:
```
gksudo gedit /boot/grub/menu.lst
```
The menu.lst is short for menu.list, not menu.first.

Scroll down to the Ubuntu entry(s) for hdb1 and change the root from (hd1,0) to (hd0,0).

You might want to backup your file, before making the changes in your menu.lst?:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

You might also want to post the contents of your menu.lst file(OS boot entries), after you've made the changes & can boot Ubuntu on hdb1:
```
cat /boot/grub/menu.lst
```

---

### Post by spacecowboy706 on 2006-10-07
Outstanding that fixed my ubuntu problem... here is what my /boot/grub/menu.lst looks like:

 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hdb1 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Mandriva Linux release 2006.0 (Official) for i586 (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-19mdk-i586-up-1GB root=/dev/hda5 
savedefault
boot


Now what would I change in here so that when i selected windows xp pro it would boot up as well? I am getting the same error 17 message when i select it to boot.

and

if i wanted to not have all the os choices from the grub menu how would i make just Ubuntu and windows show up and not the others?

---

### Post by confused57 on 2006-10-07
You might need to add a mapping command to your Windows entry:

```
title                 Windows XP Professional
rootnoverify     (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader     +1
```

This assumes you're booting first from hdb.

Add:  You comment out the entries you don't want displayed in your grub menu, by placing a # in front of them.

---

### Post by spacecowboy706 on 2006-10-07
i have always booted from hdb... so should i give that a try

---

### Post by confused57 on 2006-10-07
> **spacecowboy706 said:**
> i have always booted from hdb... so should i give that a try

Yes, it's worth a try.

---

### Post by spacecowboy706 on 2006-10-07
That worked as well and I would like to thank you very very very much for helping me out in this major bind i was in. Now my system is working like it was before i started jacking with it this evening.

The moral of this story is... if your a noob dont mess with grub. :D 

one last question to ask and you can help if you have time... if your out of time then that is ok also, since you got me up and going again .

In the grub menu there are a bunch of choices to selct from, like:

ubuntu blah blah
ubuntu blah blah recovery
ubuntu blah blah
ubuntu blah blah recovery
windows xp pro
Mandriva linux

and i am only wanting 
ubuntu
windows xp pro

to be the only two options? how do i accomplish this?

---

### Post by confused57 on 2006-10-07
Yes, it's getting late here on the East coast and I'm going to have to go...glad everything worked for you.
Here's an excellent website you might want to peruse:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
This is the homepage, if you scroll down, you'll see a section on grub, as well as a plethora of excellent links that may be helpful in configuring Ubuntu when you have problems.

You can probably boot Mandriva with root (hd1,4).

Put a #(comment out) in front of any OS entries in your menu.lst that you don't want displayed in your grub menu at bootup...they'll still be in your menu.lst and can be uncommented(remove #), if you ever need them.

Glad I could help...

---

### Post by bulldog on 2006-10-07
Just comment ## the lines you don't wanna see in your GRUB menu.lst.

---

### Post by spacecowboy706 on 2006-10-07
> Just comment ## the lines you don't wanna see in your GRUB menu.lst.

U lost me already on that ](*,) 

Does that mean i put the actual "##" in front of the entries that pertain to the other boor options... like this (the ones in bold)?

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-27-386 **<------- not this one**
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

**##title Ubuntu, kernel 2.6.15-27-386 (recovery mode)**
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

**##title Ubuntu, kernel 2.6.15-26-386**
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

**##title Ubuntu, kernel 2.6.15-26-386 (recovery mode)**
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

**##title Ubuntu, memtest86+**
root (hd0,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bulldog on 2006-10-07
Your on the way but you have to set a # on **every** line you don't want to see,not just the headlines.

---

### Post by spacecowboy706 on 2006-10-07
but the headlines are all i see in the choices i have to select from in the grub menu?

Nevermind i figured it out from the link above.

---

### Post by bulldog on 2006-10-07
You have to edit it like,
```
gksudo gedit /boot/grub/menu.lst
```

Now put a # in front of every line from a kernel you don't want to see.```

#title		Ubuntu, kernel 2.6.15-27-k7
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash vga=792
#initrd		/boot/initrd.img-2.6.15-27-k7
#savedefault
#boot
```

---

### Post by spacecowboy706 on 2006-10-07
got it. thanks and you can even change the title line to read anything you want.. like now I have...

MyName Ububtu
MyWifesName Windows

---

### Post by confused57 on 2006-10-07
> **spacecowboy706 said:**
> got it. thanks and you can even change the title line to read anything you want.. like now I have...

MyName Ububtu
MyWifesName Windows

Sounds like you got it worked out...least it was a learning experience...you can do what you like, but I'd suggest you may want to keep the following as well(latest kernel recovery mode & maybe the next oldest kernel, in case you have trouble booting to the newest one):

title Ubuntu, kernel 2.6.15-27-386 
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

You can designate which OS you want grub to boot by default:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by spacecowboy706 on 2006-10-08
I even figured out how to make my own splash screen for it now... It was very painstaking trying to line up the default border that appears on there but after about 40 bootups and a dry marker map on my monitor i got it... i made my own by making my own default border page then copying the "bazooka frag penguin" from gnome-look.org (cant remember the original author of that piece) but it was fantastic and it looks even more fantastic on mine cause it all lines up correctly.

Here it is if anyone is interested (under attachments as Mine.xpm.gz). Dont extract it, just copy it to your /boot/ directory and then open a terminal and enter;

 gksudo gedit /boot/grub/menu.lst

when the document opens go to:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

and insert this... splashimage=(hd0,0)/boot/mine.xpm.gz ...onto the 5th line from the top... which will then look like this:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd0,0)/boot/mine.xpm.gz

Click the save button and then you are done. close out the terminal and restart the computer.

---

