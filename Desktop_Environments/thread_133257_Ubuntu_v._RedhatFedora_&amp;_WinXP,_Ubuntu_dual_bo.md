---
title: "Ubuntu v. Redhat/Fedora &amp; WinXP, Ubuntu dual boot"
date: 2006-02-19
forum: Desktop Environments
---

### Post by xyz1.key on 2006-02-19
Greetings all!

I am new to the Ubuntu forums after running only Red Hat linux (no windows)  for a number of years.  Now, I am preparing to install Ubuntu 5.1 on an HP Pavilion a1110n system that came with WindowsXP home, SP2? installed.  

I have plenty of hard disk space available to set up partitions for linux as well as ample ram.  The system also contains five (5) different removable media drives not including a USB 2.0 port that can also be used for removable media.  System bios only supports booting from hard drive and CD drive.

Dual Boot, Master Boot Records, and Partition Schemes

A Partition Magic license has been purchased, but not installed yet as it is quite insistent on replacing the Windows boot record with Partition Magic's own version.  Google searches have returned material suggesting that replacing the MicroSoft boot record entails risks for leaving one with a non-functioning system.  Anyone care to share their own experiences in setting up dual boot systems with Ubuntu?

In repartitioning the hard drive for Ubuntu installation, how many new partitions, their sizes, and file types do forum users recommend?

Installation of new Red Hat/Fedora linux versions on my older machines would commonly require bypassing use of the Xwindow system and working from the command line to back out the most recent Xwindow version and replace it with an earlier version until driver issues were overcome.  I know the commands needed to do that in Red Hat/Fedora.  Are they different in Ubuntu (Debian)?  Would anyone care to recommend some good reference sources on Debian/Ubuntu file structures and commands?

---

### Post by RAOF on 2006-02-19
You should be able to use Ubuntu's own partitioner during the install.  That's always worked for me.

As for paritions, I'd recommend at least 3: / (5 - 10 Gb), /home (as big as it can be), swap (~500MB - 1GB).  If you want to use something other than ext3 for your root drive (reiserfs is the other main option), you'll also need to add a /boot partition.  That can be ~50MB.

If you're a bit comfortable, I'd suggest setting up LVM during the install - then you can later easily resize (even across new harddrives) your partitions.  Perhaps less important in a laptop - I suppose you're unlikely to be adding harddrives :)

The "installing software in Ubuntu" link in my sig has a good run-down of the ways of installing stuff.  But you shouldn't need to update your X - it's already pretty much the latest version on the disc.

---

### Post by ahlich on 2006-02-19
Greetings. 

Agreed w everything RAOF said.
One note: Everytime i installed dual boot on a machine i never had any problem with the automatic detection of the MBR information and accomodation of another OS on top of the currently installed one, but ONLY when i was loading Linux distros on top of Windows... 
If absolutely must/want to use the XPsp2 you might consider convert form NTFS to FAT32 on that windows partition so you can write to your windows folders.

---

### Post by az on 2006-02-19
[QUOTE=xyz1.key]
In repartitioning the hard drive for Ubuntu installation, how many new partitions, their sizes, and file types do forum users recommend?

Installation of new Red Hat/Fedora linux versions on my older machines would commonly require bypassing use of the Xwindow system and working from the command line to back out the most recent Xwindow version and replace it with an earlier version until driver issues were overcome.  I know the commands needed to do that in Red Hat/Fedora.  Are they different in Ubuntu (Debian)?  Would anyone care to recommend some good reference sources on Debian/Ubuntu file structures and commands?[/QUOTE]

I would just free up some disk space and run the installer.  Let it create the partitions for you.  By default, you get everything on one partition plus a swap.  You are free to create other partitoins by hand, if you wish/need to.  The installer's partitioner seems to be more relable than Partition Magic.

As for your older hardware, what kind of card requires an older version of xorg or xfree86?  I'll bet they work fine out of the box for you.  I have tried Ubuntu on a large variety of legacy hardware without many issues.

---

### Post by xyz1.key on 2006-02-20
RAOF, thanks.  The partition suggestions and sig links were quite helpful.

---

### Post by xyz1.key on 2006-02-20
ahlich, azz: Thanks for the input.  I will definitely setup a FAT32 partition and will try using the installer to set up those new partitions.

azz: The older hardware that tended to provoke problems on update/upgrade of Red Hat/Fedora linux was an early ATI Radeon with limited onboard memory.  Your question prompts me to realize that I probably misspoke in attributing the difficulties entirely to driver issues.  On one occasion I did need to back up to an earlier version of the Xwindow system for a while until a new driver was developed.  On other occasions the Red Hat installer applied a video resolution that was too high for the card and the issue was resolved simply by lowering that resolution.

---

### Post by az on 2006-02-21
[QUOTE=xyz1.key]On other occasions the Red Hat installer applied a video resolution that was too high for the card and the issue was resolved simply by lowering that resolution.[/QUOTE]

By default, xorg will use the highest color depth.  You can use 16-bit color instead of 24-bit color on a card with 2 megs of memory so that you can get 1024x768.

You will need to run

sudo dpkg-reconfigure xserver-xorg

to do that.

---

