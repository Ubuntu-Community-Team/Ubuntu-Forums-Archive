---
title: "Touchpad cursor jumps around"
date: 2008-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by colinnwn on 2008-08-23
Hi,

When using the touchpad on my Vostro 1500 with Hardy, my cursor will regularly jump around the screen.  Frequently if I continue moving my finger, the cursor will jump right back to where it should be, sometimes it will continue along in its new random location.  I feel like this has gotten worse in the last week.

I have tried disabling the horizontal and vertical scrolling.  I have played with the sensitivity and acceleration to no effect.  And I have been very careful where the rest of my hands are as I use the touchpad.  Even with no other part of my hand near the touchpad aside from my finger, this will still happen.

Does anyone else have this problem?  Is it a problem with the Linux driver?  Or could it be a hardware malfunction?  Or is it probably me? I don't have my Windows partition working right now for testing because I blew it messing around with the Media Direct functionality.  Any thoughts or suggestions would be appreciated.

---

### Post by TimDaniels on 2008-08-23
Have you tried UNchecking "Enable mouse clicks with touchpad"?

As for the dysfunctioning Vista partition, which boot manager were you using - Grub in the MBR, or Vista's boot manager with the standard MS MBR?

*TimDaniels*

---

### Post by colinnwn on 2008-08-24
Yes, I have 'Enable mouse clicks with touchpad' DISabled.  I have never been able to use that feature well with Windows or Ubuntu.

I have XP (bought it just before June 30.)  I use GRUB.  I accidentally messed up the XP partition while trying to set up the Media Direct button to boot straight to XP and have the power button boot straight to Ubuntu.

---

### Post by BLTicklemonster on 2008-08-24
Mine does that because I inadvertently have a lazy finger or thumb accidentally touching the pad when I shouldn't. Drives me crazier.

---

### Post by colinnwn on 2008-08-24
At first I thought that might be the cause, so I tried placing one finger on the touchpad, and holding the rest of my digits and palm up as high as I could, and the other hand away from the keyboard.  It still happened.

---

### Post by kessaris on 2008-09-07
Hello,

I'm having the exact same problem and it's not related to any physical cause.

I also have tried a number of different settings and just when I think something works, the behaviour returns.

I just wanted to let you guys know that this problem is real and it's not caused by any rational phenomenon.  I suspected it was everything from the tap to click to the sensitivity to static electricity to aliens.

The moment I lift my finger from the touchpad, the cursor jumps back to where it was when I started.  It has nothing to do with extra fingers.  At this point I'm just a few different solutions shy of wearing a tin foil hat.

My touchpad is on a sharp laptop, and although it's recognized as a synaptics, I suspect it's a cheap knockoff.  

In any case, I'd love to be included in the event of any solution to this issue.

Regards,

Kessaris

---

### Post by colinnwn on 2008-09-07
Under XP, I do not notice this problem of the cursor jumping around while using the trackpad.  Though even in XP, this is not the smoothest trackpad I have used.  But the trackpad is still jumping around in Ubuntu.  Apparently this is not a hardware problem, and is a Linux trackpad driver problem?

---

### Post by BryanMarley on 2008-09-08
It may sound crazy, but whenever i use my touchpad on my dell xps m1530 it sometimes does the same, but just occasionally.
THe thing is, if you look in the bottom right corner in the taskbar it shows your touchpad as an image (at least my drviers do).
Whenever this occurs and i take my finger from the touchpad the image says that the touchpad is being pressed somewhere. So if i move my finger over the spot the image says where its pressed it dissapears and my touchpad works again.

+1 for weardiness

(edit: the above was a conclusion i made when using Windows Vista. the problem appeared also under XP, Mac OSX and Linux. So the problem is not OS bound in my part. The only thing was that i could see where i needed to press. in other os' i needed to press all the parts once, and then it would disappear.

---

### Post by trwww on 2008-09-09
Check to see if your power supply matches the problem power supply in the following thread:

[http://dellcommunity.com/supportforums/board/message?board.id=insp_general&view=by_date_ascending&message.id=269361#M269361](http://dellcommunity.com/supportforums/board/message?board.id=insp_general&view=by_date_ascending&message.id=269361#M269361)

I had the same problem and a new power supply fixed me right up.

---

### Post by colinnwn on 2008-09-10
> **trwww said:**
> Check to see if your power supply matches the problem power supply in the following thread:

I have a rev A00 power supply and I hadn't made the connection, because I have 3 different power supplies all different revisions.  But I am 99% sure you are right and it has only happened on the A00 power supply.  I'll press Dell to replace it.  Thanks!

---

### Post by fallenstar on 2008-10-05
I have the same problem on an Inspiron 1525, and I know why, but struggling to do anything about it.

There are 2 reasons why the touchpad jumps around, it's because circular scrolling is enabled in touchpad preferences (the GUI isn't actually installed with Ubuntu), and because it thinks there's another mouse attached.

I used to run Suse 11.0, and to get the touchpad working, you had to disable the apparition of another mouse in the sax2 module. In my xorg.conf [Ubuntu] (sudo gedit /etc/X11/xorg.conf), it can see another mouse, while I don't have one. In Suse, you went through Yast/Sax2 to remove it. I can't find the equivalent in ubuntu.

There was also an option of Touchpad settings, which you adjust, and turn off circular scrolling (which makes it jump all over the place). You can install "Touchpad" from Add/Remove Programs, but it won't initialise, giving the error message:
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I added the line 
	Option		"SHMConfig"		"true"


but it still comes up with the same error message. I'm investigating the XF86Config at the mo.

Any ideas?

---

### Post by pooyaplus on 2008-10-07
On my tx2000z laptop the cursor jumps, even before the synaptic touchpad being configured. And whenever I enable the touchpad (pushing its button) the ubuntu help center window comes up.

Any ideas?

---

### Post by Thebear on 2009-02-10
I have the same problem, but unchecking and disabling the touchpad and using an external mouse which I prefer anyway seems to do the trick. 

I have a windows Vista partition and do not have the problem on the rare occasions that I use Vista. 

I will watch this post for anyone who has a more pernanent solution that works.

---

### Post by pooyaplus on 2009-04-19
I have contacted my laptop customer service and they say this may be caused by the remaining flea power charge trapped inside the circuits. And by removing all the peripherals and AC adapter and the battery then pressing and holding the power button it will be removed.

But that did not help for me. You can also try that.

---

### Post by coire on 2010-01-21
ok i have the same problem. as i move my finger across the trackpad the cursor just jumps all over the screen and left and right clicks everywhere leaving new folders all across my desktop and just generally making a mess. also i am running karmic from a USB flash drive and this problem has ocurred on 3 different laptops using my flash drive so its not hardware and definitly not me accidently touchin the pad. thing is, this happened a couple times and a reboot fixed it but its now happening every boot and i am still pretty new to linux in general. so how about it? any old hands wanna help a noob?:D:confused::D

gonna try the flea charge theory but i cant see that being the problem in 3 different machines

---

### Post by cpighin on 2010-10-18
:) I had the same problem with my Aspire8530 under Windows7 and Ubuntu10.10.

I was able to solve the issue with Windows7 by decreasing the touch-pad (mouse) sensitivity, but not with Ubuntu and so I opened a bug request here:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/646860](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/646860)

Claudio :)

---

### Post by pooyaplus on 2010-10-18
Hi again,

I have upgraded to 10.04 lucid a few days ago. The touchpad has been installed OTB and the problem seems to be resolved here. Any other confirmations?

Cheers.

P.

---

### Post by Bononoman on 2011-07-06
> **pooyaplus said:**
> Hi again,

I have upgraded to 10.04 lucid a few days ago. The touchpad has been installed OTB and the problem seems to be resolved here. Any other confirmations?

Cheers.

P.

Well I'm having this problem crop up on me as well and I've got Ubuntu updated fully and made sure my driver where up to date and browsed this whole thread and other threads but I seam to not be able to get rid of this problem. It doesn't crop up endless I'm watching a video (in full screen), using Mupen (in full screen) or/and have the net book shut but not off.

Idk what to do I'm lost....
I'm using a HP Compaq tc4400
Specs:
CPU Duel core 1.83Ghz each
Ram 2.5 GB DDR2
Ubuntu Vr. 11.4 (natty)
Kernel Linux 2.6.38-8-generic
Flash 10.3.181.34
Blue Tooth compatible

          CompizConfig Settings:
                                Composite
                                OpenGL
                                Zoom Desktop
                                Desktop Cube
                                Expo
                                Rotate Cube
                                Ubuntu Unity Plugin
                                Window Decoration
                                Wobbbly Windows
                                PNG
                                Mouse position polling
                                Regex Matching
                                Move Window
                                Resize Window
                                Unity MT Grab Handles

Well that's all the useful info i can think of that might relate to this problem so lets be good little Linux monkeys and solve this problem.

[CENTER]P.S.
Thank You
for any and all support.:)[/CENTER]

---

### Post by tyk on 2012-01-14
> **trwww said:**
> Check to see if your power supply matches the problem power supply in the following thread:

[http://dellcommunity.com/supportforums/board/message?board.id=insp_general&view=by_date_ascending&message.id=269361#M269361](http://dellcommunity.com/supportforums/board/message?board.id=insp_general&view=by_date_ascending&message.id=269361#M269361)

I had the same problem and a new power supply fixed me right up.

This is absolutely right. Many thanks.

Try this - unplug the power supply from the laptop while keeping a finger on the touchpad. While the cursor would be quivering and/or jumping away when the power is plugged in, it stabilizes and becomes usable when the power is plugged out.

Thanks again and I'll get Dell to replace about power adapaters for about 6 laptops that I bought for my company :)

Here's a link to a Dell response to a customer query - [http://en.community.dell.com/support-forums/laptop/f/3518/p/19271502/19474971.aspx#19474971](http://en.community.dell.com/support-forums/laptop/f/3518/p/19271502/19474971.aspx#19474971)

Cheers,
Swastik.

---

### Post by Stabledog on 2013-01-23
2012, and I still have this problem.  Today I had an epiphany: if I take my finger, and sweep it all round the touchpad as if I were polishing the thing, the problem goes away.  For a while.   Apparently my problem is some sort of static buildup, not software or hardware.

---

### Post by virtualx on 2013-09-13
Just wanted to confirm this problem / fix with an ASUS K55A laptop and ASUS Model EXA1202YH Rev:02  AC Adaptor (power supply).

---

