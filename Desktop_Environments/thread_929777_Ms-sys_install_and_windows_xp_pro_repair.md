---
title: "Ms-sys install and windows xp pro repair"
date: 2008-09-25
forum: Desktop Environments
---

### Post by Delinquentme on 2008-09-25
hey all!

so I've had a Ubuntu live CD laying around my house for a while now and thanks to windows...

NOW I HAVE A REASON TO TRY IT OUT!!

ha ha so i loaded it up and absolutely LOVE it.  

SO to my question:

i did some googling and found that theres a program called "ms-sys" that can be used to fix windows problems which is fantastic cause thats what i have :P

that being said the walk through had me enable the "universe" repository then open the terminal and give it this line:

sudo apt-get install ms-sys 

so i hit ENTER and get this:

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ 

so I'm dead in the water here

additionally i checked out some manual downloads( lol I'm new to Ubuntu and I'm starting to think that the terminal line IS the manual way to d/l and install so maybe I'm using the wrong terms here)

but the Ubuntu site recommended aptitude or synaptic as a "package manager" can anyone recommend using either one of these

or better yet explain whats going on with the terminal??

thanks so much 

:guitar:
rock on
:lolflag:

---

### Post by pytheas22 on 2008-09-25
The package for ms-sys is not available on Ubuntu 8.04, apparently because [Microsoft says that it infringes on its copyrights]("https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349").  That's why you're getting an error about it not being found.

However the package still appears to be available in older versions of Ubuntu.  If you go [here]("http://packages.ubuntu.com/gutsy/ms-sys"), you can download the package manually (click one of the links at the bottom of the page for amd64, i386 or ppc depending on the architecture of your computer, then choose a download link and the package will be saved to your desktop).  Then double-click on the icon for the package and it should install.  If the installer tells you that the package can't be installed for some reason, let us know.

FYI, this is not the way that you should generally install software in Ubuntu--it's usually a lot easier and better to use 'apt-get' or its graphical version, Synaptic (System>Administration) menu.  But in this case, this method is probably the easiest way of getting ms-sys installed.

---

### Post by Delinquentme on 2008-09-25
thanks for the help!

so 95% of the time to find a program i want for Ubuntu ill simply be using apt-get or synaptic to download programs??

thats SO much SMARTER!!

PS

using this to REPAIR a windows install... I'm running Ubuntu on a live CD.  Does this change anything? IE should i be worried about installing program?

and its been so long since I messed with the hardware on this comp... can i check the hardware properties ( right click my computer > properties in windows) to figure out the architecture?

i THOUGHT it was an AMD 64 but I D/Led the ms-sys_2.1.0-1_amd64.deb and opened it with GDebi Package Installer and it says i have the wrong architecture

suggestions?

---

### Post by pytheas22 on 2008-09-25
> so 95% of the time to find a program i want for Ubuntu ill simply be using apt-get or synaptic to download programs??

Yes, it's easier, safer (because you're getting software from a trusted centralized source, not some random website), and makes updates easier (you can update all of the hundreds of programs installed on your computer in one click via Ubuntu updates, whereas Windows updates only work for Microsoft software).

> using this to REPAIR a windows install... I'm running Ubuntu on a live CD. Does this change anything? IE should i be worried about installing program?

I've never used ms-sys so I can't vouch for its effectiveness in actually repairing Windows, but no, there's no reason to be concerned about installing the program itself.  Just keep in mind that anything you install while running the live CD is not permanent--the next time you reboot your computer, it will all be gone, because the live CD only runs in RAM, not using your hard drive.

> and its been so long since I messed with the hardware on this comp... can i check the hardware properties ( right click my computer > properties in windows) to figure out the architecture?

You can get all this information using the command-line, but for a nice graphical interface, try installing 'hardinfo' by typing:
```

sudo apt-get install hardinfo
```

After that, you'll find a utility at System>Preferences>System Profiler and Benchmarker that has similar functionality to the stuff in Windows, and will tell you about the hardware on your machine.
> 
i THOUGHT it was an AMD 64 but I D/Led the ms-sys_2.1.0-1_amd64.deb and opened it with GDebi Package Installer and it says i have the wrong architecture

Try installing the i386 package.  Even if your processor is 64-bit, the live CD kernel is probably only 32-bit.  If you wanted to use 64-bit Linux, you would have to burn the 64-bit version of Ubuntu.

---

### Post by caljohnsmith on 2008-09-25
Delinquentme, the ms-sys package is typically for writing a Microsoft compatible MBR (master boot record), and it also has a few other boot record related features. I doubt that is what you are looking for, but I could be wrong. :) What exactly is wrong with your Windows? What happens when you try to boot it? If you give more info about that, we might be able to suggest some ways to help repair your Windows. Also, do you have a Windows Install CD?

---

### Post by Delinquentme on 2008-09-25
cal

so FIRST off lol i hate to add one more thing to make this more complex...

i have a modded version of windows called windowsXP "Dark Edition" so im trying to get THAT repaired

when i go to boot up it goes through the abit screen ( my mobo) and then to "Verifying DMi Pool data...." which it clears to

"Boot from CD: ( i just have that as a default in my bios)

and the it ENDS on  DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER



suggestions?

---

### Post by Delinquentme on 2008-09-26
BUMP did de le ump bump

---

### Post by Delinquentme on 2008-09-26
Oh and another question

assuming that my current windwos "dark edition" isn't working

is it a bad idea to install ubuntu as a dual boot while this OS in non-functional??

---

### Post by pytheas22 on 2008-09-26
> 
assuming that my current windwos "dark edition" isn't working

is it a bad idea to install ubuntu as a dual boot while this OS in non-functional?? 

Installing Ubuntu as dual-boot shouldn't make Windows any worse (in fact there's a small chance that it could resolve the whole problem, depending on where exactly the boot issue lies...but don't assume that it will).  You will have to repartition the disk, which carries a small chance of corrupting your Windows system (that's why it's always recommended to back up before installing Ubuntu), but really the risk is very very small.
> 
and the it ENDS on DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Did you try inserting your Windows installation CD here to see what happens?

Also, isn't XP Dark Edition just an interface modification (that's what it looked like to me after some googling)?  It doesn't change any of the underlying system, just the colors, theme, graphics, etc., right?

---

### Post by Delinquentme on 2008-09-26
yeah i inserted the actual windows xp pro disk and the dark edition "power pack" disk

the windows XP pro (MS certified disk):
opens into the windows setup and loads all the files, bringing me to the install / repair option ( enter / r respectively) and i get this after hitting r:
```

Microsoft WindowsXP (TM) Recovery Console.
The Recovery COnsole provides system repair and recovery functionality.
type EXIT to quit the Recovery Console and restart the computer
The Path or file specified is not valid.
C:/>

```
and im left with the c propt...



the windows dark loads up to the main screen with these options:
```

Boot from hard disk
Boot function
Setup windows Dark Edition v.6

```

so i click the setup dark edition, which gives me these options:

```

Original version
SATA/RAID driver version
All driver ( without sata/raid) version
All driver version
Full option version
Repair version
Repair version ( sata/raid driver)

```

I click on "Repair version"

so ti brings me to the blue windows setup screen and everything finishes loading

and i get to the 
install / repair option ( enter / r respectively) and i hit r

then it gives me the same:
```

Microsoft WindowsXP (TM) Recovery Console.
The Recovery COnsole provides system repair and recovery functionality.
type EXIT to quit the Recovery Console and restart the computer
The Path or file specified is not valid.
C:/>

```

maybe i should be getting a hint here because its the exact same error for both install CDS??

---

### Post by Delinquentme on 2008-09-26
oh and how do i setup a partition on the HD for Ubuntu?

can this be done off the live CD?

---

### Post by Delinquentme on 2008-09-26
NEW update!
so i get this error on the running of the dark edition that says:

Error : partition table invalid or corrupt
Command: Chainloader (hd0,0)+1

im doing some googling as we speak but just thought id keep yall up on the case of the disappearing OS :P

---

### Post by pytheas22 on 2008-09-27
It might help to boot to the Windows CD (either one) and at the command-prompt, type:
```

fixmbr
```

That program is *supposed* to be able to detect errors with the boot record and fix them.  As a disclaimer, I've never once in my life managed to get the recovery console of the Windows CD to actually repair anything, but in principle, Microsoft says it can.
> 
oh and how do i setup a partition on the HD for Ubuntu?

If you boot to the live CD and click the icon on the desktop called "Install," it will walk you through the partitioning stuff as well as everything else required to install Ubuntu to hard disk.

---

### Post by Delinquentme on 2008-09-27
hahah yeah so i just tried it annnnnndd my computer just stares at me drooling :P

is all i have to type:
fixmbr?

cause that doesnt even return information

soo after doing a little footwork i found this microsoft page on fixmbr

[http://support.microsoft.com/kb/307654/#3](http://support.microsoft.com/kb/307654/#3)
so i took that and ran a few of the commands...
it seems that dos just doesn't see the HD as even being installed...

additionally
and i yanked out the primary and plugged it into my vantec hard drive to usb adapter

annnd well it powers up but it doesn't load up it just spins...

so how do i get my computer to recognize that somethings plugged in... / make the HD readable

---

### Post by pytheas22 on 2008-09-28
To be honest I'm not really sure where to go next.  Unfortunately I don't know very much about fixing Windows, and your problem is 100% Windows (or possibly even hardware failure, if Windows doesn't want to see your hard disk at all).  Do you have any tech support available that you could call?  Or you may want to try asking for help in a forum like [Microsoft's support forum]("http://forums.microsoft.com/TechNet/default.aspx?SiteID=17").

I don't mean to push you out of here without an answer; I just don't want to keep wasting your time, since at this point I don't think I will be able to give you any more useful suggestions.

Of course, there are plenty of other Ubuntu users who do know Windows, so hopefully someone besides me might be able to help...

And you could always just install Ubuntu to replace your broken Windows :)

---

### Post by Delinquentme on 2008-09-30
actually i think i narrowed it down to some kinda problem with my primary HD

I plugged it into my laptop via a vantec IDE to USB adapter and it shows up in the device manager but not in windows explorer...

pretty peculiar 

also i went to run the disk and it said that it has a bad boot partition

ADDITIONALLY i ran gparted on the computer and it only sees the sata raids that i have setup and not the primary install HD

so righ tnow my task is getting this HD to come up and be readable in either ubuntu /gparted or with the plug and play IDE to USB...

---

### Post by Delinquentme on 2008-09-30
Oh PS...

is "mounting" the term i want to use when talking about getting a OS to recognize a HD being plugged in?

---

### Post by Delinquentme on 2008-09-30
so i found this sweet little walk through on how to work with an unallocated disk:

[http://kbserver.netgear.com/kb_web_files/n101625.asp](http://kbserver.netgear.com/kb_web_files/n101625.asp)

so this WOULD have fixed my problem but when i run through the steps it says that my disk is not initialized...

im guessing this means the disk is not recognized as having a file type? IE FAT / NTFS???

---

### Post by pytheas22 on 2008-09-30
> 
is "mounting" the term i want to use when talking about getting a OS to recognize a HD being plugged in?

When you 'mount' a file system, it means that you initialize it in order for the operating system to use it.  In other words, if you want to read and/or write to and from a disk or partition, it needs to be mounted first.

Note that you can have disks present and "recognized" by the system, but not mounted.  This just means that the operating system detects that there's a disk present, but it's not doing anything with it--the disk is left idle, since it can't be written or read until it's mounted.

If no operating system is seeing that your hard disk exists at all, which seems to be what's going on for you, then I'd suspect issues with hardware.  gparted should at least be able to see that the disk exists as long as it's connected to the computer.  So there could be hardware failure either with the disk itself, with the cable connecting it to the computer, or with the connectors on your motherboard.

If the system sees the disk but you can't mount its files for some reason, that's generally just a software issue, but I don't think that represents your situation.

---

### Post by Delinquentme on 2008-09-30
so with a little further tinkering i've gotten windows vista to recognize it as an unknown uninitialized HD (via IDE to USB connector)  AND GParted live to recognize it with the same connection...

gparted doesn't give me any options as the HD is uninitialized

so is there a way to repair i guess it would be called "initiation" of a HD with gparted

( i know the HD is windows XP formatted )

---

### Post by pytheas22 on 2008-10-01
Linux can't repair NTFS (Windows XP) file systems, because it's a proprietary and undocumented file system.  gparted could erase the disk and create a new partition, but you'd lose all the data that way.  But Windows should be able to repair the file system with the 'chkdsk' and/or 'fixmbr' programs; you can find information on how to use them online.

---

### Post by Delinquentme on 2008-10-02
SOOO i've decided to just blow away the OS and reinstall

this SHOULD be easy but now my HD isnt' letting me format it lol

i used the terminal command:
dd if=/dev/zero of=/dev/sdb

and get this back:
dd: opening 'dev/sdb/: Permission denied.

WTF?!

lol my HD is saying it doesnt want to be deleted now??

---

### Post by Delinquentme on 2008-10-02
i also saw this command:

```
shred -vfz -n (drive)
```

where n = number of overwrites
from thread t=817882


could someone tell me how to state the drive in the command 

i tried:

```
shred -vfz -1 /dev/sdb 
```

annnddd that didnt give me the results i was looking for lol

---

### Post by pytheas22 on 2008-10-02
I'm not sure, but maybe you need to specify a partition.  Does:
```

sudo shred -vfz -1 /dev/sdb0
```

do anything?  Also, are you sure that you're specifying the correct drive?  It might not be named sdb--it could be hda, hdb (hd* is for older SCSI drives, I think; SATA drives are named sd*), sdc, or something else.  You can look in your /dev directory to see which names are being assigned to the various connected drives, and then you'll have to use hit or miss to figure out which one is the one you want to shred.

Also, are you sure you can't just use gparted to format the drive?  'shred' does a very low-level and thorough format that's intended for completely wiping drives that contain sensitive data (so that no one can find them in the trash and recover files off of them, etc.), and generally isn't necessary if you just want to format a file system.

---

### Post by tmcmulli on 2008-11-04
Not sure if this matters, I just hosed my MBR, and used a 8.10 Live CD and the ms-sys package from Debian to fix it:  [http://packages.debian.org/etch/ms-sys](http://packages.debian.org/etch/ms-sys) and then follow this tutorial:  [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

