---
title: "Vista freezes on boot, Ubuntu works fine."
date: 2009-04-30
forum: General Help
---

### Post by usopenplayer on 2009-04-30
Hey Guys,
   I have looked all over the internet and haven't found much help, I seem to have a very peculiar problem.  

Here is what I did to get in this mess: I installed Ubuntu 9.04 (dual boot with Vista home) recently but somehow only allocated 2.5 GBs for my home directory...the other 108 GBs that I allocated for the Ubuntu install where being recognized as an external storage device.  I could boot into either Vista or Ubuntu fine, I just couldn't install anything in Ubuntu due to the lack of space.  I used gparted to format the Ubuntu partition and tried reinstalling and got even wierder problems.  Eventually I just expanded the Vista partition to encompass the entire hard drive and reinstalled Ubuntu over that.


I am now running Ubuntu and it works great, but every time I try to boot into Vista GRUB gets stuck at "Starting up..."  I have let it sit like this for hours, it just freezes at this point.

I know the Vista partition isn't corrupted because I can mount Vista's partition in Linux and access all my files fine, so I assume that it must be something with the MBR.  I have an ASUS M50 laptop and it the recover disk that it comes with will NOT let me restore Vista's MBR (I do not own a Vista Disk), it will only let me wipe the entire HD (or partition).  I'd really rather not wipe my system if it can be helped because besides the MBR everything is working wonderfully...

I am not very experienced with hard drive partitioning but I have attached screen shots of my partitions from gparted, and the output from the command "sudo fdisk -l" if that helps.  I have a feeling that the problem is simple and I am missing something obvious, but I have been wrong before =P



Thanks,
-Dave

---

### Post by Monotoko on 2009-04-30
Can you run this for me and post the output please?

```
gedit /boot/grub/menu.lst
```

---

### Post by usopenplayer on 2009-04-30
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e79c0f14-fce2-4a88-ae67-51915fc660ae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e79c0f14-fce2-4a88-ae67-51915fc660ae

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e79c0f14-fce2-4a88-ae67-51915fc660ae
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e79c0f14-fce2-4a88-ae67-51915fc660ae ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e79c0f14-fce2-4a88-ae67-51915fc660ae
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e79c0f14-fce2-4a88-ae67-51915fc660ae ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e79c0f14-fce2-4a88-ae67-51915fc660ae
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by Monotoko on 2009-04-30
Delete this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

Its picked your recovery partition up as Windows Vista

see if that fixes the problem ;)

---

### Post by Pidgin on 2009-04-30
I think there is not any problem with your MBR.
Your GRUB should display two items of Windows Vista. I think only the second will boot your Windows Vista.
If that does not work, there may be something wrong with the boot sector of the VistaOS partition, not the MBR. Boot using your Windows Vista DVD, then enter the command-line interface, and type:
```
bootrec /fixboot
```
You should not use "/fixmbr", or Windows Vista will overwrite GRUB.

---

### Post by usopenplayer on 2009-04-30
I deleted the entry, and it removed a one of the Vista boot options, It is still hanging though...

Pidgin, is there any way I can do this without a Vista DvD?  I only have a recovery DvD that will wipe everything...

---

### Post by Monotoko on 2009-04-30
You definatly deleted the right entry? And i dont think there is a way to get into the recovery console without a Vista Install DVD, you could maybe check your Recovery DVD without actually reinstalling, it may come with a repair option.

---

### Post by usopenplayer on 2009-04-30
I deleted the correct one, I tried booting into the other one and it came up with an error that said "Missing Recovery.dat"...but that actually booted, I suppose the next step is to find a Vista DvD :P

---

### Post by Monotoko on 2009-04-30
Aye, just borrow one from friends or get an ISO, your not actually installing it, so its perfectly legal to own the disk if you have a legal product key, which you do because you have vista installed.

---

### Post by meierfra. on 2009-04-30
I don't think you need to reinstall Vista. Try this:

Download the testdisk-6.10.linux26.tar.bz2 package to your desktop, and then do:



```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda
```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Vista partition (should be #2) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk.

This should take care of the "starting up" error.

But you might also  have to fix the Vista boot loader.  So if you are still not able to boot into Vista, report any error messages you got and we will work from there.


If you have more than one hard drive, you might also try

title Vista
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader  +1

in menu.lst

---

### Post by usopenplayer on 2009-04-30
Thanks for your advice everyone, I will try everything you guy's said and report back on what worked.

---

### Post by Pidgin on 2009-05-01
> **usopenplayer said:**
> I deleted the correct one, I tried booting into the other one and it came up with an error that said "Missing Recovery.dat"...but that actually booted, I suppose the next step is to find a Vista DvD :P

That is weird. I think you still boot into the recovery partition.

---

### Post by usopenplayer on 2009-05-03
> **meierfra. said:**
> I don't think you need to reinstall Vista. Try this:

Download the testdisk-6.10.linux26.tar.bz2 package to your desktop, and then do:



```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda
```Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Vista partition (should be #2) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk.

This should take care of the "starting up" error.

But you might also  have to fix the Vista boot loader.  So if you are still not able to boot into Vista, report any error messages you got and we will work from there.


If you have more than one hard drive, you might also try

title Vista
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader  +1

in menu.lst


This worked, it did fix the starting up problem, however your guess was correct and it still says that I have a corrupted file and cannot boot 
the filename is winload.exe
can I just replace this file manually?

I downloaded a "Vista Recovery DvD" from this location 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
I read on other forums that you could run a command from this "bootrec /fixboot" might fix the second problem?  I am afraid to run this command before getting a confirmation because I don't want to corrupt anything else.

---

### Post by meierfra. on 2009-05-03
> the filename is winload.exe
can I just replace this file manually?

Usually the error messages means that Windows Boot loader is configured wrongly. Try this:

Boot from a Vista Recovery DVD,

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".
If a pop windows appears, offering to repair a problem with the "Startup options", click on "Repair and restart".
Otherwise choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" more than once.

---

### Post by usopenplayer on 2009-05-03
> **meierfra. said:**
> Usually the error messages means that Windows Boot loader is configured wrongly. Try this:

Boot from a Vista Recovery DVD,

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".
If a pop windows appears, offering to repair a problem with the "Startup options", click on "Repair and restart".
Otherwise choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" more than once.


Success!  I am writing this message from my Vista partition thank you all for your help :)...I'm curious though was this just a problem with my Vista boot record?  What did the testdisk utility that I ran fix? (I like learning the source of problems not just how to fix them)

---

### Post by meierfra. on 2009-05-03
When you resized the Vista  partition the  start point of the vista partition must have changed.
Now the start point  is recorded in two different places:

The boot sector of the Vista partition
In the BCD  (the BCD is a  registry used by the Visa boot loader)

After resizing,  both those places still contained the old start point.
Testdisk fixed the number in the boot sector, and the boot sector  was now able the find the vista boot loader.
(fixboot can also fix this number, but tesdisk is more reliable)

The  Vista Recovery CD fixed the number in the BCD, and the Vista boot loader now was able to find "winload.exe"


Did  you use the gparted to resize Vista?  If yes,which version (look under Help->About in gparted)?
Did you intentionally move the start point of the Vista partition? (sometimes gparted moves the start point to keep the partition on cylindrical bounds)

---

### Post by jamieh on 2009-05-03
Don't use Vista.

---

### Post by usopenplayer on 2009-05-03
> **meierfra. said:**
> When you resize the Vista  partition the  start point of the vista partition must have changed.
Now the start point  is recorded in two different places:

The boot sector of the Vista partition
In the BCD  (the BCD is a  registry used by the Visa boot loader)

After resizing,  both those places still contained the old start point.
Testdisk fixed the number in the boot sector, and the boot sector  was now able the find the vista boot loader.
(fixboot can also fix this number, but tesdisk is more reliable)

The  Vista Recovery CD fixed the number in the BCD, and the Vista boot loader now was able to find "winload.exe"


Did  you use the gparted to resize Vista?  If yes,which version (look under Help->About in gparted)?
Did you intentionally move the start point of the Vista partition? (sometimes gparted moves the start point to keep the partition on cylindrical bounds)

Ah, very interesting...I did indeed used Gparted v0.4.3  I did not intentionally change the start of the partition.  I did however expand the Vista partition over an old botched Ubuntu install... after I expanded the partition I reinstalled Ubuntu and that is when my problems began.  
Everything is working top notch right now though.  :)


> **jamieh said:**
> Don't use Vista.

I admire your passion, but I have never had any problems with Vista, is there any reason in particular that I should avoid using it?

---

