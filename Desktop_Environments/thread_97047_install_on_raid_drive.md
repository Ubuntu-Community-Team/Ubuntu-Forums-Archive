---
title: "install on raid drive?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by paridoth on 2005-11-30
how do you get the kubuntu installer to recognize a raid aray? i have two hard drives, a pair of 80 gig WD sata drives, on mirror raid, with a windows ntfs partition and 10 gigs of unpartitioned space. with windows i had to put the drivers on a floppy and load it durring the install, what is the procedure i should use here? here is a link to the motherboad site. thanks for all your help!

ps im installing off the Kubuntu 5.10 (breezy) i386 cd.
[http://www.chaintechusa.com/tw/eng/product_spec.asp?MPSNo=13&PISNo=319](http://www.chaintechusa.com/tw/eng/product_spec.asp?MPSNo=13&PISNo=319)

ok i did it again and this time i created two raid partitions on the seperatly recognized sata drives, and when i went to create software raid i got a message telling me it needed to write changes to the disks to continue. i think this is what i want to do, and this will make it recognize the raid i have however im worried that doing this will make my current ntfs windows partition unusable or even erase it, how should i proceed?

---

### Post by HermanAB on 2005-11-30
Hardware RAID array?  If so, get a Linux driver from the RAID adaptor manufacturer web site, eg Adaptec.

---

### Post by paridoth on 2005-11-30
how do i find out if its a hardware or software raid? i downloaded drivers from the chipset site, however the instructions were only for fedora and suse, ill paste them in here to see if you can tell me how this translates to ubuntu

____________________________________________________________________

ULi RAID Linux Driver
For Fedora core 2/3-32/64bit
Version 1.00 [22/11/2004]

[INTRODUCTION]

1.1 Foreword

This procedure applies to ULi RAID 5281|5283|5289|5287 adapters.

1.2 Prepare a Driver Diskette

You will use a diskette to load the new Linux driver onto your PC.

1) Obtain a new, formatted diskette and label it "ULi RAID Driver Disk."
Insert it into your PC's floppy drive.

2) Extract the contents of the driver file you downloaded from the
ULi website onto your floppy disk. Use either WinZIP in Windows or
Unzip in Linux to extract the files.


[INSTALLATION]

2.1 To install the ULi RAID Linux Driver into an EXISTING SYSTEM:

1.) Boot linux system and login as root.

2.) Insert ULi RAID Driver Disk for install ULi RAID Driver by issuing
commands :
# mount /dev/fd0 /mnt/floppy
# cd /mnt/floppy
# sh install (Answer Yes/No when inquire setup configuration)

You can answer Yes to bind ULi RAID driver into linux booting.

# cd ..
# umount /dev/fd0
NOTE: Due to the Linux kernel misidentifying the ULi RAID card, all IDE
channels except onboard IDE are disabled. To enable the other IDE channels,
remove the line "ide2=0 ide3=0 ide4=0 ide5=0 ide6=0 ide7=0 ide8=0 ide9=0"
in /etc/lilo.conf.anaconda or /boot/grub/grub.conf.

3.) Reboot Fedora system.


2.2 To install the ULi RAID Linux Driver into a NEW SYSTEM

1.) Start the Fedora Installation with CD-ROM booting.

2.) At the first installation screen, a prompt
labeled "boot:" will appear at the bottom of the screen.

3.) Please append parameters (see Note 1 below) at the "boot:" prompt,
then press the Enter key.

4.) At the "driver disks" dialog box, press "YES" .

5.) Next ,if "Driver Disk Source " dialog box appears,select "fd0" and press "OK".

6.) At the Insert Driver disk" dialog box,insert your raid driver disk into floppy drive and press "OK" to continue;

7.) If the system shows "Error" dialog box, press "Manually choose" and scroll down at "Select Device Driver to Load"
dialog box to select ULi 5281 Raid Controller (ALiRaid),then press "OK".


8.) Enable "Configure advanced boot loader options" box at Boot Loader
Configuration menu, and type kernel parameters (see NOTE 2 below)
in the General kernel parameters field.

9.) Continue with the installation as normal.

10.) If the installer occur warning message about "The partition table on device /dev/sd(x)
is of an unexpected type loop for your architecture....." or "the partition table on device sd(x) is unable to read
...",just click "YES" bottom to continue the install.
11.) Complete the installation as directed by the install.

WARNING(only for fc2-64bit): After the install begins,fresh install into hd on 5281 card may pause at certain package because of the fc2-64 system 's ext3's bug;
you must repeat the install several times to solve the problem.

[NOTE]

Linux Kernels 2.6.x misidentiy ULi ATA-RAID controllers as simple
IDE controllers. This results in the built-in Linux IDE driver trying to
handle the controller and can prevent the proper ULi RAID driver
from loading.
Follow the installation instructions AND the parameter commands referred
to below section. This status we called "IDE issue".

M5281/M5283:
1.) "linux ide0=0x1f0,0x3f6,14 ide1=0x170,0x376,15 ide2=0 ide3=0 ide4=0
ide5=0 ide6=0 ide7=0 ide8=0 ide9=0 dd "

2.) "ide0=0x1f0,0x3f6,14 ide1=0x170,0x376,15 ide2=0 ide3=0 ide4=0 ide5=0
ide6=0 ide7=0 ide8=0 ide9=0 noirqdebug"
("noirqdebug" parameter is for fedora 2 only)

M5287/M5289:
1.) "linux dd"

2.) "noirqdebug"
("noirqdebug" parameter is for fedora 2 only)

______________________________________________________________________

---

### Post by HermanAB on 2005-11-30
"how do i find out if its a hardware or software raid?"

Well, it is your computer - if you really don't know what you have, then you have to open the box and take look.

A hardware RAID system is typically a special PCI card from Adaptec or someone with two or more disk drives connected to it.

A software RAID is made by connecting two or more similar disk drives to the mother board directly, then using a software driver to control them.

---

### Post by paridoth on 2005-12-01
im sorry, thats what i meant, how can i tell them apart, until today i didnt even know such a thing as a software raid existed, i thought raid was raid.
as you can see in the link to the motherbaord site i get my raid from my motherboard, my two sata drives connect to the motherboard, and shortly after the post screen i have a split second to hit a button and enter a raid setup screen and deleet or create raid arrays.

---

### Post by HermanAB on 2005-12-01
So, it sounds like you have RAID capability built into the mother board, in which case, the whole RAID thing should be transparent to Linux.

---

### Post by paridoth on 2005-12-01
=( that suks what can i do to make it recognize it?

---

### Post by vva on 2007-07-21
Hi,

Has this issue been resolved? I tried to install Kubuntu 7.04 on my system, which probably has the same chipset ALi/ULi M5281 and I got an error when trying to resize my ntfs partition. This worried me enough so I didn't insisit and winXP was able to repair the damage on boot.

I have neither hard- nor software RAID. The controller is only there for my SATA drive.

I downloaded the Red Hat driver from ULi but I'm newbie enough not to be able to figure out whether/how to apply the instructions to installing Kubuntu from the live CD. Should I use the alternate CD and how?

r. Ville Valtasaari

---

