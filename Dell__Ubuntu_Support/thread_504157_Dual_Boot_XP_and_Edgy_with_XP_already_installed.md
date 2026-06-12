---
title: "Dual Boot XP and Edgy with XP already installed"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by htrdfrk on 2007-07-18
Ok I just want to make sure with some sort of assurance that it won't be a problem installing Ubuntu 6.10 on my Dell XPS M140 which already holds XP.  I have alot of things on the system that I want to keep so basically I just want it left untouched, and install Ubuntu along side it.  Now my concern is from alot of what I have read is that most say to reformat drive, partition it, then reinstall windows then ubuntu.  But I don't want to reformat, repartition and all that...I just want to install it with the XP still intact as it is right now.  Please dont' leave comments like why you need windows and such, as it won't help me...let's just leave it at I want them both.  So with that my question is this....If I was to load up the live cd of edgy into my active XP set up...and begin to install it...will it work around it automatically with me specifying some things of course by readjusting the partitions with in the install, or do I have no choice but to repartition seperatly then install.

thanks for your time and any advice you can give.

---

### Post by dougfractal on 2007-07-18
I've not got windows so i've not tried them

1   download virtual box an run ubuntu inside XP.
or
2 [http://wubi-installer.org/](http://wubi-installer.org/)

> Wubi is an unofficial Ubuntu installer for Windows users that will bring you into the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other application. If you heard about Linux and Ubuntu, if you wanted to try them but you were afraid, this is for you.



Wubi is Safe

It does not require you to modify the partitions of your PC, or to use a different bootloader.

Wubi is Simple

Just run the installer, no need to burn a CD.

Wubi is Discrete

Wubi keeps most of the files in one folder, and If you do not like, you can simply uninstall it.

Wubi is Free

Wubi (like Ubuntu) is free as in beer and as in freedom. You will get this part later on, the important thing now is that it cost absolutely nothing, it is our gift to you...

---

### Post by TheTaylorEffect on 2007-07-18
A few weeks ago, I was in an identical situation. To answer your question: no -  simply booting to the Edgy Live CD will not ensure a smooth dual boot install.

I found this guide [by Matthew J Miller ]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")to be particularly helpful with my XP/Ubuntu Dual Boot.

It suggests you use the Linux Rescue CD to safely repartition the drive, then install Ubuntu.

It worked like a charm for me (using Feisty). And others have reported similar success with Edgy (although, if you can get your hands on a 7.04 CD tonight, you might want to use that instead, it automates the GRUB bootloader reconfiguration... with Edgy you have to do it by hand).

The GPart tool (a Partition Magic clone) is VERY easy to use... so if you don't mind burning an extra CD the Rescue CD is the way to go, in my book!

Please, keep us posted on how it goes!

---

### Post by pbcartwright on 2007-07-18
I have a Dell XPS M140, I've had it for over a year, and it has XP and Kubuntu Gutsy on it now. I've installed Ubuntu, Kubuntu and... a few others on it.
just shrink the partition ( defrag XP first) and be on your way.. I also just put ntfs-3g on it, so I can write to teh XP partition from Kubuntu, in case I need some files from the dark side.

---

### Post by htrdfrk on 2007-07-19
Thank you all for your advice and thank you TheTaylorEffect for the guide....

I have one other question regarding this before I hit the button....In some instances I see people needing to create a /boot partition with in the 1024 cyclinder mark and in other instances I see people saying it's not necessary.

So question is:

Do I need to shrink my windows partition a bit at the front so I don't end up with the 1024 cyclinder error, ie Grub Freeze, or will it not be a problem for this situation?

Thanks again for the advice.

---

### Post by strabes on 2007-07-19
Your windows partition should be at the front of your hard drive. My partitions go like this:

20gb: Windows XP
15gb: Kubuntu Feisty
1gb: Swap
Rest of HD: Shared ext3 data partition.

You can resize the windows ntfs partition to around 20gb; more if you have lots of data on it. If you like ubuntu, you should consider setting up a shared data partition so that you can read/write files to it in both windows & ubuntu.

Good luck.

---

### Post by htrdfrk on 2007-07-20
Ok I have a problem...I got everything partitioned down, installed ubuntu and everything seemed to go exactly to plan.  So it came to the end and asked to restart and I said yes.  It restarts and begins to load Grub, which immediately I was like wait a minute...I put in for the Grub to be installed on (hd0,1) and it installed fine, but shouldn't it load into windows so I can set up the windows boot loader to recognize ubuntu, instead of grub trying to act as the boot loader?  So It recognized windows is there in the Grub loader, but when I click on it to load it says the typical starting up...
starting grub stage2 or something like that, then go directly back to the boot loader main page where it lists all the OS's again...I don't get it...

my partitions are listed as
hda1 primary empty fat16
hda2 primary windows ntfs boot
hda3 primary unbuntu ext3 
hda4 extented ext3
hda5 logical swap
hda6 logical osshare fat32

Any advice you could through at me would be much appreciated...I'm guessing I messed something up and am hoping I can fix it.

---

### Post by htrdfrk on 2007-07-22
Ok, I wanted to make sure I documented my whole process for my Dual Boot Windows XP/Ubuntu Edgy installation on my Dell XPS M140 in which XP came installed when I got it.

Now I did struggle a bit, but was mostly due to one mistake in which I read several times, but didn't quite click to it was starring me in the face.  Now I did ask a few questions mostly for reassurance as it wasn't the first time I had installed a linux system, just the first time I had ever attempted a dual boot.  Also as a special note TheTaylorEffect really pointed me in the right direction with link to Mattew J. Miller's Research Homepage, I got alot of good info out of that which was very similar to my situation.  So Thank You Kind Sir.

So first things first...I immediately began a system defrag and disk scan as my system had been used for a good 6 months with just windows prior to my dual install, so it was essential to sort and clean everything thoroughly before I began my partitioning.

Secondly I got me a copy of the Linux System Rescue CD in which I got from here: [http://www.sysresccd.org]("http://www.sysresccd.org/Main_Page")

Now I was ready to partition.  I could have partitioned it with other partition software I had, but I wanted to use the same partition program as Ubuntu would use during install so I used the System Rescue CD for that.  When the disk loaded up, it said right in the main page it had "gparted" which is what ubuntu uses during it's installer so I typed:

gparted

and the response I got was...It can't load the graphical interface or something becuase I wasn't in the Rescue CD's user interface.  So I typed:

startx

and the interface began loading....after it was finished it automatically started up the terminal so all I had to do was type:

gparted

and bam...there it was....now first thing I noticed is I already had 3 Primary partitions in there and I need atleast 2 more just to install linux so one had to go.  I examined them and noticed my first one was only about 37MB, my second one was 72GB, my third on was 4GB.  The first and 3 part I didn't recognize as there was nothing identifying them, but the 2nd one was obviously the Windows one and I want to keep that one perfectly in tact just size it down to what I need out of it.  Also I need to get rid of one of them so I have a spot for 1 more partition for linux.  So I deleted the 4 GB as after some research I realized it was the dell support section in which I was no longer going to need and if I did I have it all on the disks dell sent me with the machine.  Then I took the windows one and shrunk it down to 40GB to hold what I had on there now and some room for some other stuff.  The linux paritions I would be putting in was:

Primary for the root
Extended for the 2 logical extensions of Swap and Osshare(so windows and linux have a shared section, this was a must in my eyes)

in the end my partition layout looked as such:

Unidentified(or uh oh, need to fix boot section...you never know) 37MB
Windows 40GB
Linux 20GB
Extended 14GB
Logical Swap 4GB
Logical Osshare 10GB

Once partitioning was complete I was ready to begin Installing Ubuntu.  I put in Ubuntu 6.10 Edgy Edition Live CD into the drive and away it went.  Now the cool thing about the live CD as it allows you to load up the linux, test it out before you ever commit to installing it....but when your ready, you just click the Install Icon on the desktop.

So Install began...I went through the 6 steps and answered as needed till I reached the Partitioning section of the Install....There I Chose "Manual Partition" as I want to designate what for what myself.

so it came to the partition screen, I doubled checked my partitions and all looked good, so I clicked forward...it then asked me to place the mount for the partition section so I could easily identify what was what.

so I chose:

/windows for sda 2(as windows was on the second partition on the drive)
/  for sda 3(as this is the third partition on the drive and the section I set aside for the linux root)
/swap for sda 5( as this is the fifth partition on the drive)
/osshare for sda 6(as this is the sixth partition on the drive)

*Now you probably ask what happened to the 4th partition on the drive...well that is the extension that the 5th and 6th are in as so we don't have to have wasted Primary's*

**Others may ask "sda" what about "hda".....well my drive was a SATA drive so sda was essential**

***Check Format buttons to right on all except Windows***

Now after that I clicked the forward button to initiate the mount changes and then it came up with a screen that said a summary of what and where was going to be loaded with a section that said:

GRUB (hd0) <------"hd0 was in a box you can click on and edit....this is important, as I dont' want GRUB going where ever it wants.

I need to make sure GRUB loads in the Linux / directory I created and I remember earlier that it was place in the 3 partition on my drive which is key here....

(hd0) represents #1 as it starts on 0

so in order for me to place it in parition 3 I had to change it to:

(hd0,2) 

,2 meaning the second one after number 1, which would be 3

I was now ready to go....clicked the forward button and away it went.  About 25 minutes later the install was complete and it was asking me to remove the CD and hit enter.  So I did and it began to reboot my computer...I was not sure what to expect at this point, just hoping something will work...and to my expectation it directly loaded into windows...thank god, because that proved through the process it didn't mess up the windows section one bit which was exactly what I wanted.  Now only thing I need to do now is get the Windows boot loader to recognize Linux.

So I needed to make a boot redirect that I could edit into the windows boot.ini

I put in the Linux System Rescue CD and began these steps also provide by the guide directed to by TheTaylorEffect.

First thing I wanted to make a mount point for the osshare partition, so I typed:

mkdir /mnt/osshare

Then I needed to mount it so I typed:

mount -t msdos /dev/sda6 /mnt/osshare

*sda6 represents the 6th partition on the drive that I made for the osshare*

Next I needed create the file windows will need in order to boot linux so I typed this:

dd if=/dev/sda3 of=/mnt/osshare/ubuntu.bin bs=512 count=1

*sda3 represents the 3rd partition on the drive that I made for the / *

Now the only thing I had left to do was reboot into windows and direct the file to the boot.ini, so I rebooted the computer and once windows was fully reloaded, I clicked on my computer and realized I had an extra drive section listed and what do you know...it was the osshare section and had a file in it called Ubuntu.bin

So I copied the Ubuntu.bin to the C:\ drive

While in the C:\ drive I went into the menubar and clicked tools--->folder options---->view tab and selected the "show hidden files and folders" and unchecked the "hide protected operating system files"

I then looked in the C:\ drive and a file named boot.ini, I right clicked it and clicked properties.  I unchecked the "read-only" box so I could edit the file then opened up the boot.ini and added this to the bottom:

C:\ubuntu.bin="Ubuntu Linux Edgy Edition"

*also change the timeout in the boot.ini so that it reads 5 or 10 instead of 30, or you'll be waiting 30 seconds for it to made the primary OS choice if your not there to pick one*

then saved and closed the file....I right clicked on the boot.ini again, selected properties, and checked the "read-only" box again and when back to tools in the menubar and changed the folder options back the way there were...then rebooted the computer....and BAM!

There it was....instantly the windows bootloader came up and asked if I wanted XP or Ubuntu...I checked both to make sure they worked and they did, so my work here was done.

so I thought....when I got in, I had 2 things that weren't quite right.  The resolution wasn't perfect and I need to set up a wireless manager that would easily handle WPA encryption for my router...which I thought could be a pain, but took less then 5 mins for both.

I went to the System--->Administration section and choose Synaptic Package Manager (The best thing since the kernal was invented for linux)

In there I went to the menubar and chose the repositories....when it opened up, I checed all the boxs so I got all packages from all over available to me.  I then searched for 915resolution and kwlan and marked both for installation and clicked apply...the installed in about 30 seconds and from there I rebooted again to set the settings....

when I came in resolution was immediatly fixed, I didn't have to adjust anything...but the wireless didn't come up....so I looked in the Applications section in Internet and there it was...I clicked on it...and I immediatly added a profile...put in my ssid, chose my encryption type and put in my key and away I went...instantly it was on and active...now I wanted it to load when Linux started so I went to the settings at the top and what do you know...I had a setting for start boot...I checked it and haven't skipped a beat since then...Now my work is done.

Thanks again for all the helped especially TheTaylorEffect and I hope this long boring drawn out post will help someone else in the future to make there dual boot transistion just a seamless as it was for me.

*Note* Entire intall from shrink partiton to finished at end only took 45 mins....Fastest OS I have ever installed...and that's Dual Boot even.  Definate thumbs up for Ubuntu

---

