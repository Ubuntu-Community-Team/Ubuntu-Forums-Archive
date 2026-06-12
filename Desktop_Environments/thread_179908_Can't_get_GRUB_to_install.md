---
title: "Can't get GRUB to install"
date: 2006-05-21
forum: Desktop Environments
---

### Post by technel on 2006-05-21
Hello,

I have two hard drives, a primary SATA 160gb and a 30gb IDE slave (just used for storage). Windows XP is on a 120gb partition on the first hard drive on the sda1 partition. I installed Ubuntu on the remaining ~37gb, and after the install, I chose to install GRUB. The installation of Ubuntu was successful, I rebooted, and yet GRUB did not work...it just booted right into XP.

So I booted from the Live CD and tried some commands:

sudo grub-install /dev/sda
sudo grub-install /media/sda
sudo grub-install /dev/sda1
sudo grub-install /dev/sda2
sudo grub-install /dev/sda3
sudo grub-install /dev/hda
sudo grub-install /dev/hda1
sudo grub --install-partition=(...)
etc.

None of them worked. Does anyone have any suggestions? I check under cfdisk and it does show the Ubuntu partition as sda2 (with Windows on sda1).

Responses are greatly appreciated. Thank you!

---

### Post by jones_jj on 2006-05-21
Did you install Grub when you were installing Ubuntu or after the fact?  Also when you were installing Grub, did you see a screen that would ask you about any other OSes that you have installed?  And where did you install Grub, was it on the MBR or on the partition with Ubuntu?

---

### Post by jpkotta on 2006-05-21
First, in Debian (and Ubuntu), the preferred way to install grub is update-grub.  It tries to auto detect the correct place to install grub, and after looking at the actual script, it seems to just look at what device / is mounted on.  In your case, this should be /dev/sda, and it should work.  

I would have thought that ```
sudo grub-install /dev/sda
``` would have worked.  Can you post the output of grub-install or update-grub?

---

### Post by technel on 2006-05-21
[QUOTE=jones_jj]Did you install Grub when you were installing Ubuntu
or after the fact?[/QUOTE]

I installed Ubuntu and it said it detected that another OS (which it
listed as Windows XP Professional...) and asked if it wanted to
install GRUB. I chose Yes, it said "Running grub-install (hdo)" or
something, and the setup completed without any more mention of GRUB.
The install did not work, so then I tried using the Live CD with
grub-install.

[QUOTE=jones_jj]Also when you were installing Grub, did you see a
screen that would ask you about any other OSes that you have
installed?[/QUOTE]

It said it detected XP, yes.

[QUOTE=jones_jj]And where did you install Grub, was it on the MBR or
on the partition with Ubuntu?[/QUOTE]

I have run numerous Linux distrobutions before and previously with
GRUB and LILO (including on the main Debian distro) I have been
prompted whether I want to install to the boot sector, MBR, etc. I
always chose MBR, and it worked, but this time it did not ask me at
all. The only options I had on install was "Yes" or "No."

[QUOTE=jpkotta]First, in Debian (and Ubuntu), the preferred way to
install grub is update-grub.  It tries to auto detect the correct
place to install grub, and after looking at the actual script, it
seems to just look at what device / is mounted on.  In your case, this
should be /dev/sda, and it should work.[/quote]

> ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ mkdir /boot/grub
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file...

Could not find /boot/grub/menu.lst file. Would you like
/boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I tried this before, but first of all, the menu never came up
(although in the menu.lst file it appears that the hidden menu
variable is TRUE), and second of all, it doesn't cite Windows XP in
menu.lst at all. This is the menu.lst file that was created:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=/dev/mapper/casper-snapshot ro

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/mapper/casper-snapshot ro
quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/mapper/casper-snapshot ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

[QUOTE=jpkotta]I would have thought that ```
sudo grub-install
/dev/sda
``` would have worked.  Can you post the output of
grub-install or update-grub?[/QUOTE]

> ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive.


I don't know if this helps at all, but this is from "sudo cfdisk":

```
    Name        Flags      Part Type  FS Type          [Label]
    Size (MB)
 ------------------------------------------------------------------------------
   sda1        Boot        Primary   NTFS             []             120588.42*
                           Primary   Free Space                           2.42*
   sda2                    Primary   Linux ext3       [/]             37811.62
   sda5                    Logical   Linux swap / Solaris
 1636.84
```

Any ideas? Thanks for the help!

---

### Post by technel on 2006-05-22
It is pretty important that I get this running as soon as possible, so help would be greatly appreciated.

Since my last message, I have asked in IRC 3 times. I got several suggestions, none of which worked:
[LIST]
[*]The ShipIT CD could have any invalid md5sum.
[LIST]
[*]So I downloaded another copy of Ubuntu and burned it at the slowest speed possible, but the installation went the same as always.
[/LIST]
[*]Press the "esc" key on startup.
[LIST]
[*]I tried this already, but GRUB doesn't even install (I know this because the directory does not exist when I try to access it with the Live CD)!
[/list]
[*]Try to use the Windows XP multi-boot loader.
[list]
[*]This might work, but I would HIGHLY prefer getting GRUB to work. It would require minimal configuration if I installed more Linux distros, it doesn't look like crap, etc. That said, this is always an option.
[/list]
[*]Re-install Ubuntu and make sure you install GRUB to the MBR.
[list]
[*]First of all, I tried re-installing Ubuntu three times with no more success than any of the previous times. The forth time was today when I tried using my burned CD instead of the ShipIt CD. Second of all, GRUB doesn't give me options whether I want to install it to a partition or the MBR. It just says "GRUB has detected another operating system: Microsoft Windows XP......Would you like to install it to the MBR?" I always select YES. And by the way, it always says "Running grub-install (hd0)...." -- why does it say "hd0"??
[/list]
[/LIST]

Again, help would be greatly appreciated. Best regards!

---

### Post by jones_jj on 2006-05-23
hd0 is the first hard drive, but I've always seen it as hda, hdb, etc, not really ever seen it as hd0.  When you are installing Ubuntu, how are you installing it?  Do you use expert mode, or do you just hit enter and do it the simplest way possible?

**It just says "GRUB has detected another operating system: Microsoft Windows XP......Would you like to install it to the MBR?**  So Grub is asking you if you want to install it to the MBR then?

> 
Code:

Name Flags Part Type FS Type [Label] Size (MB) ------------------------------------------------------------------------------ sda1 Boot Primary NTFS [] 120588.42* Primary Free Space 2.42* sda2 Primary Linux ext3 [/] 37811.62 sda5 Logical Linux swap / Solaris 1636.84



Now why is it stating your swap space is Linux/Solaris?  This is something I've never seen either.  Also it looks like you are stuffing everything into "/" instead of creating a few  directories like /usr, /var, and /?

This is very troubling to me, and I am trying to think of anything and everything I can to help you out.

---

### Post by technel on 2006-05-23
[QUOTE=jones_jj]hd0 is the first hard drive, but I've always seen it as hda, hdb, etc, not really ever seen it as hd0.  When you are installing Ubuntu, how are you installing it?  Do you use expert mode, or do you just hit enter and do it the simplest way possible?[/QUOTE]

I don't really know where you can choose what "mode" to install in. I use the advanced partitioner, but I don't know really know what you are referring to.

[QUOTE=jones_jj]**It just says "GRUB has detected another operating system: Microsoft Windows XP......Would you like to install it to the MBR?**  So Grub is asking you if you want to install it to the MBR then?[/quote]

Yes, screenshot of this and more below.

[QUOTE=jones_jj]Now why is it stating your swap space is Linux/Solaris?  This is something I've never seen either.  Also it looks like you are stuffing everything into "/" instead of creating a few  directories like /usr, /var, and /?[/QUOTE]

What I did was go into advanced partition, delete the Ubuntu partition from my previous install, hit ENTER on the free space, and select "Automatically partition space" (see screenshots again). I don't know for sure, but isn't the "/" referring to the Label (which apparently is non-existent), not the directory structure? Obviously I am not manually copying packages and everything off the CDs and creating the directory structure, so why wouldn't it create the /bin, /usr, /var, etc. directories?

[QUOTE=jones_jj]This is very troubling to me, and I am trying to think of anything and everything I can to help you out.[/QUOTE]

Your help is welcomed greatly appreciated!

====================

To help diagnose my problem and better describe what I am seeing during the installation, I took some pictures with my camera of the screens pertaining to this issue.

[http://i76.photobucket.com/albums/j1/technel/100_0820.jpg](http://i76.photobucket.com/albums/j1/technel/100_0820.jpg)
[http://i76.photobucket.com/albums/j1/technel/100_0822.jpg](http://i76.photobucket.com/albums/j1/technel/100_0822.jpg)
[http://i76.photobucket.com/albums/j1/technel/100_0823.jpg](http://i76.photobucket.com/albums/j1/technel/100_0823.jpg)
[http://i76.photobucket.com/albums/j1/technel/100_0825.jpg](http://i76.photobucket.com/albums/j1/technel/100_0825.jpg)
[http://i76.photobucket.com/albums/j1/technel/100_0827.jpg](http://i76.photobucket.com/albums/j1/technel/100_0827.jpg)
[http://i76.photobucket.com/albums/j1/technel/100_0833.jpg](http://i76.photobucket.com/albums/j1/technel/100_0833.jpg) ** GRUB INSTALL QUESTION **

Thanks.

---

### Post by technel on 2006-05-24
(bump)

(wow...page 3 already!)

---

### Post by jones_jj on 2006-05-25
> I don't really know where you can choose what "mode" to install in. I use the advanced partitioner, but I don't know really know what you are referring to.

What I am refering to here is the mode you install Ubuntu.  When you first boot up your PC with the install CD, you will get the screen where you can hit enter or type help for help options.  Also here you can type server to install the server version, or expert to go into expert install mode which give you more control over the installation.

> What I did was go into advanced partition, delete the Ubuntu partition from my previous install, hit ENTER on the free space, and select "Automatically partition space" (see screenshots again). I don't know for sure, but isn't the "/" referring to the Label (which apparently is non-existent), not the directory structure? Obviously I am not manually copying packages and everything off the CDs and creating the directory structure, so why wouldn't it create the /bin, /usr, /var, etc. directories?


"/" refers to the root directory or the top of the file system.  Since you automatically created directories everything gets created for you under "/"  Me personally I created a few directories myself such as /home, /var, and I believe one other directory.  I did the manual option myself.  Also instead of using ext3, I use the reiserfs filesystem.  I have found it is a little more stable, and the journaling system seems to be a bit better.

I checked out your screenshots and everything looks good to me.  I just don't understand why Grub is not installing properly.  The only thing that I can think of is where is your MBR sitting at?  Is it on hdb, or sda?

Since you are not able to boot into Ubuntu with Grub, boot using the live cd and go to the /boot directory.  See if there is a /grub directory.  If there is check to see you have a menu.lst file.  Here is a copy of my menu.lst file for you to look at:

> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
kernelernative k/boot/memtest86+.binSC to see the menu)
boote End DefaulUbuntu, kernel 2.6.12-9-386 (recovery mode)NEL LIST
roothis howmany=(hd0,0) options to pass to only these/
### END DEBIAN AUTOMAGIC KERNELS LIST9-386 root=/dev/hdb1 ro single
initrd can have /boot/initrd.img-2.6.12-9-386ons can be omitted.fiedfault entry
booteluld update/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd. memtest8/boot/initrd.img-2.6.12-9-386boot options
titleefaulttest8Ubuntu, memtest86+d be put into the menu.lstnteractive editing
rootmtest86=true(hd0,0)t occurence of a kernel, not theptionsrotected by the


jj@the-one:/boot/grub$ clear
jj@the-one:/boot/grub$ gedit
The application 'gedit' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.
jj@the-one:/boot/grub$ vim menu.lst 
c
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
timeout         3

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
# groot=(hd0,0)

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by technel on 2006-05-25
[QUOTE=jones_jj]What I am refering to here is the mode you install Ubuntu.  When you first boot up your PC with the install CD, you will get the screen where you can hit enter or type help for help options.  Also here you can type server to install the server version, or expert to go into expert install mode which give you more control over the installation.[/QUOTE]

Ah, I can try using "expert" installation mode and see if I get any extra options that might help.

[QUOTE=jones_jj]"/" refers to the root directory or the top of the file system.  Since you automatically created directories everything gets created for you under "/"  Me personally I created a few directories myself such as /home, /var, and I believe one other directory.  I did the manual option myself.  Also instead of using ext3, I use the reiserfs filesystem.  I have found it is a little more stable, and the journaling system seems to be a bit better.[/QUOTE]

Aren't these directories usually created automatically?

[QUOTE=jones_jj]I checked out your screenshots and everything looks good to me.  I just don't understand why Grub is not installing properly.  The only thing that I can think of is where is your MBR sitting at?  Is it on hdb, or sda?[/QUOTE]

**I think you nailed the problem right here.** I realized that initially, my Windows installation was on sda, and backup was on hdb. hdb was set to the master hard drive. I changed it to slave so sda would be the master, and that most certainly messed something up. What can I do in this situation?

[QUOTE=jones_jj]Since you are not able to boot into Ubuntu with Grub, boot using the live cd and go to the /boot directory.  See if there is a /grub directory.  If there is check to see you have a menu.lst file.  Here is a copy of my menu.lst file for you to look at:[/QUOTE]

Will check that when I can get to my computer again!


Thank you!

---

### Post by jones_jj on 2006-05-27
> Aren't these directories usually created automatically?

Yes they are created automatically, but I have read somewhere and have talked to a few of my friends and they have said to make them seperate file systems, e.g. they will still be under "/" but they are not created automatically.

> I think you nailed the problem right here. I realized that initially, my Windows installation was on sda, and backup was on hdb. hdb was set to the master hard drive. I changed it to slave so sda would be the master, and that most certainly messed something up. What can I do in this situation?

Ok call me crazy, but I did not think you could make an IDE drive a slave to a SATA drive.  First they are not even the same hardware, and second they don't even share a channel at all.  What do you have connected to the same IDE ribbon as your hard drive labled hdb?  Do you have a CD/DVD drive or another IDE hard drive attached to it?

---

### Post by technel on 2006-05-27
[QUOTE=jones_jj]Ok call me crazy, but I did not think you could make an IDE drive a slave to a SATA drive.  First they are not even the same hardware, and second they don't even share a channel at all.  What do you have connected to the same IDE ribbon as your hard drive labled hdb?  Do you have a CD/DVD drive or another IDE hard drive attached to it?[/QUOTE]

Good point. The IDE cable has a 2 CD/DVD drives connected to it, in addition to the hard drive. Here are the options for both the hard drives (for the jumpers):

SATA
> SSC_DIS <--
PM2
OPT1
OPT2

PATA
> CS
Slave
Master <--
PM2

As you can see, I changed hdb from "CS" (original setting) to "Slave" to the current value of "Master". sda is still at "SSC_DIS".

Will this help at all? I will try installing Linux again...

Thanks!

---

### Post by technel on 2006-05-28
I tried installing Ubuntu *again* (literally my 8th or 9th time this month) with the new configuration on the hard drives. Nothing has changed.

](*,) 

Is it really worth it? Any other suggestions? :confused:

Look [on Google](http://www.google.com/search?hl=en&lr=&q=%2Fdev%2Fmapper%2Fcasper-snapshot+does+not+have+any+corresponding+BIOS+drive.&btnG=Search) for "/dev/mapper/casper-snapshot does not have any corresponding BIOS drive." There are a whopping 5 results (excluding the omitted results), one of which is this thread, one is a thread in a foreign language, and the remaining three are IRC logs also in a foreign language.

---

### Post by jones_jj on 2006-05-28
Having your IDE as master or slave will not matter with the SATA drive.  Totally different ribbons and the hardware really does not communicate with each other eiter.

you are trying to install Ubuntu to the SATA drive right?  Just for shits and grins, let's install it to the IDE drive, unless there is important data on that drive.  And see if it will install there.  Make sure to disconnect the SATA drive.  Or wait Ubuntu seems to install just fine, it's just Grub is acting up.

Disconnect the IDE drive and see if you can get Ubuntu on the SATA drive.  The current version of Ubuntu should handle SATA drives just fine.  That is what I don't get.  Something to also think about is the next version of Ubuntu is coming out soon, and it may better handle SATA drives.

---

### Post by jpkotta on 2006-05-28
About manually specifying partitions for directories:  It's not necessary at all.  If you want the easiest install, just put everything on the same partition (except swap).  It sounds like you want to leave open the possibility of installing other distros.  In that case, I would recommend the following:

/boot = 50 MB
swap = RAM
/ = 5-15 GB
/home = the rest

That way, you can have the same menu.lst for all distros (in /boot/grub), and you have all of your files across all distros (in /home).  You can also reinstall without worrying about your data (just be careful not to format the /home partition).   To install a new distro, you just have to make a new 5-15 GB partition somewhere and tell it where /home, swap, and /boot are.

On to the problem at hand.  I just realized you might be running the commands from the live CD environment.  You need to run them in a chroot environment. From the live CD, open a terminal and 
```
mkdir /hd_install
mount /dev/sda5 /hd_install
chroot /hd_install
update-grub
exit
```
That will do things to your installation on the hard drive, not to the live CD environment.  If you are already doing this, then we have to think about it some more.

---

### Post by RedBoot on 2006-05-28
technel, I have the EXACT same problem. I've installed Ubuntu Dapper successfully on over 8 computers, but hit the same wall yesterday.

I'm guessing that Ubunutu can't handle the fact the in BIOS I specified that  the SATA drive to be the one to boot from.

My setup:
/sda1 - NTFS - WinSrv2003 installed yesterday, boots fine.
/sda2 - ext3 Ubuntu /
/hda1 - Ubuntu swap
/hda2 - NTFS - extra storage
/hda2 - Ubuntu /usr

Install proceeds as you've stated. On reboot, grub does not run.
I run the "repair broken" and try to reinstall grub every way possible and always get an "error 20" which is a very generic "failed".:confused: 

A hint may be that Ubuntu refers the SATA as drive 1, but the IDE as drive 0.:-k 

I had a similar problem installing SUSE linux on a PC w/ 2 SCSI disks where somehow it had been set to boot from #1 instead of #0.

I'm going to redo it all, setting BIOS to boot 1st from the IDE. I'll post what I find.

---

### Post by RedBoot on 2006-05-28
:D An "aha" moment:
I just went into BIOS to swap the boot order of my drives and got out the WinSrv2003 disks (groan!) Then thought, "Hey, if grub WAS installing itself onto the wrong disk (the IDE) will it just boot correctly if I swap them?"

And that's exactly what happened. I let the PC boot from the IDE and up with the grub menu. I selected Windows and it worked! Rebooted and chose Ubuntu and it worked!

Hope this helps you.

---

### Post by jones_jj on 2006-05-29
Actually that makes total sense now that I think about it.  If you are installing Ubuntu to an IDE it will be able to see Windows on a SATA drive, but it will think the MBR is on the IDE drive and not somewhere else.  As I said IDE and SATA two totally different beasts.  But what's odd is technel is installing Ubutnu to a SATA drive that has Windows on the same drive.  What I don't get is where is Grub installing?  It should be installing to the SATA drive, but it doesn't seem to be installing there though.

For a swap size, I really wouldn't use the size of RAM.  I've always been told you should always use 2-3 times RAM.  But if you have 2 GB of RAM why bother having swap, just stuff everything into RAM anyway.

---

### Post by RedBoot on 2006-05-29
Hi jones_jj. 
> But what's odd is technel is installing Ubutnu to a SATA drive that has Windows on the same drive. What I don't get is where is Grub installing? It should be installing to the SATA drive, but it doesn't seem to be installing there though.

In technel's 1st post he says:> I have two hard drives, a primary SATA 160gb and a 30gb IDE slave (just used for storage). Windows XP is on a 120gb partition on the first hard drive on the sda1 partition. I installed Ubuntu on the remaining ~37gb, and after the install, I chose to install GRUB. The installation of Ubuntu was successful, I rebooted, and yet GRUB did not work...it just booted right into XP.

I'm thinking he just boots from the IDE and sees what happens.
> If you are installing Ubuntu to an IDE it will be able to see Windows on a SATA drive, but it will think the MBR is on the IDE drive and not somewhere else. As you said, I think grub is installing itself onto the IDE drive. I see what you mean. Not long ago, I installed Fedora 5 on a similar configuration, with Win booting from SATA and Fedora on IDE. It had same problem with grub putting itself on the IDE. (I fixed problem by carving out a part of the SATA drive to install Fedora on.) 
But I don't see this as making sense. To me, it seems like a malfunction, an inability of Linux to sense what disk the computer boots from.

---

### Post by jpkotta on 2006-05-29
[QUOTE=jones_jj]
For a swap size, I really wouldn't use the size of RAM.  I've always been told you should always use 2-3 times RAM.  But if you have 2 GB of RAM why bother having swap, just stuff everything into RAM anyway.[/QUOTE]

I've been told that too, but after playing around for a few years, I've found that 2x is more than enough, and most of the time 1x is more than enough.  If you ever really needed more swap than that, you can make a swap file or buy more RAM.  (disclaimer: I only have experience with desktops/laptops, so maybe the 2-3x would apply to servers.)

[QUOTE=RedBoot]Hi jones_jj. 

In technel's 1st post he says:

I'm thinking he just boots from the IDE and sees what happens.
 As you said, I think grub is installing itself onto the IDE drive. I see what you mean. Not long ago, I installed Fedora 5 on a similar configuration, with Win booting from SATA and Fedora on IDE. It had same problem with grub putting itself on the IDE. (I fixed problem by carving out a part of the SATA drive to install Fedora on.) 
But I don't see this as making sense. To me, it seems like a malfunction, an inability of Linux to sense what disk the computer boots from.[/QUOTE]

Correct me if I'm wrong, but isn't the BIOS what decides which disk boots?  And isn't the BIOS invisible to the OS?  On the other hand, grub should try to install to the disk that /boot is on.  If this theory is correct, then grub is doing the wrong thing and should be fixed.  I'm not sure, but I'm guessing the installer uses update-grub.  I know that's what gets used when you install a new kernel.

---

### Post by RedBoot on 2006-05-29
jpkotta,
> Correct me if I'm wrong, but isn't the BIOS what decides which disk boots? And isn't the BIOS invisible to the OS? True and a good point.
> On the other hand, grub should try to install to the disk that /boot is on. I have to plead ignorance here, both of grub and the details of OS booting.  I assumed grub was looking for the location of Master Boot Record, if another operating system was already installed. I didn't realize grub was going to install on the disk where we place /boot.

But even so, I don't understand why manually trying to direct install-grub to a specific disk fails (again, referring to technel's first posting.)  This has been my experience, too.

---

### Post by jones_jj on 2006-05-30
Hey Redboot, where in Ohio are you from?  I'm from Ohio myself orginally.

What is strange to me is that if he installed both Windows and Ubuntu to the SATA drive, why would Grub be installing to the IDE drive?  That just doesn't make sense to me at all.

Technel, I would like you to try something for me when you have the time.  I want you to disconnect the IDE drive and just have the SATA drive connected.  Then I want you to try and reinstall Ubuntu using the expert mode that I told you about.  And then report back your findings please.

Thanks

---

### Post by jones_jj on 2006-05-30
> I have to plead ignorance here, both of grub and the details of OS booting. I assumed grub was looking for the location of Master Boot Record, if another operating system was already installed. I didn't realize grub was going to install on the disk where we place /boot.

Actually from my experience of dual booting, and I have never created a /boot filesystem before I have always installed Windows first and let it think it's the only OS for you, and then install Linux after that on another partition of the same drive, pretty much just like Technel is doing.  You will have the Windows boot loader in the MBR just like Windows wants, and then I have installed Grub in the MBR also and it seems to work just fine when I have done it.

As we all know all Grub is suppose to do is load a screen that gives you an option as to which OS to load, you hit the corresponding number or highlight the OS you want and hit enter, and then from there Grub is suppose to look at your option and then boot the correct OS.  This is pretty much a nutshell of what Grub is suppose to do.

Grub should install in to the MBR if you tell it to, or another location like the first cylinder of the second hard drive in the 3rd partition if that's where you want to put it.  (just making up some sort of location here)

---

### Post by jpkotta on 2006-05-30
[QUOTE=jones_jj]But even so, I don't understand why manually trying to direct install-grub to a specific disk fails (again, referring to technel's first posting.) This has been my experience, too.[/QUOTE]

See my other post about that.  Technel, it seems like you're trying to install grub from the live CD, which of course doesn't have a menu.lst.  You want to install it from your HD.  If you chroot, you can do that.  

[QUOTE=jones_jj]
What is strange to me is that if he installed both Windows and Ubuntu to the SATA drive, why would Grub be installing to the IDE drive?  That just doesn't make sense to me at all.

Technel, I would like you to try something for me when you have the time.  I want you to disconnect the IDE drive and just have the SATA drive connected.  Then I want you to try and reinstall Ubuntu using the expert mode that I told you about.  And then report back your findings please.
[/QUOTE]

I'm thinking that for what ever reason, grub finds IDE before SATA, and goes with the first disk it finds.  Your suggestion will probably work.  Technel, you should try it.  You can add the other HD manually later.

[QUOTE=jones_jj]Actually from my experience of dual booting, and I have never created a /boot filesystem before I have always installed Windows first and let it think it's the only OS for you, and then install Linux after that on another partition of the same drive, pretty much just like Technel is doing.  You will have the Windows boot loader in the MBR just like Windows wants, and then I have installed Grub in the MBR also and it seems to work just fine when I have done it.
[/QUOTE]

I'm thinking whatever partition /boot is on, even if it's on the same one as /.  I think that's the most logical choice for picking an HD to install to with out knowing exactly which one the BIOS will boot.

---

### Post by RedBoot on 2006-05-30
jones_jj, we may have done a flip flop. I grew up just south of Fort Wayne, went to IU and now live in Cinci.:p 

I'm hoping to find a good reference on grub so I can easily edit the menu. Any web sites, wikis out there?:-k

---

### Post by jpkotta on 2006-05-30
```
sudo apt-get install grub-doc && info grub
```

Not the easiest reference, but it has everything.  It's better than most man pages.  Google "grub doc" (no quotes), and you get the html version.

---

### Post by jones_jj on 2006-05-31
I'd go to wikipedia and do a search on Grub, you may find a lot of helpful information there.

I'm starting to wish I hadn't moved to Ft. Wayne.  There is nothing here for IT Professionals.  I'm actually trying to get back towards Columbus, hopefully to work at OSU again.

jpkotta, you know you may be onto something there.  I just wonder what the boot order is in the bios.  If it is set to boot SATA before IDE or not.  But that still should not really matter to Grub I would think, but I could be wrong.

---

### Post by RedBoot on 2006-05-31
Gracias, jpkotta. I'll check it out!8-)
> Code: sudo apt-get install grub-doc && info grub

---

### Post by jpkotta on 2006-05-31
[QUOTE=jones_jj]jpkotta, you know you may be onto something there.  I just wonder what the boot order is in the bios.  If it is set to boot SATA before IDE or not.  But that still should not really matter to Grub I would think, but I could be wrong.[/QUOTE]

All I know is that when I have an IDE and an SATA installed, my BIOS insists on trying to boot the IDE first.

---

### Post by jones_jj on 2006-06-01
Seeing how I don't have SATA and IDE paired together, can you set in your BIOS that the SATA drive boots first?  I just wonder if BIOSes today are assuming that if you're running IDE and SATA that the IDE will have the OS(es) on them and that the SATA drives are going to be in a raid configuration and not have an OS on them.  A very brave assumption, but I just wonder if that's what it is doing.

---

### Post by ozroy on 2006-06-01
I have a brand new computer and ONLY have a SATA drive. Windows is installed on it and working. But grub will not install. The Dapper installer crashes when it gets to configuring grub.

Trying to do it manually gives me the same errors as everyone else.
/dev/sda does not have a corresponding BIOS drive

---

### Post by tim123 on 2006-06-01
have u tried to use lilo it is better than grub it is more easy to use it will see windows but it won't be called windows xp it is called other

---

### Post by RedBoot on 2006-06-01
> I have a brand new computer and ONLY have a SATA drive. Windows is installed on it and working. But grub will not install. The Dapper installer crashes when it gets to configuring grub. 
Trying to do it manually gives me the same errors as everyone else.
Interesting. FWIW, I have only SATA drives on machine dual booting Win and Fedora 5, but I can't say what Ubuntu installer does in this situation:-k 

> Seeing how I don't have SATA and IDE paired together, can you set in your BIOS that the SATA drive boots first?jones_jj, on my system (w/ an Intel 865GV /ICH5 chipset and Award BIoS) I can go to menu Advanced BIOS Features, Hard Disk boot priority and rearrange the boot order of 1 SATA and 1 IDE drive.  Same on the computer with w/ a NVidia GeForce 6140 nForce 430 chipset and an Award BIOS and 4 SATA drives. .

---

### Post by ozroy on 2006-06-01
OK I got it all working.

Everything installed on the system fine, it just crashed when trying to install grub. As we all know using update-grub and grub-install etc didn't work. I was however able to get grub installed manually.

First I booted into the liveCD. Trying to use the rescue mode on the install discs was painful due to TERM issues. Once on the liveCD desktop I opened up an xterm and mounted the root partition of my new ubuntu install. I then mounted the /dev stuff using *mount -o bind /dev /media/dev* and then chrooted using *chroot /media*

Once that was done I copied the grub stage files from /lib/grub/i386-pc/ to /boot/grub then execute *grub* to get the grub shell. Install to the MBR by typing *root (hd0,4)* then *setup (hd0)*. The root command tells grub where the root partition is. If you don't know type *find /boot/grub/stage1* and that will tell you what device to use.

Once all that is done grub should be installed on the MBR and you just have to make sure menu.lst is all correct. The gentoo installation guide was a big help ([http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)) as was the grub manual ([http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html))

Just to clarrify, I had problems with the 6.06 Desktop installer. So the text installer may work fine. I just downloaded the wrong one yesterday, and didn't want to download another 600Meg. I'm only guessing it was a problem with SATA :)

---

### Post by jpkotta on 2006-06-03
If you think it's a bug in the installer (it sounds like it is), please submit a bug report.

[https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs)

---

### Post by jones_jj on 2006-06-04
You know I really wonder if Breezy fixes a lot of these problems that we have been discussing here over the past few days.  I have to order my cds and I'll have to find out.  Can't wait to see what they have done with Breezy, and I'm really looking forward to the release in November with Xen and a few other fun toys to play around with.

---

### Post by RedBoot on 2006-06-05
> You know I really wonder if Breezy fixes a lot of these problems that we have been discussing here over the past few days?jones, jj, do you mean Dapper, which just left Beta to be released? That's what I've been using for the purposes of the previous posts.

---

### Post by RedBoot on 2006-06-05
jpkotta,> If you think it's a bug in the installer (it sounds like it is), please submit a bug report.Good point. I went to report it and found it already there, so I added my comment and referred to this thread, indicating we have all had a problem with this. 
Interesting reading about the bug at:
[https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/46520/+index]("https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/46520/+index")

---

### Post by jones_jj on 2006-06-06
Yup that's what I meant redboot, I got my animals all confused.  Interesting choice of animals on Ubuntu's part.  I wonder what the release in November will be called.  Will it go away from animal names since it is kind of a bleeding edge version or if it will continue with it's naming covention.

---

### Post by technel on 2006-06-22
[QUOTE=jones_jj]You know I really wonder if Breezy fixes a lot of these problems that we have been discussing here over the past few days.  I have to order my cds and I'll have to find out.  Can't wait to see what they have done with Breezy, and I'm really looking forward to the release in November with Xen and a few other fun toys to play around with.[/QUOTE]

Hey, it's me again (the guy who started the post). Just so you know, I never did get Ubuntu working. I did downloaded 6.06, but GRUB still didn't work properly. I am currently in the middle of development and I really can't afford any more time to invest in this issue, but I think I am going to try completely wiping both drives and starting over once I finish this application. I appreciate all of the responses everyone made, and sorry I was so late in replying!

Hopefully after a clean wipe Ubuntu will install properly with GRUB. I do think something is messed up on the MBR though, when I start up the initial screen shows up a lot longer than usual and says to press a key to view ROM messages or something.

---

### Post by RedBoot on 2006-06-23
technel,
Yeah, it's interesting how your original post can take on a life of its own. 

I believe that many good points about Grub were made in posts on this thread. I know I learned some things.

One thing I did explore after reading a message about whether the /boot directory needed to be on the booted disk. It does NOT. I purposely setup a 4 disk install and put /boot on the 3rd disk. It worked just fine. FWIW.

It DOES seem to assume that, given an IDE and SATA mix, the IDE is the boot drive no matter what you setup in BIOS.

jones_jj,
Your comment about the animal names seems timely. When I last visited the Ubuntu main page, I didn't see any reference to Dapper Drake or any animal; just 6.06. Pretty boring. Is Ubuntu trying to achieve mainstream normalcy? :confused:

---

### Post by technel on 2006-06-27
[QUOTE=RedBoot]It DOES seem to assume that, given an IDE and SATA mix, the IDE is the boot drive no matter what you setup in BIOS.[/QUOTE]

So how exactly are you supposed to get GRUB to load up when you boot from a SATA drive?

---

### Post by RedBoot on 2006-06-28
In short:
1) SATA drives only? No problem.
2) PATA (IDE) drives only? No problem.
3) SATA and PATA with PATA boot drive? No problem.
4) SATA and PATA with SATA boot drive? You will have a problem. You can become a grub expert and tweak it yourself (and will have to re-do some steps manually each time the kernel is updated) or do what I did and reconfig your system to look like 3). ](*,) 

The bug reports are pretty clear that this is a standard problem. What gets me is that on the following report, it's been deemed a level of "wishlist". The last poster reports an awful scenario that I hadn't considered. Grub wipes out the MBR on a drive that should have been an "innocent bystander" but contained a truecrypt drive that was effectively destroyed. Ouch.
[https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/32357]("https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/32357")

---

### Post by mmccaghrey on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:(I have tried (twice) to install Ubuntu Feisty Fawn onto a SATA/IDE system with the SATA drive as the boot drive and it has failed at this point. I have found it a deeply frustrating experience as I have discovered it won't install and I have to either remove my IDE disk or manually edit the boot loader myself.

I cannot say how dissapointed I am that I have encountered this bug and that it is obviously a long standing bug that has been ignored.

I was attracted to Ubuntu as a non-Linux user who wanted to move from XP to Linux but cannot afford the time or effort required to completely relearn how to use my computer. Like or lothe XP you just put it on and it works. This is how Ubuntu needs to be.

I fail to understand how such a simple scenario causes such problems and affects so many without it being solved. I fail to understand how a installation bug can be left fo so long without being solved.

If you really want Ubuntu to be a system only used by Linux-heads then you are going the right way. But if you really do want Ubuntu to attract people away from XP then not just this bug, but the whole attitude behind the lack of progress on this bug needs to be altered.

---

### Post by technel on 2007-10-31
> **mmccaghrey said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:(I have tried (twice) to install Ubuntu Feisty Fawn onto a SATA/IDE system with the SATA drive as the boot drive and it has failed at this point. I have found it a deeply frustrating experience as I have discovered it won't install and I have to either remove my IDE disk or manually edit the boot loader myself.

I cannot say how dissapointed I am that I have encountered this bug and that it is obviously a long standing bug that has been ignored.

I was attracted to Ubuntu as a non-Linux user who wanted to move from XP to Linux but cannot afford the time or effort required to completely relearn how to use my computer. Like or lothe XP you just put it on and it works. This is how Ubuntu needs to be.

I fail to understand how such a simple scenario causes such problems and affects so many without it being solved. I fail to understand how a installation bug can be left fo so long without being solved.

If you really want Ubuntu to be a system only used by Linux-heads then you are going the right way. But if you really do want Ubuntu to attract people away from XP then not just this bug, but the whole attitude behind the lack of progress on this bug needs to be altered.

Yeah, it does kinda suck that this doesn't work. I ended up giving up, buying an external hard drive, and taking out the IDE drive. I invested way too much time into troubleshooting this.

Best of luck, nonetheless!

---

### Post by davexnet on 2007-11-05
"4) SATA and PATA with SATA boot drive?"

Is that really so uncommon?  I think not, it's an upgrade path for anbody who originally
installed Windows on IDE, then later bought a big SATA drive and cloned XP to it, and made the
SATA the new boot drive.


I am suffering from the problem myself and being new to Linux, I don't know a clean way to fix it.
I read this whole thread and I see that I could have allowed the installer to install GRUB to the IDE drive
MBR; then I could have altered the BIOS to boot first from the IDE drive.

But this is nonsense. All the OS's are installed on the SATA !!.
I'm afraid at this point, I agree whole heartedly with mmccaghrey's comments a couple of posts back.
If Linux ever wants to expand it's base,  this kind of thing needs to be recognized as important and fixed.

Dave

---

### Post by gkestrel on 2008-01-10
I have experienced similar problems myself when using both sata drives and ide drives.  I usually fix the grub issue first by booting with a super grub disk and letting that fix grub, but then found that every time the kernel updated i had the grub problem return.  After searching on the net i found that occasionally Ubuntu gets the device map for the hard drives wrong and has taken a best guess during the install. I was able to fix this by doing the following

before starting make sure to backup of /boot/grub/menu.lst and /boot/grub/device.map
To fix your /boot/grub/device.map	type sudo gedit /boot/grub/device.map and change it
mine original was like this

(hd0)	/dev/sda
(hd1)	/dev/sdb

i then changed it to

(hd0)	/dev/sdb
(hd1)	/dev/sda

then save the file

I then renamed /boot/grub/menu.lst  to /boot/grub/menu.lst.old
then updated grub by	sudo update-grub

As a precaution do sudo gedit /boot/grub/menu.lst again and check to see if it contains the correct entries for your windows installation mine did not, so i had to copy the correct entry from the old version of menu.lst so as to be able to boot into windows correctly.
Also if you have any splashscreen enabled you will need to add again the line to enable it.

---

