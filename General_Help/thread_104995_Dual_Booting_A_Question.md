---
title: "Dual Booting: A Question"
date: 2005-12-17
forum: General Help
---

### Post by Tmyers on 2005-12-17
On my PC, I currently I am running Ubuntu. Steam and Many other games are a hassle with wine and they honestly run better in a windows enviornment. So my question is: Can I partition my harddrive with something like GU Parted, and install windows alongside ubuntu? I know you can partition in windows and install ubuntu second, but is it possible to do it the other way around. Will windows clear the other partitions?

Im asking because it's not often that someone wants to install windows with ubuntu already installed. It's usually the other way around. Dont get me wrong, I love ubuntu, but gaming in it for me is becoming a problem. I cant seem to get any of them running with wine. If I eventually figure it out Ill be happy to delete the windows partition and use ubuntu 100%. But for now I think I need windows.

---

### Post by codyrinas on 2005-12-17
dude I got the same question, and was told not to trust the GRUB loader on the primary HDD cause it could lose your windows XP...I would love to know how to create a dualboot from 2 HDDs...so ya that would be helpful information.

---

### Post by Hancoque on 2005-12-17
As far as I know Windows will always overwrite the master boot record (MBR) during the installation. That may render your Linux partition unbootable. Windows won't delete the Linux partitions though, if you don't tell it to do so. You should backup the boot sector that currently makes Linux bootable into a file which you can use from now on to boot Linux from Windows. But as Linux seems to be your main system I think you want it the other way round: that you can boot Windows from GREP.

First make sure you can boot Linux from its partition rather then the MBR. Then you install Windows (make sure you don't tell Windows to delete your Linux partitions during installation). After booting into Windows the first time use the Disk Management (Administrative Tools -> Computer Management -> Disk Management) in Windows to set the Linux boot partition as the active partition. After a reboot your computer should automatically boot Linux again. I dunno if Ubuntu automatically adds Windows to the boot menu or how to do it if not. Maybe you have to extract the Windows boot sector like you have to if you want to boot Linux from Windows' boot manager. If the latter is the case than you should do that before you reboot into Linux. Otherwise you may not be able to boot your Windows anymore. But you can always make Windows bootable again by changing the active partition.

---

### Post by Tmyers on 2005-12-17
Alright, Ill give that a shot.

But I need to know a few things:

1. How can I check if ubuntu is bootable from it's partition

2. What would be the best method of partitioning ubuntu without destroying all of my data? GNU Parted doesn't want to work for me. If parted is your answer, could you please elaborate on how to use it. Or give me a link to a tutorial that will?

(Free Programs Please: Im only 15 and quite stubborn when it comes to buying software)

---

### Post by aysiu on 2005-12-17
[QUOTE=codyrinas]dude I got the same question, and was told not to trust the GRUB loader on the primary HDD cause it could lose your windows XP[/QUOTE] Actually, it's the other way around. If you put Ubuntu's Grub on the MBR, it will most likely add Windows XP automatically to the boot menu.

If, however, you don't install Grub to the MBR, I can guarantee you Windows' boot.ini file will not recognize Ubuntu... and Windows in general will not acknowledge you have another OS present. Under Disk Management, Ubuntu will appear as only a "healthy partition" of an unknown type.

For more on dual-booting, go here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by bscbrit on 2005-12-17
I am not aware of grub ever 'losing' the windows partition, but perhaps someone can point to a thread about this.

It is always tricky installing windows after linux because windows does not believe in sharing.  But it can be done.

Install windows, and it will overwrite the contents of grub.  But, once you have windows up and running, if you then enter linux recovery (or is it repair?) mode on the cd it can be persuaded to reinstall grub again and it will automatically include an entry for the new windows partition.  Sorry I can't be more precise because it is not something that I have done for several years.

Keeping the 2 OS on different drives is an excellent idea but it does not affect the installation process.  There will have to be a 'menu' somewhere asking which OS you want to start and, from a software point of view, whether that partition is on one drive or another doesn't make any difference.

---

### Post by Hancoque on 2005-12-17
[QUOTE=aysiu]If, however, you don't install Grub to the MBR, I can guarantee you Windows' boot.ini file will not recognize Ubuntu... and Windows in general will not acknowledge you have another OS present. Under Disk Management, Ubuntu will appear as only a "healthy partition" of an unknown type.[/QUOTE]Yes, not automatically. You have to extract the Linux boot sector as a file, put it to a place where Windows can access it at boot time and add an entry to the boot.ini. But then everything works fine. Windows can boot Linux and the MBR can be left untouched by Linux. But as I said, if your main system is Linux then you might not want it this way.

---

### Post by Tmyers on 2005-12-17
From all of your helpful posts this is what I understand

[LIST]
I need to resize my ubuntu partition and create a windows one (ubuntu already created swap space when it was installed - Question: Which format does the new partition need to be in? Fat32 so it can swap or can XP only handle NTFS?)
[/list]
[list]
Then I can proceed to install windows, selecting the newley created partition when prompted.[/list]

[list]After this I need to go to Disk Management and select my ubuntu partition (which should show as healthy partition)[/list]

[list]When I reboot ubuntu will boot[/list]


After ubuntu is booted what do i need to do to get the bootloader (im assuming grub) reinstalled so that it picks up XP and ubuntu? Synaptic > Search Grub & Install?

Im new at linux so be patient with me :)

---

### Post by aysiu on 2005-12-17
[QUOTE=Tmyers]
I need to resize my ubuntu partition and create a windows one (ubuntu already created swap space when it was installed - Question: Which format does the new partition need to be in? Fat32 so it can swap or can XP only handle NTFS?)[/quote] XP will run better on NTFS, but you may want to create a separate (third) FAT32 partition to share files on.

> 
Then I can proceed to install windows, selecting the newley created partition when prompted. Yes.

> After this I need to go to Disk Management and select my ubuntu partition (which should show as healthy partition) No. Selecting it does nothing. Windows **does not recognize Ubuntu** as an operating system.

> 
When I reboot ubuntu will boot No. When you reboot, Windows will have taken over the MBR with absolutely no trace of Ubuntu. You'll have to reinstall Grub on the MBR to get it booting properly.

---

### Post by Tmyers on 2005-12-17
Thank you aysiu, your being very helpful!

Hopefully this is my last question: How do I go about reinstalling Grub on the MBR?

---

### Post by aysiu on 2005-12-17
[QUOTE=Tmyers]How do I go about reinstalling Grub on the MBR?[/QUOTE] This thread may help: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Tmyers on 2005-12-17
I think I can do that, Thanks for your help everyone!

Im going to make some partitions and load up this thread on another pc, so I dont make any mistakes...

---

### Post by Tmyers on 2005-12-17
I promised that would be my last question, but im having trouble finding a partitioner for ubuntu that I can get working...what are you suggestions? (free software please)

---

### Post by smpgavane on 2005-12-17
Sir I Have P4ht Desktop With Winxpsp2
I Want To Install Ubuntu 5.10 On The Same 
Guide Me In Details
Sanjay

---

### Post by aysiu on 2005-12-17
[QUOTE=Tmyers]I promised that would be my last question, but im having trouble finding a partitioner for ubuntu that I can get working...what are you suggestions? (free software please)[/QUOTE] To partition, you're going to need a CD. I know this seems weird, but I'd highly recommend the first installer CD of Mandriva. You don't actually have to *install* Mandriva. Just boot up the CD, go through partitioning with DiskDrake and then reboot your computer and continue.

Others will most certainly recommend the Ubuntu live CD with GParted or Knoppix with QTParted, but I've found that sometimes GParted or QTParted will limit your options (gray them out in the context menu) even if you don't have the partitions mounted.

---

### Post by LoclynGrey on 2005-12-17
> Sir I Have P4ht Desktop With Winxpsp2
I Want To Install Ubuntu 5.10 On The Same
Guide Me In Details
Sanjay

Best thing to do here mate is type, "dual booting setup" in this forums search and do some reading. :)

---

### Post by aysiu on 2005-12-17
[QUOTE=LoclynGrey]Best thing to do here mate is type, "dual booting setup" in this forums search and do some reading. :)[/QUOTE] Actually, the best thing to do is go to this page:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Tmyers on 2005-12-17
If I remember correctly, after you adjust partition sizes in the ubuntu installer, it then immediately proceeds to install ubuntu's core files. How can I just adjust the partition sizes and exit. Is it possible?

---

### Post by aysiu on 2005-12-17
[QUOTE=Tmyers]If I remember correctly, after you adjust partition sizes in the ubuntu installer, it then immediately proceeds to install ubuntu's core files. How can I just adjust the partition sizes and exit. Is it possible?[/QUOTE] Try using a live CD, then, and GParted.

As I mentioned before, though, the only surefire free partitioner I've seen in Mandriva's DiskDrake.

[Up-to-date/extra repositories](http://www.psychocats.net/linux/sources.php) | [Installing software in Ubuntu](http://www.psychocats.net/linux/installingsoftware.php) | [Making Root Changes](http://www.psychocats.net/linux/permissions.php) | [Mounting Windows](http://www.psychocats.net/linux/mountwindows.php)

---

### Post by Tmyers on 2005-12-18
GParted through live install  wasn't working correctly and I kept getting an error message (even after "sudo swapoff -a) , So Im following your lead and burning mandriva (disc 1) to a cd, and trying out diskdrake. Anything I should know about forcequitting the installer? Or will it give me an option to quit?

---

### Post by aysiu on 2005-12-18
[QUOTE=Tmyers]GParted through live install  wasn't working correctly and I kept getting an error message (even after "sudo swapoff -a) , So Im following your lead and burning mandriva (disc 1) to a cd, and trying out diskdrake. Anything I should know about forcequitting the installer? Or will it give me an option to quit?[/QUOTE] It may pain you to do this, but I've done this many times on my computer and once on another computer, and it's never given me problems... I go through the entire partitioning process with DiskDrake until it's done. 

Then it prompts me about detecting the first Mandriva install disk and do I want to copy the contents. 

I just hold down the shut down button on my computer until it shuts down. 

Then, I reboot, and while it's rebooting, I pop out the Mandriva CD and pop in the Ubuntu CD.

---

### Post by Tmyers on 2005-12-18
Thats what I was planning on doing, but wasnt quite sure. Ill probably have the dual boot up tommorrow as the mandriva iso is taking a bit to dl.

---

