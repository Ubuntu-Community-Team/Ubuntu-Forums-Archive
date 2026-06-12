---
title: "Dell 1420N"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by PenguinLover4Life on 2007-07-30
Hey guys. I ordered a Dell 1420 today. I've been reading around on the forums and I'm beginning to think it was such a great idea... I have a few questions:

-I read that some people are having problems re-installing Ubuntu on the system is there a fix for this?

-I read the X3100 doesn't work well in Ubuntu. Any fixes for this?

-I read where people with similar dell's are having issues mounting live cd's of other distros, any fix for this?

-This is going to be a dumb question. I want to install XP on a different partition for gaming. I can do this with the 1420 right?

Thanks,
-Taylor

---

### Post by notwen on 2007-07-31
> **PenguinLover4Life said:**
> Hey guys. I ordered a Dell 1420 today. I've been reading around on the forums and I'm beginning to think it was such a great idea... I have a few questions:

-I read that some people are having problems re-installing Ubuntu on the system is there a fix for this?

-I read the X3100 doesn't work well in Ubuntu. Any fixes for this?

-I read where people with similar dell's are having issues mounting live cd's of other distros, any fix for this?

-This is going to be a dumb question. I want to install XP on a different partition for gaming. I can do this with the 1420 right?

Thanks,
-Taylor
1. Dell has a recovery partition that can do this for you available from GRUB.
2.  Works fine out of the box, you may/may not need to re-configure xorg.conf for a better resolution.  By default it is unable to run the "Desktop Effect" (ie. Compiz-Fusion / Beryl).  Reports on this [thread]("http://ubuntuforums.org/showthread.php?t=506744") say it's possible after installing a couple of new packages for the Intel X3100 chipset,
3. 
4. Yes, just find a dual-boot howto that suits your needs(UBuntu installed first, wanting to install WinXP).  I'll see if I can find a l

---

### Post by smithno on 2007-07-31
I don't understand why folks feel the necessity to re-instull Ubuntu on one of the Dell N machines as soon as they get it. Everything worked on my 1420N out of the box. The screen resolution was even right and the wireless connected as soon as I remembered that I had to add the NIC address to the allowed list of machines in my wireless router. I even installed KDE without issues! There is no need to blow away Ubuntu and install Kubuntu to get KDE! Having both on my machine and having the choice to boot into either Gnome or KDE is nice. There is a old saying, "If it ain't broke, don't fix it!"

---

### Post by PenguinLover4Life on 2007-07-31
I wasn't planning on reinstalling the OS as soon as I got it. The only reason I asked for was later own down the road. Incase something happens and I have to. 

Thanks for your replies they have definitly put my wories to a rest,
-Taylor

---

### Post by timseal on 2007-07-31
just watch out for the GL screensavers, my 1420N crashed hard just doing a preview.

---

### Post by apswartz on 2007-07-31
Some of us are having trouble getting our trackpads working. They are recognized as mice, but not as trackpads. That means we cannot scroll.

See this thread...
[http://ubuntuforums.org/showthread.php?t=510516](http://ubuntuforums.org/showthread.php?t=510516)

---

### Post by sciurus on 2007-08-01
Here are the two main issues I know of

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119255)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673)

The video thing is not a difficult fix. Intel graphics are definitely the best choice for Linux.

---

### Post by ticklecricket on 2007-08-07
You can't install feisty from a live cd, but that's a problem with the santa rosa intel chips, not specifically with the dell. There are hacks, but they're not so elegant.

There's a fix for the trackpad issue.

My biggest issue is that it ships with a 32 bit os. I've been using a 64 bit OS for two years, so why do they need to ship the 32 bit version?

---

### Post by mjbommar on 2007-08-07
When I got home yesterday, a Dell Rep had left me a message indicating that my shipment date, which should have been yesterday, has been delayed by a week to next Monday.

Anyone else experience likewise?

---

### Post by Malice007 on 2007-08-07
When I ordered mine the ship date got bumped back also. When I called I was told  it was because of the color I picked and the Lid was on backorder. 
F.Y.I. if you take the live cd out and re install Ubuntu I was told by Dell that you wipe out there restore feature (hitting the esc button when booting up) I used this several times when messing around with settings. Just hit the esc button you will see the option restore to factory defaults and once its completed it just like you got  it right out of the box.

Problems I ran into so far with my 1420N

When going to the screen savers it crashes my computer.
Compiz is very buggy but I believe I read that there is a fix for this. 


I called tech support a few times for minor problems that I caused. And the tech support is GREAT! When you call for tech support you will get the windows guys. Just give them all of your info and tell them you want the LINUX tech support.


Im still trying to work on the bluetooth I had recieve working but some how I managed to make that stop working also.. :)

---

### Post by chronniff on 2008-03-07
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)


This has most of the fixes, I got the 1420n and had to use the wifi fix and used the compiz fix....compiz works mosty fine...wifi works fine ( although signal reception is what it was )
and the reinstall dvd's are here too..........otherwise I have been quite pleased with the laptopp....despite the fact that dell really pooped the bed by limiting its first ubuntu installs on hardware that isn't yet properly supported in linux

---

### Post by natehall on 2008-03-08
I was annoyed I had to fix a few things right out of the box but overall I'm glad I'm finally free of Microsoft's control. I had tried and failed to get Linux  ( and tried OS/2 warp before that !) Now I'm convinced the future of computing is with Linux.

---

### Post by jeffreyldavidson on 2008-03-08
I purchased my 1420N in February 08 and have been very happy with no problems. Compiz and Avant worked perfectly. My wireless also worked perfectly without any need to configure. I upgraded my video card to the Nvidia high resolution screen and am glad I did. I have no complaints...everything has worked.

---

