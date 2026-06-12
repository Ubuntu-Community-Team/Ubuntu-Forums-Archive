---
title: "Error 17 and I suspect others"
date: 2009-03-07
forum: General Help
---

### Post by Clarkey252 on 2009-03-07
Ok so before anyone says it yes i have checked here:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
and i tried doing what mbwardle said on page 1
However:
I mounted the /ubuntu folder and opened it
then when i tried to change folder to /boot/grub it said it can not find it but, it is there when I try to access it through the file browser?!?!

After this I put in dir and all of the files came up except for the /grub folder and an archive file called initrd.img-2.6.24-16-generic 

My current setup is:
HD0 - Windows / Linux
HD1 - Media
HD2 - Encrypted media

and i think windows is on the first partition and linux is on the second (of hdd0)

the device.map file says:
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc

I did try to modify this manually but i cant save it becuase i don't have enough privilages (I assume mbwardle's method opens it as sudo solving this)

Please bear in mind that i am a complete n00b when it comes to linux but I am reasonably computer literate.

I am very greateful to anyone who even reads this,
Thanks
Clarkey252.

---

### Post by GSF1200S on 2009-03-07
> **Clarkey252 said:**
> 
I did try to modify this manually but i cant save it becuase i don't have enough privilages (I assume mbwardle's method opens it as sudo solving this)

You can open the file browser as root using a terminal:

sudo nautilus  (if on Gnome)
sudo konqueror (if on KDE)
sudo thunar  (if on XFCE)

Ill keep an eye on this thread in case the manual editing doesnt help..

EDIT: Opening the browser as root will cause any editors opened from it to be root..

---

### Post by Clarkey252 on 2009-03-07
Ok tried changing the first line of device.map to
(hd0) /dev/sda2

With no luck so ill change it back

Thanks for that GSF i'll try to remember that as it will be useful in future

Any other suggestions?

---

### Post by Herman on 2009-03-07
:D  Hello Clarkey252,
As far as I can tell, editing the /boot/grub/device.map doesn't do anything in modern versions of GRUB.
I don't think GRUB looks at that file at all during boot-up. 
 In older versions of GRUB it may have,  mbwardle was using the Ubuntu 7.10 release candidate.
I think the /boot/grub/device.map is only there for the user's information nowadays.
You're probably wasting your time trying to edit that, if you read the rest of that thread you'll see how hard I tried to see if I could get that to work.

In my opinion, the easiest way to fix GRUB Error 17 is to follow these steps,   [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17").

If your computer has both IDE and SATA hard disks, try [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") and you might get away without the need for editing any files.

Regards, Herman :D

---

### Post by Clarkey252 on 2009-03-07
Ok so i've re-installed grub to (hd0,1) as i should and now im checking the IDE jumper setings for my HDD's i have:

IDE1
CD-ROM set to slave
MAIN HDD (Hd0) to master (with windaz on partition 0 and ubuntu on 1)

IDE2 
HDD1 random stuff (no o/ss) set to master
HDD2 encrypted drive (no o/ss) set to slave

but thats ok right?

And if so what do people suggest is my next move???
--
EDIT:If someone wants to talk me through all this on skype i would GREATLY appriciate it

---

### Post by Herman on 2009-03-07
Take a look at your IDE cables and see if they are the old type which require 'master; and 'slave' jumper settings, or they are the more modern 'cable select' type.
If you have 'cable select' IDE cables then you can set all your drives' jumpers to 'cable select'.
You can tell by the color of the plugs. The older master/slave type of ribbon cable typically has one black plug for the motherboard socket and two black plugs, one for each hard drive.
A 'cable select' IDE ribbon cable has a blue plug for the motherboard and a grey plug for the slave drive and a black plug for the master hard disk.

If you have 'cable select' type cables, then your jumpers are probably set correctly, judging by your description. Very good.

Probably there's nothing wrong with the way GRUB ha been installed then, if you have all IDE hard drives and the cables and jumpers were okay when you installed.

It's more likely that your Ubuntu partition just needs a file system check, [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")
If you have 'cable select' type IDE cables and you're also applying 'master' and 'slave' jumper settings, that's a 'belts and braces' approach, and it has been known to cause problems. Please use the correct jumper settings for the tyep of IDE cables your computer has.

Regards, Herman :)

---

### Post by Clarkey252 on 2009-03-08
Hmm would it affect it if i had

IDE0 - Red end
CD-ROM (slave) - black end
HDD (master) - grey end

Because reading what you put this suggests that it is getting confused as there is conflict between ide cable and jumper setting, however I can not reverse the way these are plugged in so would seting them both to cable select solve this and or confuse the BIOS/GRUB loader because of the switch (as i assume CD would become master and HDD slave)

Thanks for your help

---

### Post by Clarkey252 on 2009-03-08
Ok i ran the partition checker thingie and swapped the jumpers over to cable select for the CDrom and HDD still no good :(

---

### Post by Herman on 2009-03-08
:D Okay, can you boot your Ubuntu 'Desktop' Live CD for me please, and run a few commands from the terminal it it for me?

Can you please post the output you get after running the following command,
```
sudo fdisk -lu 
```

Also, can you click on your 'Places' menu for me and find your icon for mounting your hard-disk-installed-Ubuntu file system and click on it for me to mount it? 
(It might be in 'Places'-->'Removable Media' somewhere, or just in 'Places'.
It may be called something like '_*xx.x*_ GB Media'

Then you should be able to open your hard-disk-installed-Ubuntu's /boot/grub/menu.lst file with a command something like the following one,
```
gksudo gedit /media/*disc*/boot/grub/menu.lst
```
Where: '*disc*' is replaced with whatever the directory in media containing your hard-disk-installed-Ubuntu's file system (mount point) has been named.

If you would be able to post just the bottom half of that file (where all of the boot entries are), it should help me to help you. :D

Regards, Herman

---

### Post by Clarkey252 on 2009-03-08
sudo fdisk -lu gives:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   273506624   136753281    7  HPFS/NTFS
/dev/sda2       273506625   311596739    19045057+  83  Linux
/dev/sda3       311596740   311982299      192780   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1d0a955

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160055594    80027766    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b5d9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    78156224    39078081    7  HPFS/NTFS

```

and i assume you wanted

```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d601ec11-a996-4c84-8236-ca7284354d57 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d601ec11-a996-4c84-8236-ca7284354d57 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Clarkey252 on 2009-03-08
hmm am i right in thinking that the start under the heading boot means its looking to boot from there?
In which case i think we may have found the problem

Also if the above follows there shouldn't be anything bootable on the 3rd HDD (sdc1)
How would i fix this?

---

### Post by Herman on 2009-03-09
The boot flags are only relevant to Windows. 

I don't see any problem with your /boot/grub/menu.lst file, thank you for posting it. 
The information in your menu.lst agrees with fdisk output.

Maybe try re-installing GRUB using your Live CD now that your hard drive jumpers are set to cable select,
```
sudo grub
```
```
find /boot/grub/stage1
```
```
root (hd0,1)
```
```
setup (hd0)
```
```
quit
```
If that doesn't work, try downloading a super grub disk, [Super Grub Disk Official Webpage]("http://www.supergrubdisk.org/")

---

### Post by Clarkey252 on 2009-03-09
Ok so i think ive figured it out

when using the SuperGrub disc i got a 'not found' error when i tried to use the find command

and then when i tried to input the root (hd0,1) i got error 18 so i think becuase my computer is really old it has the 137GB limit on it (i read your page on it) and i have a 160GB HDD with linux mounted on the last 20GB (I know how unlucky).

So if this seams plausable then my question is can i re-order the partitions somehow?

Then if I can do that i'm guessing I would then have to re-install GRUB and every thing will be hunky-dory :D

---

### Post by Herman on 2009-03-09
:D  Hey, it sounds as if you've tried using your Super Grub Disk's [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")!  Very good! That's the best way to either get your computer to boot or to find out why you're having difficulties.

It's possible that your thinking is correct. 
You can re-order your partitions using GParted Partition Editor in your Ubuntu Live CD or in some other Linux Live CD, including GParted Live CD or Parted Magic which are live CDs dedicated mainly to GParted.
However, it will be a slow process. If you wanted to add more hard disk space to an established operating system in which you've invested some time customizing it and installing all your favorite software already and so on, it would be worth copying the entire Ubuntu partition and pasting it to the other end of your hard disk. 
Then if you have Hardy Heron or older, you'd have a different partition number and you'd need to edit some files to get Ubuntu working, but that wouldn't be too difficult.
If you wanted to avoid editing files, you could 'leapfrog' your Ubuntu partition twice, in order to end up with it in a different location, but with it's original partition number back again.
If you have Intrepid Ibex or newer, your job will be a lot simpler since the boot loader (GRUB), and your /etc/fstab files both make total use of file system UUID numbers. You would only need to resize your first partition and copy & paste your Ubuntu partition in the free space. You'd probably just need to re-install GRUB.
I can tell by your /boot/grub/menu.lst file that you have Hardy Heron. I use that as mt main OS myself, since it's the LTS version and the newer versions of Ubuntu are too advanced for some of my favorite programs.

Since it's a brand new installation and you haven't invested a lot of time and creativity into it yet, it's expendable and it will only take you half an hour to re-install. It would be quicker for you to resize your first partion from the start of the hard disk, and install Ubuntu again.

Another idea, but one that will require more learning, would be to make a separate /boot partition. You'd only need to resize your first partition by a few GB to make room for a separate /boot partition in your particular circumstances. [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").

Before you go to too much trouble though, I think it might be wise to check your IDE cables. They only cost a dollar or so each and I remember not so long ago I had one with the ribbon partially torn away from a plug. It was probably from my own rough handling, and the damage wasn't easy to see without a close inspection. It had me scartching my head for a while before I discovered that. It was an easy fix.
Another problem I helped someone with not so long ago was caused by an IDE cable that was sold to them that was too long. IDE cables should be 69cm or shorter for an 80 conductor IDE ribbon cable. You may be able to buy longer ones, but they can be problematic. Can you boot Windows from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")?
If so then it's likely only a Ubuntu problem, not your IDE cable. It's possible that your 137 GB theory is quite possibly correct.

Moving Windows to make room at the start of the hard disk hasn't hurt any Windows installations I've tried it on. Many people are superstitious about that an there's a widespread beleif that Windows will only boot if it is located at the beginning of the hard disk. I haven't found that to be true. Windows can be located anywhere, but it easier if you preserve the partition number. Then it iwll boot without the need for editing any files. 
If the partition number does get changed you only need to edit boot.ini of you have XP. For Vista I'm not so sure, but I think it can find itself a lot easier, but you mustn't copy it from one hard disk to another unless you make a backup of the first 446 bytes of the MBR (including the 'disk signature'), and copy that to the new hard disk as well.
 [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

---

### Post by Clarkey252 on 2009-03-09
Hey thanks for the advice I've deleted the Linux partition and I'm moving the windows one over so I have a free 20GB at the start to put Linux back on.

If that doesn't work i may hang myself :D (nah not really probably just format the entire drive! Windows install is fairly recent but still don't wanna lose it)

I don't see how it would be an IDE problem as all of the data is reading/writing fine its only the boot data that seems to be messed up.

And yes you were right the ETA is about 3:20 so going to do something else for a while lol 

Fingers Crossed :mrgreen:

EDIT: 
NOTE:Yes you are correct i'm using 8.04 as its an old disc and i can't be bothered / don't have the resources to burn an up-to-date one.

---

### Post by Clarkey252 on 2009-03-10
YYYEEEEEEYYYYY FIXED!!!

My theory about the limit was correct :mrgreen: thanks for all of your help Herman moving the partition over and then installing fresh linux worked a treat thankyou

Now if you could possibly suggest some ideas to make my linux stay more pleasureable (i.e. doing stuff you can't do in windaz) then i would apreciate it, as i want to learn about linux and what makes it great/different from windows (apart from the obvious).

Thanks again
If there is anything i can do for you please name it - not that I have many skills to offer (particularly Linux ones) =D

---

### Post by Herman on 2009-03-10
:D Well done! Congratulations! 

Things we can do in Linux that can't be done in Windows?
That will take more than one post as the list is very long and I don't have the amount of continuous time on my hands to write you all I'd like to on this subject all at once.  ;)

I'd start by looking down in the lower right-hand corner of my screen and finding two little rectangles in the bottom panel. (Windows users call it a 'task bar', if I remember correctly). When you hover your mouse over these rectangles, the words 'Switch between workspaces' may appear. I like to right-click on then and select 'preferences', and then change the number of workspaces in 'Workspace Switcher Preferences' to about 12.
Now, open any application from your 'Applications' menus. You might open 'Office' -->'Open Office.org Spreadsheet' for example. Next, go back down to your Workspace Switcher and click on a different workspace. You may open another program in that workspace and leave that open and start another one in the next workspace. We can also drag and drop open programs from one workspace to another if we have 'System'--'Preferences'-->'Desktop Effects' set to it's most conservative setting, (my favorite, even though I do have a reasonable graphics card). I know that you're probably used to 'minimizing an open window to the taskbar', in Windows. In Linux we can do that too, but I prefer to switch to another workspace instead. Workspaces are something I really miss whenever I boot into any Windows system.

---

### Post by Herman on 2009-03-10
That brings me to the next point, internet safety.
You'll notice I didn't call Windows an 'Operating System', that's because of the number of Windows systems I get that don't actually operate. (I fix computers for people for a hobby. I'm quite busy, it's almost ready to become a small business).  Windows does make nice operating systems when they're newly installed, but unfortunately there are a lot of viruses and other nasty malicious programs out there that can infect Windows and ruin the user's computer experience. Windows users may not realize it until they stand back, but it takes up quite a lot of the user's time to learn how to avoid getting viruses, being careful not to visit and 'dangerous sites', (as if people will know in advance) and which anti-this-and-that, cleaners and preeners they need to buy and then spend the most of their computer time updating and running scans with. 
There are even a lot of fake anti-virus programs now, and registry checkers and so on, that are actually the viruses themselves, (wolves in sheep's clothing), which people install and actually pay for, only to find they do things that are not very nice at all.
With Linux, the user is freed from all those worries. We don't need to try to guess which programs we safe and which are not, ( but claim they are). As long as we install software from the recommended Ubuntu sources, we're absolutely safe. 

Linux users can get right to work or play, without needing to wait while half a dozen programs update and require a reboot before they can settle down and use the operating system. We don't have an antivirus program running silently in the background using up resources and lugging the computer down.

Even the well known and trusted antivirus programs aren't able to offer complete protection for Windows, because new viruses keep appearing every day, and a virus can exist and circulate for quite a long time before the antivirus people learn about it and come up with a remedy and removal method. That's a fact that they'd rather keep quiet about.

If you dual boot, and refrain from letting Windows come into contact with the internet, (except maybe for 'trusted sites' like Windows Update and the antivirus updates and so on, you'll find out that Windows will remain clean, and after one or two anti-adware scans, you won't find any more internet trash in Windows at all. You can safely continue to use Windows problem-free for the life of the computer if you don't allow it on the internet.

We can go anywhere on the internet we want in Ubuntu, even virus driveby download sites, and Ubuntu will remain unaffected. I have tried it.

---

### Post by Herman on 2009-03-11
There's only one Ubuntu. There isn't a poor man's edition, mediocre and an elite version to choose between. Ubuntu gives the best open source software to everyone.

Ubuntu is ready to go as soon as you install it. 
Ubuntu comes with Open Office .org Presentation, Spreadsheet and Word Processor already installed. You don't need to go and buy separate software to get Ubuntu to be able to do something.
With Open Office.org, you can open up word documents and spreadsheets and so on in file formats made with Windows apps. 
You can also create files and save them as Windows formats, so that you can share your documents with friends who have Windows. Windows programs can't save in Linux formats or open Linux file formats, so when you use Linux, it's like having the 'master key'.

---

### Post by Herman on 2009-03-11
Ubuntu isn't handicapped with anti -piracy boobytraps, so if anything ever does go wrong with it, it's able to be repaired, often by simply copying and pasting to replace damaged or deleted files. 

We can easily move a hard drive with Ubuntu in it from one computer to another and it will detect the new hardware, automatically configure itself, and boot, it won't freak out and think it's being pirated and disable itself.

That's useful for hard disks that might have sensitive information on them that you want to take home with you from the office. Some computers now have easily removable hard drives. You can just take the hard drive home instead of carrying a whole laptop and pop it into the computer at home if you want to complete some work at home.
USB installations are popular for that, I don't actually recommend carrying hard disks around, I think they're safer when they're screwed in to a computer. Flash memory though, is much more robust. For now, USB flash memory sticks are getting larger and they're quite affordable. Many people like to have Ubuntu installed in a USB flash memory stick. Ubuntu is already way ahead of it's time when it comes to being installed in portable devices. I suspect that's why we have UUID numbers in /etc/fstab and in GRUB now, in the latest versions of Ubuntu.
In the future I think that USB SSD disks will get popular, especially when USB3 comes out. USB3 will be very fast. 
That's something you can't do with Windows but you can easily do with Ubuntu, and it's going to be a very important reason for many people to switch to Ubuntu when the hardware technology catches up.

---

### Post by Herman on 2009-03-11
If you're a traveller, such as a travelling salesman or anyone who travels a lot, you may have take your laptop or USB device with you and you may want to use printers of various makes and models at various locations wherever you may go.
 Ubuntu is for you. You can plug a wide range of printers into a computer with Ubuntu in it and you don't need to bother people to go looking for the driver CD specific for that particular printer. Ubuntu probably already has a driver that will be able to make the printer work for you. 
Just go 'System'-->'Administration'--'Printing', and click on 'New Printer', and navigate to the printer's manufacturer and printer model and in a few minutes you''l be all set up to print with just about any printer you might find.

Many other hardware devices work in Ubuntu without the need for any setup CD, such as digital cameras and scanners and various other gadgets. There are some things you might  that might not work (yet), but it's amazing how many things do work pretty much automatically in Ubuntu.

---

### Post by Herman on 2009-03-11
Because Ubuntu is immune to viruses, and isn't handicapped with anti-piracy booby traps so we can use it to boot any computer, it's useful for finding, diagnosing and sometimes fixing problems in other computers.

If you're working from Ubuntu installed in a USB flash memory stick, you can have AVG virus scanner installed, and scan a sick or dead Windows computer to see what happend to it, [HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064&highlight=avg+free+32+bit") or [[64-bit] Install AVG free and pro anti-virus for Ubuntu 64-bit]("http://ubuntuforums.org/showthread.php?t=622967&highlight=avg+free+32+bit")

You may be trying to follow some how-to on the internet that advises you to edit the Windows Registry, to fix a system infected with some kind of spyware.  you can have a little program called [chntpw]("http://home.eunet.no/pnordahl/ntpasswd/") installed, with which you can edit the Windows registry o\in a disabled Windows system.

Other programs that might be useful in a Ubuntu USB flash memory stick are TestDisk, a program for fixing a corrupted partition table, and recovering deleted partitions, and PhotoRec comes with it, for file recovery.

Partimage or the dd command can copy and restore partitions and operating systems.

I know you can buy proprietary programs for doing some of those things, but I don't know how you use them if Windows is already dead, except from Linux.

---

### Post by kwpowers on 2009-03-11
what happened to grub between hardy and intrepid?  I have a hardy install where grub boots fine with external drives attached preboot. (I always make it a habit of installing without external drives to ensure the correct drive is installed to) Now with intrepid I get an error cannot find boot partition unless I connect the drives after the boot partition has been located.  I read the link at the top of the thread and see only that the hardware must be hacked in some way. This is not user friendly.  I have been using ubuntu as my main distro since novell bought SuSe and find it to be rock solid  with a few issues along the way.  This is in my opinion a big issue. The boot loader should  be able to adjust to changes like this without user intervention!! Getting in to use the computer breaks, and for the novice user; this has just rendered the hardware useless unless they reformat and start over.  The boot loader is the most important part of any operating system and must always work in all situations, or on failure immediately offer a way to fix the problem for a first time users experience level.  With the advent of memory sticks External drives etc. the boot loader should behave as if it were a live distro searching all partitions and create a list if  it cannot find the default list when it starts.  Also the loader should ask if this new list should be saved when a choice has been made.

---

### Post by Herman on 2009-03-11
> what happened to grub between hardy and intrepid? Ubuntu's GRUB had some improvements added so that GRUB will look for the boot partition by the file system UUID number instead of the way the hard drives are numbered in the BIOS. In my opinion it's a wonderful improvement and should just about eliminate the incidence of GRUB Error 17.
In my computer I can even boot the correct Ubuntu installation in a daisy chain of USB flash memory sticks and USB hubs, even when Ubuntu is installed in one of the last flash memory sticks. (It doesn't matter what drive Ubuntu might happen to be in).
> I have a hardy install where grub boots fine with external drives attached preboot. (I always make it a habit of installing without external drives to ensure the correct drive is installed to) Now with intrepid I get an error cannot find boot partition unless I connect the drives after the boot partition has been located. I don't know without knowing more about your computer first. That seems very strange to me. If this is true then maybe the BIOS of your motherboard is different to the majority of other computers? I have one laptop here I'm fixing for someone which likes to list an external flash memory stick as number 1 hard drive, while the majority of other computers normally list a USB device last after IDE and SATA disks. It's unfortunate that all motherboard and BIOS manufacturers can't have a meeting and agree on how drives should be listed. Until that happens, we have to improvise the best we can. Maybe when EFI replaces the BIOS things will change.[Extensible Firmware Interface - Wikipedia,  the free encyclopedia]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") > This is in my opinion a big issue. The boot loader should be able to adjust to changes like this without user intervention!! Getting in to use the computer breaks, and for the novice user; this has just rendered the hardware useless unless they reformat and start over. Ah, I think you have misunderstood, did you read the thread properly? It is only when the computer has been assembled wrongly and the hard drives jumper settings are not placed correctly that the inside of the computer needs to be accessed. 
Normally, if the computer is new, it would already be set up correctly, or if hard drives have been added by a qualified and reputable computer technician, the jumpers should be set up and the IDE cables plugged in correctly.
It is only when users add their own hard drives themselves, without a proper knowledge of the IDE interface, or following bad advice that it needs to be corrected.
In that case. presumably the user has done the mis-configuring themselves, so the user should be able to do it again, but correctly this time. 
If the user is not confident, they should take their machine to someone who knows what they are doing. Even some technicians plug in and jumper IDE hard drives wrongly sometimes though.

There is another way of correcting GRUB Error 17, you can wrongly edit the menu.lst file to match the wrong hardware setup and re-install GRUB, that will probably work, but it can get a little bit complicated and messy.
> The boot loader is the most important part of any operating system and must always work in all situations, I agree. :D
>  or on failure immediately offer a way to fix the problem for a first time users experience level. A boot loader needs to be able fix hardware issues? 
>  With the advent of memory sticks External drives etc. the boot loader should behave as if it were a live distro searching all partitions and create a list if it cannot find the default list when it starts. You should try running the uuid command from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). GRUB legacy can detect operating systems and you can boot them, but it doesn't add them the the menu.lst file, you need to do that yourself by manually editing the file.
The idea of using file system UUID numbers in Intrepid's GRUB is a good one for USB flash memory sticks, and it works well for me and almost everyone else. Your case is the first I've read that's different. 
>  Also the loader should ask if this new list should be saved when a choice has been made. GRUB 2 can do that, when you run the grub-install command if GRUB 2 is installed in Ubuntu, it will scan the hard disks for all operating systems and update the /boot/grub/grub.cfg file. That doesn't happen unless the user issues that command, after the operating system is up and running. I agree with you, it would be cool if a boot loader could automatically configure itself on the fly at each boot-up. 

By the way, I'm not a developer, I'm only another computer user who has spent more time trying to understand GRUB than most others. I'm a GRUB supporter,  in something the same way as a person might support a favorite football team. I support GRUB verbally, but I don't actually represent GRUB in any formal capacity. I just try to help people understand GRUB so they can use GRUB better.

If you are a programmer and you have ideas about how to implement some of the suggestions you have made, you should look for  the [GRUB 2]("http://www.gnu.org/software/grub/grub-2.en.html") developers, they might appreciate your help.
If you are another computer user, (like me), you are welcome to ask me for more comments if you like and I'll try to help. Maybe there is more I can explain? 
Regards, Herman  :D

---

