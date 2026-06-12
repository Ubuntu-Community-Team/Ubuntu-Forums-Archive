---
title: "After installation: Ubuntu maintenance?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by seatea on 2005-10-25
I have been running Mac Os 9.2.2 on  a PM G4 400 desktop and was relatively happy with my setup. I had looked at upgrading to Mac Os X, but after looking around at other users' experiences, I was concerned that I would end up with  a large, relatively  slow operating  system. Also, I was comfortable with troubleshooting and maintaining my current system and have not been  in the mood to do an upgrade which would involve learning  a new operating system. As time has gone by, I have been experiencing more problems  accessing  necessary websites which require upgraded software not available for OS 9.2.2. After looking around, I decided to try Ubuntu. I reasoned that with the switch to Apple's OS X requiring  learning to use a Unix based system, I might as well learn about Linux. I have been pleased with the speed of using applications in Ubuntu and the appearance of the desktop GUI, although I have been troubled by the nuances of getting my computer organized and running the  necessary applications. These forums have  been of vital assistance. My questions are, apologies for my lack of knowledge on Linux,:

1. What  does the  expression "break" your system mean? Does this refer to crashing the system or is it the rendering  of an unusable system requiring a fresh re-installation?

2. Are there routine  maintenance tasks that  need to be  run? For instance, in Mac OS 9, I periodically rebuilt the desktop, ran Disk First Aid, and, occasionally, DiskWarrior to maintain my system. Also. I would at infrequent times remove preferences in programs that were acting up. Are there preference files  that  become corrupted in Ubuntu and require manual removal?

3.Should I need or make a bootable CD to use  for disk repair or troubleshooting? Does the installation CD have repair utilities and how do you access them? I was wondering how to use fsck, if ever, on my system. Can it be run  from the  install CD after booting up on it? I  haven't figured out how to do that.

Once Again, I appreciate the help I have been getting from these forums.

---

### Post by SilentCacophony on 2005-10-25
Hi.

> 1. What does the expression "break" your system mean? Does this refer to crashing the system or is it the rendering of an unusable system requiring a fresh re-installation?

There are many ways that one can 'break' thier 'system', usually by mucking around with something that one is unfamiliar with in the OS, and causing some component of the OS to fail. Quite often, people have trouble with packages 'breaking', if they are running the unstable release of ubuntu, or trying to install packages which aren't in the official repositories.

In most cases, a fresh install would not be needed. The tricky part is finding out what steps need to be taken to remedy the problem. There are commands that will reconfigure packages, or editing of a certain file may be needed, etc... Depends upon the specific problem. If you're not too adventurous in your use of Ubuntu, it shouldn't be a problem.

> 2. Are there routine maintenance tasks that need to be run? For instance, in Mac OS 9, I periodically rebuilt the desktop, ran Disk First Aid, and, occasionally, DiskWarrior to maintain my system. Also. I would at infrequent times remove preferences in programs that were acting up. Are there preference files that become corrupted in Ubuntu and require manual removal?

I have no idea what the apps you mentioned do, but I have seen no need for any routine maintenance tasks. AFAIK, disks are checked during bootup, and I personally never had any corrupted files (using ext3 filesystem,) or problematic preferences, except on two occasions I've had a screen resolution problem upon booting, where a restart of the computer cleared it up.

> 3.Should I need or make a bootable CD to use for disk repair or troubleshooting? Does the installation CD have repair utilities and how do you access them? I was wondering how to use fsck, if ever, on my system. Can it be run from the install CD after booting up on it? I haven't figured out how to do that.

The install cd serves that purpose. When you boot with it, enter 'rescue', and it'll guide you to where you can mount the root filesystem, and will drop you into busybox, a limited shell. I believe most basic tasks like fsck can be done there.

Some people prefer to have knoppix on hand for that, while some like [sysresccd]("http://www.sysresccd.org/download.en.php").

---

### Post by swerner on 2005-10-25
Welcome to the big wide world of [Tux]("http://www.isc.tamu.edu/~lewing/linux/").

[QUOTE=seatea]
1. What  does the  expression "break" your system mean? Does this refer to crashing the system or is it the rendering  of an unusable system requiring a fresh re-installation?
[/QUOTE]

Breaking your system may crash it and rendered it unusable! "Break" is just a geeks way of saying that things won't work like they should.  When your system is broken: at best you won't notice a thing, at worst you will loose all your data and you will have to re-install.  If you do get a warning message saying "Continuing may break your system. Do you want to continue? [Y/N]", I suggest the "N" option, unless you are *really* sure you know what it is doing.

[QUOTE=seatea]
2. Are there routine  maintenance tasks that  need to be  run? For instance, in Mac OS 9, I periodically rebuilt the desktop, ran Disk First Aid, and, occasionally, DiskWarrior to maintain my system. Also. I would at infrequent times remove preferences in programs that were acting up. Are there preference files  that  become corrupted in Ubuntu and require manual removal?
[/QUOTE]
Appart from backing up my hard disk and downloading updates (which is almost automatic with Breezy), there is nothing you really need to do on a regular basis.  Defraging programs exists, but I don't know of anyone who uses it, I have heard (I could be wrong here) that the file systems used don't need defraging.  
I have had problems with Gnome preference files becoming corrupted, but that was mainly on Fedora, I have not had that happen with Ubuntu. 

[QUOTE=seatea]
3.Should I need or make a bootable CD to use for disk repair or troubleshooting? 
[/QUOTE]
It would be wise to have a repair disk on hand, just like it would be for any other operating system.  The only reason I have needed a recovery disk is because of my own stupidity, and running "unstable" systems.  I recomend the Ubuntu Live CD or Knoppix Live CD, although Knoppix will have more of the tools to fix the system.  If you don't "play" with your system, you should never need a repair disk.

[QUOTE=seatea]
Does the installation CD have repair utilities and how do you access them? I was wondering how to use fsck, if ever, on my system. 
[/QUOTE]
Yes the install CD does come with some repair utils, these are all console based however.  With this console you will be able to fix most things that occur, but if you are not used to the console it can be a huge learning curve.  fsck is run about every 30 boots, or every 180 days (I think), which ever comes first.  I never had any filesystem problems that are due to random corruption (just my own stupidity again).

[QUOTE=seatea]
Can it be run  from the  install CD after booting up on it? I  haven't figured out how to do that.
[/QUOTE]
yes, fsck can be run from the install CD, just start the normal install until it asks for the langauge.  Then hit CTRL-ALT-F2 (or the Mac equivilent) to bring you to the console, it will ask you to "Hit Return" to activate the console.  You should be able to run fsck from here.

[QUOTE=seatea]
Once Again, I appreciate the help I have been getting from these forums.
[/QUOTE]
:)

---

### Post by seatea on 2005-10-25
Thanks again.

I don't leave my computer running all the time. In Mac Os X there are certain routines run that would be aborted if your  machine does not run 24 hours and they must be periodically forced to run. Will shutting down my computer nightly  pose a similar problem in Ubuntu? Also in Mac OS X, I have read a frequent recommendation that permissions be  repaired routinely after installing new updates or programs. (This I understand is something like Disk First Aid. "no idea what the apps you mentioned do" In Windows 98, there  is a similar program called ScanDisk. Disk First Aid repairs the file system tree and other parts of the disk system, that I can't explain. Disk Warrior is a directory repair program.) Is there a similar problem with Ubuntu permissions that occurs requiring a utility?

---

### Post by SilentCacophony on 2005-10-25
> I don't leave my computer running all the time. In Mac Os X there are certain routines run that would be aborted if your machine does not run 24 hours and they must be periodically forced to run. Will shutting down my computer nightly pose a similar problem in Ubuntu?

I shut mine down every time I'm away from it. AFAIK, there are no programs or tasks in a new installation that would be interfered with by shutting down ubuntu. I suppose that there may be something that you might install yourself that could be a problem, but I expect that the docs would warn so.

Even if you never shut down, it should run just fine.

I'd recommend using the ext3 filesystem rather than ext2, though. I've had data loss on ext2, but not on ext3.

> Also in Mac OS X, I have read a frequent recommendation that permissions be repaired routinely after installing new updates or programs. (This I understand is something like Disk First Aid. "no idea what the apps you mentioned do" In Windows 98, there is a similar program called ScanDisk. Disk First Aid repairs the file system tree and other parts of the disk system, that I can't explain. Disk Warrior is a directory repair program.) Is there a similar problem with Ubuntu permissions that occurs requiring a utility?


If you use any of the dpkg front-ends installed by default (synaptic, aptitude, apt-get, 'Add Applications' in gnome) to install new packages onto your system or update existing packages, generally you should have no problems as long as you are using Breezy or earlier. If you use the 'Dapper' (unstable) repositories, then you may experience various problems... but you have to explicitly set that up to move to unstable ubuntu.

I've never had any problem with permissions having gone awry, and I've been using ubuntu since July, starting with the 'Hoary' release.

---

### Post by seatea on 2005-10-25
It seems to me almost astonishing that there are not any maintenance issues or routines. Maintenance utilities are sort of a cottage business with  Macs. I would not describe my Mac OS 9.2.2 as unstable and I have never had any problems with viruses or spyware, but I consider a restart and the occasional appearance of a directory error a normal event. Even with Mac OS X there are utilities by companies like Alsoft and Micromat to keep the system running smoothly outside of the  built in Mac OS utilities. The recommendations I have received on maintenance issues here clears up the lack of search  results when I was looking into this concern on  Google.

I thought there was a program called cron that did maintenance tasks, but maybe that is an individual's choice on whether or not to use that application on their computer.

---

### Post by endersshadow on 2005-10-25
[QUOTE=seatea]It seems to me almost astonishing that there are not any maintenance issues or routines. Maintenance utilities are sort of a cottage business with  Macs. I would not describe my Mac OS 9.2.2 as unstable and I have never had any problems with viruses or spyware, but I consider a restart and the occasional appearance of a directory error a normal event. Even with Mac OS X there are utilities by companies like Alsoft and Micromat to keep the system running smoothly outside of the  built in Mac OS utilities. The recommendations I have received on maintenance issues here clears up the lack of search  results when I was looking into this concern on  Google.[/QUOTE]

It really is quite amazing, isn't it?  Probably one of the best features of Linux, that's for sure. :-D

[QUOTE=seatea]I thought there was a program called cron that did maintenance tasks, but maybe that is an individual's choice on whether or not to use that application on their computer.[/QUOTE]

cron performs scheduled tasks, such as log rotation or update checking.  You can set cron up to do "maintenance tasks," as I think a few do exist for Linux, but I can't think of any one that has a huge following, for good reason.  But, in the end, cron is just there to run a script at a certain time or a certain interval.  If you'd like to explore cron, by the way, you can find it in /etc :-D

---

### Post by Dr. Nick on 2005-10-25
Check this thread concerning disk cleaning
[http://ubuntuforums.org/showthread.php?t=80474](http://ubuntuforums.org/showthread.php?t=80474)

What was eventually determined is that linux can be cleaned up some after time, but not doing so really isn't a problem.

That post was sorta comparing to windows but the same conclusions can be drawn.

Just my personal expierence
1. No data corruption and I am using XFS file system
2. Some permission problems, caused by me and fixable without any 3rd party application

I dont believe cron has any jobs set by default that would need the comp to be left on 24/7 Mine goes off every night and is running smoothly

---

