---
title: "Hardy stops responding on Dell Latitude C400"
date: 2008-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jare on 2008-05-05
I installed final version of hardy on c400 about a week ago. Since then i have had these sudden freezes when the whole system stops responding. I can't even change between ttys.

This happens quite randomly. There might be many hours or only five minutes of use before freezing. Either syslog nor messages was much of a help, because i could not find any consistent data from there (yet).

Specs: 1.2GHz p3m, 512MB ram, 40GB harddisk, Intel 82830CGC graphics controller, Intel 82801CA audio controller, 3c905C ethernet controller, ISL3890 (prism) wlan.


Edit: Added some hardware specs.

---

### Post by Jare on 2008-05-06
And no, it's not an overheating problem. I installed i8kutils and tuned my own settings file, but those sudden freezes keep still happening.

(It also seems that first freeze happens after many hours of use and then second one right after the first when i have finished booting up. After that there might be again hours of use before freezing.) Actually there seems to be no such pattern and those freezes keep happening even more often now. I also tried to get some log data with netconsole, but it wasn't much of a help.

---

### Post by embro on 2008-05-07
I have exactly the same problem on my Dell Latitude C400 since I have installed Hardy. I haven't found a solution yet..

---

### Post by Woolsh on 2008-05-08
Same problem here, but with an intel ipw2100 wireless card. Seem to rule out wireless as the reason at a first glance.

It is hard to test as the lockups occur at inpredictable intervals - no log entries either.

I just disabled DRI to find out if that might be the rason.

---

### Post by cdmackay on 2008-05-08
same here, 100% fine on gutsy, regular hard hangs since a fresh install from scratch of hardy (not an upgrade).

I have found that downgrading to an earlier kernel (alone) seems to stop the hangs. I installed the following gutsy pkg: linux-image-2.6.22-14-386 and used grub to select that kernel.

That may introduce other issues, however, and may not be suitable for all, or as a long-term workaround.

NOTE: no wireless card

Pentium III 866/665MHz
384MB RAM

---

### Post by gypaete09 on 2008-05-08
Hardy got my Dimension E521 freeze sometimes for a few seconds since I upgraded from gutsy to hardy last week. But today I downloaded another upgrade, and after having restarted my machine some time later, the desktop died on me, means I can't start any app, not even terminal, not shutdown, nothing. crazy enough, the last app used, skype, works, video and sound and all.
Since my company invoicing runs on this machine under virtualbox, and my last backup is a week old, I am NOT fond of a reinstall of Gutsy with partition format.
for a complete backup before reinstall, if unavoidable, I need to know where virtualbox stores the VDI file for my XP client.
I have several hard disks, so I can do quick backups, but running the install CD for copying, I don't have enough file access rights to do it, of course, and to do it as root on the console I'm yet too dumb to do that.
I tried adduser to make a new user (under recovery mode from the CD and root prompt) but that new user would have the same problem.. it could start firefox once, but then "dies", next login, once the file browser can be started, then dies..
I really need help, am too new to solve this, too new on linux.

---

### Post by cdmackay on 2008-05-08
I do sympathise, and although I can't offer any immediate help, I would recommend you start a new thread for this issue, as it would seem to have nothing much to do with the one under discussion here (which relates to permanent "freezes", i.e. hard hangs, on Latitude C400)

one suggestion for your issue: try another pkg upgrade from the console:

    sudo apt-get update && sudo apt-get upgrade

best of luck.

---

### Post by Chief_Frankus on 2008-05-09
I had the same problem, as i have the same exact laptop as the first poster. I ran all the updates above in the console and haven't had a crash in hours. We'll see how does tommorow after extended use.

---

### Post by fatfranko on 2008-05-09
i had the same problem with my friend's dell d400.  i found this fix on a bug report from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256)

> 
The fix for this issue is to quirk your card to force enabling Pipe A. If you suspect you're having this bug, try setting this option in your xorg.conf: 

Section "Device"
    ...
    Option "ForceEnablePipeA" "true"
  EndSection


edit:
forgot to mention:  i think this fix is only for a problem with some intel-based graphics cards.  read the bug report link and see if it sounds like your problem.

---

### Post by cdmackay on 2008-05-09
interesting; thanks Franko.

Not sure this is my problem though: that bug seems to relate to an issue that was seen in gutsy, and mostly when closing the lid.

My issue is definitely new in hardy - never a single hang in gutsy - and occurs even when the system is sitting idle, no-one logged in, and with the lid open.

but I'll try the PipeA, if that's relevant to my i830 card, anyway, thanks.

---

### Post by crawall on 2008-05-11
[QUOTE=cdmackay;4921287]interesting; thanks Franko.

Not sure this is my problem though: that bug seems to relate to an issue that was seen in gutsy, and mostly when closing the lid.

My issue is definitely new in hardy - never a single hang in gutsy - and occurs even when the system is sitting idle, no-one logged in, and with the lid open.



I'm using a Dell latitude D505 and i have the same problems. I tried the   Option "ForceEnablePipeA" "true" solution but it didn't change anything.
Suggestions are welcome

---

### Post by cdmackay on 2008-05-11
yup, I added the PipeA option yesterday, and had another hang this morning.

So, can confirm that these are different issues, and the PipeA doesn't help with the one reported here (well, assuming that's what I'm seeing).

crawall: did you see my post about trying an older kernel? That seems to work for me.

---

### Post by Chief_Frankus on 2008-05-12
I too am still experiencing this problem. If it really is only a Hardy problem then I suppose its back to XUbuntu7.

---

### Post by embro on 2008-05-18
Hey guys, I noticed that when my USB mouse is connected, then Hardy does not freeze anymore! :) I left it to run for 2 days without any problems. 

Although as soon as I remove the USB connection, I have a hard hang in the next 10-15 min. So ok, this is not a solution as such, but at least I can work without this fear of the random hangs.

I browsed through other threads on this forum and saw that this 'fix' has been reported also on other machines that have the same hard hangs problems.

Personnally, since I'm not too keen on touching the kernel or re-installing an earlier Ubuntu version, I'll run my Hardy with the mouse connected for the moment, at least waiting (and hoping!) for an update to fix this.

---

### Post by kongster on 2008-05-19
Any updates to this "fix"?  Anyone else tried?  Success?

---

### Post by cdmackay on 2008-05-22
interesting; I have noted that if I leave my C400 on, but don't use it directly, logging in remotely via ssh instead, it never hangs. That might tie-in with a problem related to the touchpad.

---

### Post by daveb272 on 2008-05-25
i myself went back to 7.10 to enjoy ubuntu, i will wait a bit longer, it is such a pain to do a fresh install with out the media cable and cd rom.  Hey, it works, why change.

---

### Post by demiurgicdaemon on 2008-05-26
This is a huge issue right now that many users are experiencing.  Upgrading to a later kernel seems to be the only fix at the moment.  After upgrading to the kernel in hardy-proposed as mentioned in [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192") I have had no crashes on my E1705, although some have needed to upgrade to the very latest kernel (25) for a fix.  You can find references to these freezes in hardy all over the forums.

---

### Post by Tsume on 2008-06-07
Ive got a C400 and it freezes often as well.  Not only that, but Gutsy detected the BCM4306 rev02 inside it, Hardy doesn't detect it with the restricted drivers thing thus I can't figure out how (an easy way) to make wireless work.

---

### Post by kevpatts on 2008-06-17
Any update on this freezing issue? I'm thinking of buying one of these laptops (cheap).

Kevpatts

---

### Post by bduares on 2008-08-14
I upgraded to 2.6.24-19-386 and it didn't help stop my C400 from freezing up at all. 

So far the only thing I have found that keeps the laptop from locking up in 8.04 is to have a USB mouse plugged in and use that instead of the touchpad. Perhaps some sort of bug in the touchpad driver in Heron? Seems likely.

---

### Post by rpaco on 2008-08-14
> **bduares said:**
> I upgraded to 2.6.24-19-386 and it didn't help stop my C400 from freezing up at all. 

So far the only thing I have found that keeps the laptop from locking up in 8.04 is to have a USB mouse plugged in and use that instead of the touchpad. Perhaps some sort of bug in the touchpad driver in Heron? Seems likely.


I have a USB mouse plugged in all the time  on my Latitude D600 but it does not stop Hardy freezing when in Evolution mail or Firefox from suddenly closing. I went back to Firefox 2 since the version 3 in the Hardy package was virtually unsable.

It has not frozen in any office application.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.16) Gecko/20080718 Ubuntu/8.04 (hardy) Firefox/2.0.0.16

---

### Post by bduares on 2008-08-15
My pre-usb mouse freezes happened in Firefox, Package Manager, while updating, and when just sitting doing nothing.

Of course there are significant differences between a D600 and the specific C400 model we are discussing here, ie:

C400 = P3 M processor
D600 = Intel Centrino Pentium M 745

Video
C400 Intel 830M  12.1" up to 1024x768 max
D600 Ati Radeon M 9000  14.1" up to 1400x1050 max

memory
C400 PC133 SDRAM  
D600 DDR 266 PC2100

Actually almost every spec differs, and they are 2 totally different machines, so it is really like comparing apples and oranges to try to guess why Ubuntu acts differently on one from the other.

---

### Post by DenzilS on 2008-08-19
> **bduares said:**
> 
So far the only thing I have found that keeps the laptop from locking up in 8.04 is to have a USB mouse plugged in and use that instead of the touchpad. Perhaps some sort of bug in the touchpad driver in Heron? Seems likely.

For what it is worth, I can confirm that works, as I have had the same issue with my C400. Rebuilding it onto another motherboard made no difference, but using a USB mouse does seem to prevent the lockups. Not ideal for portability but at least I can use it again!

---

### Post by benji.ijneb on 2008-09-13
having the exact same problem as everyone else on my latitude c400. I've found that as well as plugging in a USB mouse, disabling compiz seems to do the trick!

Would be nice if there were to be a fix that didn't involve doing either of the above. Has anyone tried installing intrepid aplha 5 on their machines? Someone should to see if it makes any difference (i bloody well hope it does...)

---

### Post by Nick Rhodes on 2008-09-28
Hi,

Thanks for the compiz suggestion !

I have been struggling with stability for a while ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570)) and I now finally have a stable C400 - 10 hours uptime, fingers crossed it lasts !

Cheers, Nick

---

### Post by benji.ijneb on 2008-09-28
pleasure! Does this have anything to do with any of the other freezes people have been complaining about that have been linked to the kernel? Has anyone tried using a latitude c400 with intrepid to see if the freezes persist?

---

### Post by Nick Rhodes on 2008-09-29
> **benji.ijneb said:**
> pleasure! Does this have anything to do with any of the other freezes people have been complaining about that have been linked to the kernel? Has anyone tried using a latitude c400 with intrepid to see if the freezes persist?

I tried the Intrepid kernel and my C400 still froze.
Pipe-A seemed to reduce the frequency of the freezes (I suspect power saving/lid closing issue).

---

### Post by Mathes75 on 2008-09-29
I have the same freezing problem and i am running a Broadcom BCM1406 MiniPCI WAN card in my C400.
I was playing around with the BIOS settings and reduced the BootUpSpeed to compatible - result is a very slow but stable Hardy! I am working with my small DELL about 6 hours a day without a lockup and no mouse attachend. Maybe intel-Speedstep problems?
Even closing the lid (and suspending) and hybernating works!

Nevertheless would it be nice to have a full speed and stable Hardy working on the C400 ....

---

### Post by benji.ijneb on 2008-09-29
> **Mathes75 said:**
> I have the same freezing problem and i am running a Broadcom BCM1406 MiniPCI WAN card in my C400.
I was playing around with the BIOS settings and reduced the BootUpSpeed to compatible - result is a very slow but stable Hardy! I am working with my small DELL about 6 hours a day without a lockup and no mouse attachend. Maybe intel-Speedstep problems?
Even closing the lid (and suspending) and hybernating works!

Nevertheless would it be nice to have a full speed and stable Hardy working on the C400 ....

does this slow the whole system, or just the bootup?

---

### Post by Mathes75 on 2008-09-30
The setting slows down the whole system, not only while booting. Is there a possibility to view the current proc-speed?

---

### Post by Nick Rhodes on 2008-10-01
The fix for myself lid-close and power saving issues was to put the following in my xorg.conf:

 Section "Device"
      ...
      Option "ForceEnablePipeA" "true"
 EndSection

But I still need to disable compiz to fix my random freezes (I have confirmed this, as soon as I install compiz on Debian testing I get freezing).

If you get chance, please put reports/fixes on launchpad I have: [https://bugs.launchpad.net/bugs/267570](https://bugs.launchpad.net/bugs/267570)

Cheers, Nick

---

### Post by immerohnegott on 2008-10-01
I was dealing with these issues for bloody EVER on my c400. I finally got it to work by telling it to use the "i810" driver instead of the "intel" in xorg.conf, and adding an option to disable DRI (Option "DRI" "false" in the device section i think). Boots in full speed and runs fine - hell, I can even use the compositor in XFCE4 if I use indirect rendering. I've been using it like this for several hours every day for about three weeks without a hang - even susp/resume.
Hope it helps.



On a side note-
I don't know about you guys, but I had a hell of a time getting the 'intel' driver to look good on this machine - no matter what I did, all of the gradients would come out looking like 16 bit (hence the usage of the i810 driver). Any ideas on that?

---

### Post by threegremlins on 2008-10-20
I was having the same problem with Hardy freezing on my wife's Dell Dimension c521(Gutsy worked fine) and searched the forum for a fix. Didn't find anything helpful and some fixes I didn't want to even try. I googled the problem and came up with a very simple solution that worked, unfortunately you have to have a bootable windows partition. Go to Dell support and see if they have a bios update for your PC and install it from windows. I'm not sure if the problem has to do with the LCD monitor I added to it or Hardy needs a more current bios to operate a usb mouse and keyboard. If it's a bios thing this solution might work on different PC's.

---

### Post by benji.ijneb on 2008-11-01
slightly off topic, but seeing as we're all on the c400, i might as well ask.

has anyone else had problems running intrepid? both an update and a clean install produced results where I got to GDM, logged on and was left with a blank screen and nothing happening (the cursor and keyboard still worked, but cntrl+alt+backspace / F1 did nothing).
I got similar results on the livecd and with kubuntu - when i did a clean install, I had to use the alternate install cd.

---

### Post by lowflyerUK on 2008-11-01
I am not sure if this is exactly the same issue, but I have just installed openSuse 11.0 (kernel 2.6.25.18-0.2) on my Dell Latitude C400 and it hangs in the same way.  I have found that it does not hang if a usb memory stick or bluetooth adapter are plugged in. Also it has not hung so far with Option "DRI" "false" in xorg.conf and it does not seem to hang in text mode (init 3).

Hope this helps. I can provide more details if you want.

:)

---

### Post by benji.ijneb on 2008-11-03
> **lowflyerUK said:**
> I am not sure if this is exactly the same issue, but I have just installed openSuse 11.0 (kernel 2.6.25.18-0.2) on my Dell Latitude C400 and it hangs in the same way.  I have found that it does not hang if a usb memory stick or bluetooth adapter are plugged in. Also it has not hung so far with Option "DRI" "false" in xorg.conf and it does not seem to hang in text mode (init 3).

Hope this helps. I can provide more details if you want.

:)

sounds very... odd...
apparently uninstalling compiz fixes this (compiz seems to do a lot of damage!) os I'll check that out later...

---

### Post by embro on 2008-11-04
Has anyone tried the new release (8.10) on its C400? There is a possibility that the random freeze issue has been fixed.

---

### Post by falcino on 2008-11-04
> **embro said:**
> Has anyone tried the new release (8.10) on its C400? There is a possibility that the random freeze issue has been fixed.

I did! The installing process was ok. Then at the first login it got stuck, I had to ask a command line session, there I removed compiz and after that i could log in normally. In general it works very well, no problem with wireless over PCMCIA Card or anything else. The big problem that I still have is that suspend doesn't work, it just doesn't wake up. Unfortunately I'm pretty a newbie so I don't really know what to do and it is not really nice when I can't suspend my pc.
The situation is as described [here]("http://ubuntuforums.org/showthread.php?p=1756442") but as there is no more xorg.conf I don't know what to do.
Before I had windows xp on this pc, and I don't intend to go back to it.
Can someone give me advice or do someone want to know something else about ubuntu 8.10 on a latitude c400?

---

### Post by benji.ijneb on 2008-11-22
> **falcino said:**
> I did! The installing process was ok. Then at the first login it got stuck, I had to ask a command line session, there I removed compiz and after that i could log in normally. In general it works very well, no problem with wireless over PCMCIA Card or anything else. The big problem that I still have is that suspend doesn't work, it just doesn't wake up. Unfortunately I'm pretty a newbie so I don't really know what to do and it is not really nice when I can't suspend my pc.
The situation is as described [here]("http://ubuntuforums.org/showthread.php?p=1756442") but as there is no more xorg.conf I don't know what to do.
Before I had windows xp on this pc, and I don't intend to go back to it.
Can someone give me advice or do someone want to know something else about ubuntu 8.10 on a latitude c400?

same stuff here - my c400 only works with no compiz (i'm using the vastly inferior metacity compositer... grr...) and all of a sudden, suspend has decided to bugger off and stop working, leaving me with a black screen (sometimes before i suspend, sometimes after it wakes up - where i can get back to gdm via ctrl-alt-backspace and then safely shut down by pressing the power button. but only sometimes, though...)

any luck on either of these fields?

---

### Post by harleymick on 2008-12-07
Hello, just to throw in my experience with c400 and ubuntu.
As I am fairly new to this linux stuff, please have patience.
Ubuntu 8.04 also showed the same problems as indicated above. Did all these pipeforce advice etc. but it didn't really help.
As a result I gave up on installing this operating system. 
However got bored and installed 8.10 a few days ago on the machine, which in the meantime got a freshly formatted harddisk and XP installation.
I used the WUBI installer for that. I got a warning that only 254 MB ram was available and the installation might fail, but I continued.
During installation the system stalled and I repeated with USB mouse connected and the system stalled at a later stage.
I then used the the install option in safe graphics mode and it was installing without problem. Note I still had the USB mouse installed.
After installation only a small part of the display was used so I had to reinstall th egraphics driver with the automated process offered by running
sudo dpkg-reconfigure xserver-xorg
After that the display was ok.
Even got my pcmcia wireless card running with windows wlan driver.
I never had a freeze since, with USB mouse installed. Since yesterday I also removed the mouse and I am  using the touchpad only. Still running fine. Lets hope it stays like that.
Cheers.
PS, I have a c400, 256MB ram, 40 GB hard disk and running Ubuntu in a 10GB partition.
Good luck for all other C400 users

---

### Post by harleymick on 2008-12-11
Just as an add on. I also got rid of the USB mouse and I am using the touchpad. System is running without problems since even when laptop is switched on and online for more then 10 hours.

---

### Post by geneh2 on 2009-02-09
Any updates on this? I am having this very problem.:confused:

---

### Post by geneh2 on 2009-02-09
> **fatfranko said:**
> i had the same problem with my friend's dell d400.  i found this fix on a bug report from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256)



edit:
forgot to mention:  i think this fix is only for a problem with some intel-based graphics cards.  read the bug report link and see if it sounds like your problem.

I read the thread but being new to Ubuntu I am not sure how to use it.

---

