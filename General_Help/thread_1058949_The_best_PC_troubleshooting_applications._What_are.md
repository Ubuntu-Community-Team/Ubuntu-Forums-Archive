---
title: "The best PC troubleshooting applications. What are they?"
date: 2009-02-03
forum: General Help
---

### Post by Roasted on 2009-02-03
I work in IT support at a school district. I'm installing Ubuntu 8.10 onto my external USB hard drive. I decided to do this because it seems there are times I can recover data from Windows computers when Windows itself can't even explore the hard drives. As a result, I figured I may take the time to look a little deeper into Ubuntu applications that I could use to troubleshoot computers. What do you folks think?

If I could get a program that'll tell me ALL of the stats of the computer (again, I'd be working FROM a usb external hard drive, but I'd still be on that computer), and maybe a hard drive scanner to tell me whether or not the hard drive is in functional condition?

Does anything like this exist??

---

### Post by Titan8990 on 2009-02-03
Honestly, for what you are looking (windows diagnostics) I personally think that Bart's PE is the way to go: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/).

---

### Post by Roasted on 2009-02-03
I'll have to check that out. That sounds like a tool I can use on my spare time too. I worked on a computer last week that had Antivirus 2009 on it. Safe mode and any virus scanning was a no go! This may help me..

Is this linux based and open source?

---

### Post by Titan8990 on 2009-02-03
No, it is proprietary and built using a Windows installation disc. 

If viruses are the problem, there is nothing better than the usual safemode and hijackthis: [http://majorgeeks.com/download3155.html](http://majorgeeks.com/download3155.html)


HJT tutorial: [http://www.bleepingcomputer.com/tutorials/tutorial42.html](http://www.bleepingcomputer.com/tutorials/tutorial42.html)


and the place where I learned everything about malware removal and etc: [http://www.geekstogo.com/forum/Malware-Removal-Guides-Tutorials-f121.html](http://www.geekstogo.com/forum/Malware-Removal-Guides-Tutorials-f121.html)

---

### Post by mb_webguy on 2009-02-03
I use Linux to repair Windows.  However, you may want to look into [remastering your Ubuntu LiveCD]("https://help.ubuntu.com/community/LiveCDCustomization") to add a few packages that aren't normally included in Ubuntu, and remove some applications that you wouldn't need for your purposes, such as Rhythmbox.  There are a few applications that make this a bit easier, such as [UCK]("http://lichota.net/~krzysiek/projects/ubuntu-livecd-customization/").

The best program I've seen to display all information about hardware specifications is Sysinfo.  This is one of the packages that you might want to add to the LiveCD.  You can get the same information using various commands in the terminal, but Sysinfo collects it all in one nice GUI.

ClamAV is a pretty good virus scanner, and it's included in Ubuntu by default, but only the command-line version.  There are a few GUIs available in the repos for it, including clamtk.  On the other hand, you might want to use [AVG for Linux]("http://free.avg.com/download?prd=afl") instead.  I prefer it because I use AVG in Windows, and it's what I'm used to.

You'll need the ntfsprogs package for various tools for working with ntfs filesystems.  It's in the repos, but not on the LiveCD.

While you really shouldn't ever need to use it when trying to fix Windows, GParted is the defacto standard for Linux partition editors.  It's not in the default installation of Ubuntu, but it *is* on the LiveCD.

To help secure a Windows machine from outside intrusion, you probably want to add Nessus (the packages nessus and nessusd).  (Note that you'd be running Nessus from a different computer in order to scan the Windows machine, so this isn't absolutely necessary, but can be convenient.)  

Quite often, if a Windows machine won't boot, it's because of a bad MBR, and I've noticed that some Windows disks don't have the necessary tools to repair the MBR.  For this, you can use the ms-sys package.  If you use an Intrepid LiveCD, you'll have to get the package from the [Debian website]("http://packages.debian.org/etch/ms-sys").  It's included in the repositories for previous versions of Linux.  However, it's easier to just keep a Windows disk that *does* include the necessary tools or a [Super Grub Disk]("http://www.supergrubdisk.org/") handy.

---

### Post by jimv on 2009-02-03
Yeah, BartPE is the way to go for trying to salvage Windows installs.  It includes a good filesystem scanner, filesystem browser, registry editor, etc.  All you need is a Windows installation disk and the program from the aforementioned site to make the BartPE disk.

There are plugins for BartPE that will let you put AVG, Adaware, Spybot, etc on the disk as well.

---

### Post by whitegourd on 2009-02-03
I keep three disks in my messenger bag at all times ...

1) Ubuntu Live CD
2) Bart PE
3) Ultimate Boot CD

---

### Post by marcgh on 2009-02-03
Hi,
I also keep CD's with me, but only 2:

- Ubuntu live CD
- Bootitng (boot, partition and MBR repair)

and hijack this + BFU ( brute force uninstaller) + bitdefender_free on a small pendrive.

This combination never let me down on a (win) machine.

---

### Post by mb_webguy on 2009-02-03
Well, if we're talking about disks we use, I always keep the following handy: a USB pocket drive loaded with an Ubuntu installation (and all of the utilities I mentioned in my previous post), an Ubuntu LiveCD (in case the computer won't boot from USB), a Super Grub Disk, a Windows XP Business Edition installation disk (which includes all of the system recovery utilities), and an Ultimate Boot CD.

---

### Post by Roasted on 2009-02-04
Not to go kinda off topic, but I will anway, how did you get Ubuntu to install on your drive? I installed 8.10 on my external hard drive and it doesn't boot. I have no idea what I did wrong.

If I could get that working and install some type of hard drive scanner to run diagnostics and make sure the drive itself is still usable that'd be friggen great!

---

### Post by mb_webguy on 2009-02-04
I just installed it like you would to an internal hard drive.  It messed up GRUB on my computer, so I had to fix that, but otherwise was a pretty normal installation.

The drive I'm talking about, btw, is a 6GB USB hard drive, not a flash drive.  Flash drives are a bit different when it comes to installing Linux...

---

### Post by glotz on 2009-02-04
See [http://www.sysresccd.org/](http://www.sysresccd.org/) (GPL)

---

### Post by Roasted on 2009-02-04
> **mb_webguy said:**
> I just installed it like you would to an internal hard drive.  It messed up GRUB on my computer, so I had to fix that, but otherwise was a pretty normal installation.

The drive I'm talking about, btw, is a 6GB USB hard drive, not a flash drive.  Flash drives are a bit different when it comes to installing Linux...

I know. I'm using a 160gb USB external hard drive for this. I have 1gb swap 30gb root and the remainder is typical FAT32 storage.

I installed Ubuntu 8.10 on my external drive on my work laptop that I'm using now. Then every time I rebooted I get the grub menu with Ubuntu + XP available. Without the drive plugged in, I got grub error 22. I somehow fixed it without knowing what I did and now XP works, but every time I try to boot to my external drive it says "Windows did not start properly. Would you like to boot Windows normally or go to safe mode?" Weird.

As we speak I'm trying to boot to my external drive on a spare HP tower behind me and it's hanging with a flashing dot in the upper left. Ugh.

---

### Post by Roasted on 2009-02-04
All right, cancel that. I got it working. What I did was I just used a spare HP computer I had laying around and, to avoid any grub issues with the current install, I simply turned it off and unplugged the internal hard drive. Then I booted to LiveCD, installed, and then booted to the external drive on a completely different HP computer. Good deal.

Now, is there any type of software that is a must have for IT troubleshooting? I was hoping to grab some sort of software that would diagnose problematic hard drives.

---

### Post by mb_webguy on 2009-02-04
There are plenty of utilities for examining and fixing hard drives.  fsck is the Linux equivalent of the Windows CHKDSK, and checks for filesystem consistency.  You should really only use it on native Linux filesystems, though.  For working with ntfs, you should check out the utilities included in the ntfsprogs packge.  For data recovery, take a look at TestDisk.

---

