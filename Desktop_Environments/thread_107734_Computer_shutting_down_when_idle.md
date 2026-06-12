---
title: "Computer shutting down when idle?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by rozojc on 2005-12-23
Well, I convinced my parents of using Ubuntu instead of Windows and they've liked it a lot. However, I'm having a really weird problem...

The computer was working fine, no problems at all. I reformatted it, installed Windows 2000 on it (my mom needs to use some ACCESS stuff for work) and Breezy. Everything went fine, normal installation etc... However, now when the computer can't stand 5 minutes idle without shutting down.

Now, what I've noticed is that it seems to be the motherboard the one shutting down the computer, as the computer won't start unless I literally unplug it from the outlet and plug it in again... weird... I remember that motherboards sometimes do that when there's something wrong (hard drive, RAM, things like that, right?), but the thing is that the computer was working perfectly until I reinstalled everything for my parents...

Any ideas of why is it shutting down? I don't really think it's (for example) temperature because it actually happens when it's idle, when you are using it it doesn't happen...

Any help will be really appreciated!

---

### Post by darth_vector on 2005-12-23
go to the gnome menu and select -> System -> Preferences -> Screensaver. Select the advanced tab and have a look at the Power Management options. Maybe your machine is set to power down if left idle.

---

### Post by rozojc on 2005-12-24
[QUOTE=darth_vector]go to the gnome menu and select -> System -> Preferences -> Screensaver. Select the advanced tab and have a look at the Power Management options. Maybe your machine is set to power down if left idle.[/QUOTE]

Well, the thing is that it's not a power down like if it killed all the processes and then shutted down, it just powers down immediately and doesn't start unless I pull the plug off and on again...

---

### Post by kosmic on 2005-12-24
It can be a Faulty Power supply :)

---

### Post by rozojc on 2005-12-24
[QUOTE=kosmic]It can be a Faulty Power supply :)[/QUOTE]
Is there any way I could confirm this before changing it and finding out it was another thing?

Another weird thing: if I boot via a Live CD it seems to work correctly (without shutting down)... I did an fsck but it didn't report any bad sectors on the hard drive...

---

### Post by msodrew on 2006-01-31
I have this problem too... the computer just shuts down after being idle for a lil while. its so gay.

---

### Post by qferret on 2006-01-31
I had this issue. Mine wasn't actually shutting down, but the monitor would go into standby and refuse to wake up, no matter what. It was apparently random, as sometimes in would go for days...sometimes it would happen several times in a day.

Sometimes holding the power button in for 5-10 seconds would kill it the rest of the way, allowing me to start it back up....sometimes I would have to flip the main on the PSU.

I happened to catch it a few times where the screensaver seemed to lock up for a few seconds before it happened. So I went in & picked a simple screensaver to stick with, instead of cycling through them (ubuntu has an awesome selection of screensavers, but I really miss the matrix one from knoppix.ru that was in Hoary & my russian sucks, so I can't find it on the site LOL)

This seems to have solved the issue 100% (Stupid ATI card)

---

### Post by rozojc on 2006-01-31
Well, I had forgotten to say I finally solved my issue. At first I thought it coulnt't be the processor getting too hot since it had never happened before, but  after keeping an eye on the temperature, I started thinking that the computer's new place (I had recently changed where I had the computer) was less ventilated and more warm. I asked my parents if the computer would shut down more often at a specific time of the day, and they actually said that on the afternoons when it's sunny. So I opened it, cleaned the heat fan (which was absolutely cluttered with dust), and they haven't had a shut down since...

So in the end, it had a heat problem which hadn't caused trouble before just because the computer used to be kept at a cooler place!

---

### Post by ivuntu on 2006-02-05
[QUOTE=qferret]I had this issue. Mine wasn't actually shutting down, but the monitor would go into standby and refuse to wake up, no matter what. It was apparently random, as sometimes in would go for days...sometimes it would happen several times in a day.

Sometimes holding the power button in for 5-10 seconds would kill it the rest of the way, allowing me to start it back up....sometimes I would have to flip the main on the PSU.

I happened to catch it a few times where the screensaver seemed to lock up for a few seconds before it happened. So I went in & picked a simple screensaver to stick with, instead of cycling through them (ubuntu has an awesome selection of screensavers, but I really miss the matrix one from knoppix.ru that was in Hoary & my russian sucks, so I can't find it on the site LOL)

This seems to have solved the issue 100% (Stupid ATI card)[/QUOTE]

I had the exact same thing, I noticed that my monitor would go into standby, when I was testing and viewing screensavers. Too bad the nicer screensavers apparently don't work.l I have NVidia 6600 GT AGP by the way, so it's not only ATI cards!

---

### Post by ivuntu on 2006-03-08
Hello Folks,

just to close my contribution here, I found out that my videocard XFX Nvidia 6600 GT AGP was the problem. I had the same problem in Windows XP when I was playing games: the monitor would go into standby after a period ranging from 10 seconds  to 15 minutes. same with linux games and screensavers.

My solution was twofold:

 I connected my AGP video card with a power connector on the backside of the card (this probably helped the power problem). I did not even now this was possible until I read about it in the manual :-k (ahem)

second: I placed another fan nearby the video card (to help cooling; temperatures ranges in games now from 60 to about 85.)

I have no problems any more with this. Hope this helps.

---

### Post by dannyboy79 on 2008-04-11
well I have recently began to have this problem. the first time I couldn't even turn it back on?? So I took all apart and cleaned it out with a air blaster (carefully of course). It was very dusty because I smoke next to it. I do have an exhaust fan for the cpu fan out of the side and I have a rear exhaust fan. I verified all connections and they were all seated properly. So when I hooked it all back up, sure enough it turned back on and was working. Well, for the last 2 days, it just shuts off without warning, it's idle (besides ssh server, gaim, torrents once in awhile) but it's also my main mythtv server so it needs to stay running if I want to record my shows. I looked in syslog, kern.log, dmesg and I can't see anything that would be shutting it down? Where would I look. I have a power supply checker so I guess I should check to make sure that's not going bad but it's a fairly new psu. I also have a different cpu fan (thermaltake or whatever) )I could install but like I said I never used to have this problem with the stock fan that came with the E4300 C2D.

The specs are: 
AsRock 775Dual-VSTA
E4300 C2D (stock fan)
2GB RAM (533mhz)
600W Zion PSU
Optiarc DVD RW AD-7170A
Floppy Drive
GeForce 6200
Texas Instruments FireWire Controller PCI Card

This machine runs 24/7, that is when it doesn't turn itself off. Any help would be appreciated.

---

