---
title: "Machine freezes when trying to edit /etc/apt/sources.list"
date: 2005-10-14
forum: Desktop Environments
---

### Post by WeeR on 2005-10-14
Hello.
Just installed ubuntu, and it looks great :)
I have just one problem, when I try to edit the /etc/apt/sources.list
in Gnome, the machine just freezes. I run my computer with 2 hdd's, on with XP and the other one with ubuntu. Win XP does not freeze, so I don't think its hardware. I run a Nforce2 chipsett, and I know from past experience that this is not so good in linux, especially with SATA drives. However, I run ATA drives and no SATA.
What could I do to fix this? Don't wont to uninstall it either :)


EDIT: Changed Topic

---

### Post by RAOF on 2005-10-14
That's really, tremendously, odd.  I can't think of any reason why that would happen :confused: 

Anyway, how are you trying to edit it?  Have you tried opening up a terminal, and running
```
sudo gedit /etc/apt/sources.list
```

I've actually had pretty good luck with nforce 2 chipsets :)

---

### Post by WeeR on 2005-10-14
I have now used the system a bit more, and I have found out that it freezes other places to.. The system is just not responding, And I also found out that the installation of ubuntu messed up my XP installation too..
I just get "Filesystem type unknown, partition type 0x7
saveddefault 
makeactive
chainloader +1"

Anyone help me please? :)

---

### Post by WeeR on 2005-10-19
Thanks for the reply RAOF.
I found out that I was running Ubuntu 5.04, and i though that upgrading to 5.10 would get rid of the problem but no..
I just formatted the machine and installed 5.10, the first thing that appears on the screen after signing in is that its available updates for download.
I click on this icon and the second i press download the machine freezes just like with the 5.04 version.. Again, XP is installed on the same hdd on different partition, and is working great.. What could do this?

---

### Post by zenodaddy on 2005-10-19
I would first run sudo apt-get update , once this completes then run sudo-apt-get upgrade.

After performing the upgrades, run sudo apt-get -f install.. or is it -r install.. anyway, this will look for any broken packages that were not installed originally.. once you do this I would then download and install the latest linux graphic's driver for your video card.

If all of this fails then you may need to just go ahead and wipe the system clean including windows xp. Windows does not like to be installed 2nd.

Using the Windows XP Installation CD create 2 partitions, install Windows on the first, once complete reboot into Ubuntu's install CD and remove the self-created partitions in the partition table, then let ubuntu choose the free space and install.. this should clear up the problem.

I have had the same issue with 5.04 and it was just a bad partition setup.

---

### Post by barakab on 2005-10-19
check this
[http://ubuntuforums.org/showthread.php?t=76288](http://ubuntuforums.org/showthread.php?t=76288)
[http://ubuntuforums.org/showthread.php?t=76288]("http://ubuntuforums.org/showthread.php?t=76288")

---

### Post by WeeR on 2005-10-26
Thanks for the reply guys, I'm really hoping to get this system online.. :)

zenodaddy:
I have now tried all the apt-get commands, and the built in update thing in ubuntu.
I have also tried formatting the disk, installed XP first (every time), and then ubuntu. Tried both 5.04 and 5.10 twice with no luck..
I have also tried installing 5.04 and 5.10 on a new hdd, with no XP at all..
Both versions locks up the same way...

barakab:
Thanks for the link, lots of things to try there :)
I have now tried everything and the machine still freezes..
Since XP works 100%, I think it have something to do with my hardware, maybe anyone can confirm this?
Machine:
MB : A7N8X E-Deluxe
Graphic : ATI 7000

Thats all.. Thanks very much for the help so far :)

---

### Post by vruum on 2005-10-26
I might be totally wrong, but this looks more like a sudo/gksudo problem than an apt one, to me. Are you able to sudo anything? for example, are you able to run any of the administration tools that require sudo access (asks for password)? if anything sudo freezes up your machine, try rebooting in safe mode or switch to a terminal (alt+control+F1) log in and run "sudo apt-get update" (the "sudo" is not needed in safe mode)

---

### Post by WeeR on 2005-10-26
vruum:
Thanks for the reply, however, the machine freezes at all times and not only with tasks that need sudo access.
(Like surfing the net with firefox, trying to edit sources.list and so on)
Do you need sudo access to edit sources?? (If I do, maybe sudo have something to do with it after all).
I would still bet my money on some sort of hardware thats not compatible.
I have not updated my ATI drivers, because on ATI.com I just found drivers for 8500 and up, not the 7000.

If it helps I only found the system stable when the login screen for ubuntu shows after a restart, after login the system freezes after 30sec to 10 minutes.. Again, I could try to leave the computer just logged in, and check if it locks up then..
Thanks very much for the help guys, just keep on posting :)

---

### Post by timbl on 2005-10-26
You may have already done this, but make sure that there are no bad blocks on the hard drive. This will cause the behaviour that you seeing, especially if the sources.list file is on a bad block.

Run: "sudo dmesg" and look for hard drive errors.

---

### Post by WeeR on 2005-10-26
I have not checked the disk, but I can do that tomorrow, because the computer is a work.. however, I don't think this is the problem since I have tried to install it on two different hdds and the Win XP installation is working like a charm..

---

### Post by WeeR on 2005-10-26
I'm running a Sempron CPU, can this be the problem?

---

### Post by Boelcke on 2005-12-09
WeeR, have you had any luck solving your lockups?  I, too, have had similar lockups.  Repeatedly, my screen just freezes, no response at all.  Mouse pointer frozen still.

I checked the video driver, and my installation defaulted to the "nv" driver, not the "nvidia", so that's OK.

There was no "RenderAccel" in my /etc/X11/xorg.conf file, so that didn't need turning off.

I removed powernowd, but it still locks occasionally,

Each time it locks, I'm not necessarily doing anything exotic.  Browsing with Firefox, locked while using the GIMP once.

I wondered if it was something in GNOME, so I installed KDE.  After an hour or two in KDE, it locked, so that wasn't it.

I'm starting to think it is a hardware problem, and that I'll have to isolate everything one by one.  Memtest86 works fine on my second-hand 512mb PC2700 memory, but I could try a 128 I have laying around (128 just isn't enough, but I'd hate to buy new memory for the system if that isn't the problem!).

I've heard some folks suggest it could be the integrated network card on my motherboard.  I do have an extra PCI network card -- I wonder if ubuntu will auto-detect that sucker.

My video card is old (it's actually a PCI card!).  Don't have an extra of those, though I suppose I *could* trade out one with my primary machine.

Any other suggestions are welcome!

---

### Post by Boelcke on 2006-02-26
I've struggled with a lockup problem that might be similar, and I believe I've just solved it.  I've tried many suggestions found in many places, including:

Making sure I'm using the "nv" open source nVidia driver
Removing powernowd
Tried other GUIs (locks up in Gnome, KDE, and XFCE)
Didn't find RenderAccel in my xorg.conf, so couldn't turn it off ;)
Checked for HD errors
Replaced old memory, which might have been suspect

I'm using an old nVidia card with a Riva TNT chip, and decided that this was the problem.  Like WeeR describes, I was able to lockup the system while running any number of applications.  The screen just freezes, no mouse movement, no nothing.  I did notice, after a time, that it often would hang while scrolling in Firefox on a page with many pictures, or a large picture.  Why didn't I think this was a graphics thing earlier?!?

I installed the proprietary legacy nVidia drivers, and it seems like that has solved the problem.  Instructions follow:

From [http://wiki.linuxquestions.org/wiki/OpenGL](http://wiki.linuxquestions.org/wiki/OpenGL), I tried this at the command line:
glxinfo |grep rendering
and saw:
direct rendering: No
It should have been Yes.  With a No, that means the CPU is doing all the OpenGL rendering my graphics card should be doing!  (And I had assumed my graphics performance was bad because the video card was old.  Apparently, it shouldn't be that bad!)

From [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
I followed the instructions to install the legacy drivers.

My graphics performance has gotten much better (as you'd expect from putting the workload on the video card, rather than the CPU), and I haven't locked up yet.  I'll post here if I start locking up again...

---

