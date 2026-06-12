---
title: "Vostro 1500, some tweaking to do."
date: 2008-01-09
forum: Dell  Ubuntu Support
---

### Post by dtwwtd on 2008-01-09
A few weeks ago I got a Dell Vostro 1500. Right away I ubuntu'd it, and have had few problems since. I got the install working with media direct on the first try, and with few problems, got the Broadcom wireless and Intel audio working as well.
I also have Compiz Fusion and AWN running.

core 2 duo 1.6 GHz,  1GB RAM,  160gig hdd,  broadcom wireless, nvidia 8400gs,  bluetooth, etc..

However, after using it the past few weeks, I've found some things that could be fixed. 
first, and others have reported these two things as well, the internal speakers play even when there are headphones. Also, the battery life in gutsy is about 3 hours compared to the 4.5 -5 hours in Vista HP.
I've not been able to find fixes for these these.

Secondly, I've discovered that after coming back up from suspend, I no longer have sound. Also, I discovered last night that after using suspend that the disc drive no longer recognizes blank CDs.
(Thus no disc burning after using suspend, until a reboot.)

These few minor problems would be handy to have fixed but not critical. I still love Ubuntu on my vostro, and won't be going back to vista for much soon.

---

### Post by icecoldtony on 2008-01-10
I've got a Vostro 1000 and am having a hell of a time getting the wireless 
working. What did you do? Also I tried to get awn installed and working and didn't have any luck there also. If you could point me in the right direction I'd really appreciate it. Thanks.

---

### Post by saru411 on 2008-01-10
> **icecoldtony said:**
> I've got a Vostro 1000 and am having a hell of a time getting the wireless 
working. What did you do? Also I tried to get awn installed and working and didn't have any luck there also. If you could point me in the right direction I'd really appreciate it. Thanks.

please make your own thread with your issues. please include what hardware specs that are relevant also, such as what wireless card you are using. also include which version of ubuntu you are running.

---

### Post by dtwwtd on 2008-01-10
> **icecoldtony said:**
> I've got a Vostro 1000 and am having a hell of a time getting the wireless 
working. What did you do? Also I tried to get awn installed and working and didn't have any luck there also. If you could point me in the right direction I'd really appreciate it. Thanks.

If you have the Dell 1390 Wireless you can follow this guide:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

After trying other things, this one worked. I did not have to reinstall ubuntu before trying it as he recommends, but you may have to. As for AWN, I added it to the apt sources. I believe I followed the guide in the ubuntu wiki...

Does anyone have any ideas about the problems I posted above?
Any help would be greatly appreciated.

---

### Post by dtwwtd on 2008-01-11
Could anyone help me?
The one thing I would really like to fix is the suspend issues. Whats the point of using it if you have to reboot?

---

### Post by ACGarib on 2008-01-12
I also have a Vostro 1500 with the same problems and no matter what I tried, I could not get suspend to resume properly or get the speakers to mute with headphones. Maybe you will have more luck: [http://ubuntuforums.org/showthread.php?t=577469&highlight=1520](http://ubuntuforums.org/showthread.php?t=577469&highlight=1520)

As for the battery life, try looking at the power management settings. Also, check to see what mode your processor is in (onDemand, powersave, performance) by adding CPU frequency monitor applet to one of your taskbars. (right-click the taskbar, then add to panel)

I guess us Vostro/Inspiron owners will just have to wait until the next ubuntu release and hope that sound/suspend are fixed.

If you ever find out how to fix the sound and suspend, make sure to create a thread telling us how to do it so the rest of us can enjoy listening to music in private after we resume from suspend!

---

### Post by ACGarib on 2008-01-12
I just found a crude workaround for the auto mute problem.

[http://ubuntuforums.org/showthread.php?p=4124682#post4124682](http://ubuntuforums.org/showthread.php?p=4124682#post4124682)

The only problem is that my headphones don't have any bass and way too much treble when they are plugged into the mic port compared to the headphone port.

Not hearing static while I'm listening to my podcasts through the mic port is a huge plus for me.

Hopefully this works on all Vostros, not just mine.

---

### Post by dtwwtd on 2008-01-12
Hey, thanks alot!
I got that fix working as well.
I'm very happy with it - even if its not the intended way to do it.

---

### Post by ocarinahuff on 2008-02-02
Try installing both linux-backports-modules and libasound2-plugins.  That got my headphones working on the Vostro 1500 the way it should.

---

### Post by dtwwtd on 2008-02-08
> **ocarinahuff said:**
> Try installing both linux-backports-modules and libasound2-plugins.  That got my headphones working on the Vostro 1500 the way it should.

That doesn't seem to have worked. My headphones now work when I plug them in the jack, however, the built in speakers do not mute. So both headphones and speakers are playing at the same time.

---

### Post by dtwwtd on 2008-02-08
Please disregard the previous post. My sound now works perfectly fine. (After a reboot, I jumped the gun in saying it didn't work)

---

### Post by nfox on 2008-03-04
Yea, about disregarding that post....

I still have sound coming out of headphones and internal speakers at the same time. No reboot-action for me. 

Does anyone know a fix for that? I'm not looking to recompile ALSA after having sought directions the first time...

---

### Post by lobo235 on 2008-03-09
Installing both linux-backports-modules and libasound2-plugins solved the problem on my vostro 1500 as well.

---

### Post by msailg on 2008-03-11
Hi
I installed 7.10, for AMD64 and intel, did you install the same. I do not have speakers working at all. I was going to try the 7.10 i386 to see if that worked, do you have any comments?

---

