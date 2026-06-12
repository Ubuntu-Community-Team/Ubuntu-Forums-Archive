---
title: "InstallingNewbie ?: Ubuntu and Win ME and two separate drives"
date: 2006-03-09
forum: Desktop Environments
---

### Post by boonesyndicate on 2006-03-09
I am ready to dive into the world of Linux for real, after playing around with the idea for a few years.  I already have ME installed on one hard drive and would like to install Ubuntu on a new hard drive.  I also have another HD which stores extra & important files just in case Windows has a fatal crash.

With that in mind, I have a few questions:

1. How should I set up these hard drives as far as connections go?  I believe its obvious that ME has to go first as the master, but do I put the Linux drive as its slave or my extra space drive. Or should I first install Linux with only the two drives, and add the third one after the install is over?


2.  How do I go about installing Linux on the second drive?  Will the boot disk recognize the second drive?


3. When I start up the computer after installing Linux on the second drive, does the system automatically go into a dual boot asking which system do I want to run, or will it go straight into ME since it will be on the master disk.  If it isn't an automatic dual boot, how do I get it to do so?

I've done some searching on these forums already, but couldn't quite get a nearly exact answer for what I wanted to know.

Sorry if this msg. is a repeat of many other posts.


d. boone

---

### Post by evilgold on 2006-03-09
Just install ubuntu to your second drive, it will automatically install grub, and automatically give you the option to dual boot. With the 3rd drive, if you make sure its formated as fat32, you can set it up as a shared drive between the two systems.

I'm wondering: why are you using windows ME?

---

### Post by bobpur on 2006-03-09
[QUOTE=boonesyndicate]I am ready to dive into the world of Linux for real, after playing around with the idea for a few years.  I already have ME installed on one hard drive and would like to install Ubuntu on a new hard drive.  I also have another HD which stores extra & important files just in case Windows has a fatal crash.

With that in mind, I have a few questions:

1. How should I set up these hard drives as far as connections go?  I believe its obvious that ME has to go first as the master, but do I put the Linux drive as its slave or my extra space drive. Or should I first install Linux with only the two drives, and add the third one after the install is over?


2.  How do I go about installing Linux on the second drive?  Will the boot disk recognize the second drive?


3. When I start up the computer after installing Linux on the second drive, does the system automatically go into a dual boot asking which system do I want to run, or will it go straight into ME since it will be on the master disk.  If it isn't an automatic dual boot, how do I get it to do so?

I've done some searching on these forums already, but couldn't quite get a nearly exact answer for what I wanted to know.

Sorry if this msg. is a repeat of many other posts.


d. boone[/QUOTE]
Hello,
  I am running a setup just like you mentioned on a 5 yr old Compaq Presario. It came with a 20 Gb HD and after awhile was jacked up to a 60 Gb master with a 40 Gb slave. 
  When I installed Ubuntu v5.10 during setup (After the language setup screens) it'll display setup options. One of which was to erase the slave and install Ubuntu there. I just pushed the appropriate buttons and that's the way it installed.
  Windows ME on the master (As slave used to be additional storage) and now Ubuntu v5.10 on the Slave. 
  You are given a choice on Bootup which OS to boot into. FYI, Under "My Computer" the HD with the other OS is not detected any more. Not a problem just something I'd noticed after the Install.
  Smooth Install in a five yr old computer and it works fine. 
  I am also a Ubuntu newbie, but; if you have any more questions I'll try and help.

---

### Post by JimS on 2006-03-09
...

I also had a smooth install on a Dell 4100 (5yr old)
with 2 HDs.  WinME on master and Ubuntu on slave.
I think I could see my Window HD from Ubuntu, but
I have forgotten how.  Also I could see my Ubuntu
HD from Windows Device Mgr.

In Ubuntu - if you want to access WinME files, you need
to mount the WinME drive's partition(s).
see
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
and/or
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

JimS[COLOR="Blue"]
Prostate Cancer Aware[/COLOR]

,,,

---

### Post by boonesyndicate on 2006-03-09
[QUOTE=evilgold]I'm wondering: why are you using windows ME?[/QUOTE]


Well, when I first got into setting up computers on my own, I bought ME, which was new at the time.  I'm a musician, so I felt that the latest at the time would do me right.  However, I was running both music programs and "regular" programs on ME.  So I built another computer for just music using XP, but didn't want to spend more money on XP for a computer that I was just going to run productivity programs on and some basic games (none of which were the latest that were out), so I just kept ME.

Now I'm at the point where I don't want MS to have a "hold" on me.  So while I'll most likely keep my music computer running on XP (I'm not sure when the next MS OS comes out if I'll upgrade), I'm looking to migrate to Linux as it is continually updated and has programs similar to and as functional as ME,XP, etc.  Right now I feel I need to keep ME as I have some programs that I am not sure will work on Linux (I have a PockePC which I'm not sure will sync through WINE variation thereof).  But as Linux continues to grow, I'm sure I will be able to ween myself off of ME, at least for the basic productivity features.  The music side, for the moment, is  a different story.


Hope my explanation wasn't too long...:KS 


d. boone

---

### Post by boonesyndicate on 2006-03-09
Thanks for the help.  I will be trying this out within the next week or so.

If anyone else has any suggestions, please continue to reply to this post.

Thanks,


d. boone

---

### Post by boonesyndicate on 2006-03-10
One last question.  

This will be the first time that I have actually had 3 HDs on a machine.  I know that I will have ME as the master, and the Linux HD as a slave to that.

So for the 3rd drive, am I supposed to run it as a slave to the CD-R, or as the master?  Or is there some other way to work it?

BTW, I will be setting this up on an ABIT KV7 MB, for those either familiar with the board or ABIT products, and I believe there are only 2 IDE slots on the board.


Thanks in advance for any help.


d. boone

---

