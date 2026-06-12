---
title: "External monitor with laptop question"
date: 2009-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by allaboutsam on 2009-02-17
I have a Dell Latitude D400 with a native screen resolution of 1024x768, running 8.10. I would like to buy a 17" external LCD to use with it, but they all have native resolutions of 1280x1024.

Will I be able to use the full 1280x1024 resolution?

There is one post about this from two years ago <http://ubuntuforums.org/showthread.php?t=118907> that basically said no, but that was two years ago. Anything since then?

Many thanks,
allaboutsam

---

### Post by Cybie257 on 2009-02-17
My first impression of this was that you were going to get hitover the head with a hammer for asking this here. But, as I realised, this can be a tricky thing with Linux to have 2 monitors with different resolutions. With windows, I'd say, not a problem and NOT because Windows is better, but because the drivers are generally designed for windows for best results. 

I'm currently running 2 monitors with 8.10, but both are 19 widescreens with an ATI Dual-Head video card, and not on a laptop. ATI has been stepping up to the plate and designing better and better Linux drivers, but the way it seems to work correctly with dual screens is with a total desktop size and not independent of each monitor. it works for now, so I leave it alone. :)

I would recommend that you share your hardware information with everyone, such as the Video card brand (IE: Intel, ATI, nVidia). That would probably be a good place to start and get with with. 

-Cybie

---

### Post by yakker.yak on 2009-02-17
It should just work. I've had similar setups with 8.04 and 7.04 with two different laptops.

Just make sure the monitor is plugged in when you boot up. Otherwise, go to the display preferences and click on the detect displays button.

If that doesn't work there's always manual methods:
[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

---

### Post by allaboutsam on 2009-02-17
I've hit myself over the head with a hammer a couple of times this morning trying to figure this out, so one or two more bashes shouldn't do too much harm :). Here's the graphics controller output from lspci:

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

According to Intel's web site, it does support dual independent monitors, but I couldn't find resolution information there. I tried plugging in an old CRT, and I did indeed get one big desktop. For resolutions on the CRT, Ubuntu offered me (in addition to lower ones) 1024x768 and 1280x768, but not 1280x1024. I know the monitor supports 1280x1024; I didn't know it supported 1280x768.

---

### Post by Cybie257 on 2009-02-17
You might have to go in and change the Xorg.conf file to get the other 1280X1024 resolution. And yes, correct, the Intel will allow the additional monitor, just never tried it on my laptop. Guess I should just to see how it works, but usually only use the laptop away from home. 

Sounds like you're on your way to getting it figured out, though. My only suggestion from here is to edit, or at least see if the resolutions are showing up for the second monitor in the Xorg.conf file. I have only used dual monitors on my tower with the ATI Dual-head and that has it's querks and probably not going to help me help you with the Intel chipset. I'll update this if I get a chance to plug in another monitor to my laptop, though. 

-Cybie

---

