---
title: "Inspiron 14 Core i5"
date: 2010-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luisg on 2010-02-17
So, I ordered a new Inspiron 14, Core i5 430M +  ati hd4330 + wireless Dell 1520. Fantastic price.

First thing I'll do on arrive is to install Ubuntu (I'm windows free since some years ago). Are there any known issues or considerations for Karmic, or should it work as usual?

Thanks.

---

### Post by manishmahabir on 2010-02-27
how is your experience bro?

---

### Post by luisg on 2010-03-04
The Inspiron has been great so far, no issues at all.

Coming from an HP Pavilion dv5z with a hot AMD Thurion X2 RM-70, the Intel Core i5 is really fast and cool (like in cool beer ;) ). Even at similar clock speeds (2 MHz for AMD vs 2.27 for Intel), a non-scientific benchmark converting a video with Avidemux gave me 3:00 on the HP, and 1:45 on the Dell, and that's only one core at use, there are 3 more idle.

Also, VLC works great with a Matroska 1080p video, wich was simply not possible on the HP.

Wireless is actually a Broadcom, which worked with the propietary drivers provided by Karmic. No problems with ATI either (but I'm not a PC gamer).

It surprised me to find an HDMI port, it's not advertised anywhere on the Inspiron's specs.

Don't know yet about battery life, I guess is somewhere between 4 and 6 hours (9 cell battery) but I've not made a controlled measurement.

Anything else, just ask.

---

### Post by Riot@ct on 2010-03-04
> **luisg said:**
> The Inspiron has been great so far, no issues at all.

Coming from an HP Pavilion dv5z with a hot AMD Thurion X2 RM-70, the Intel Core i5 is really fast and cool (like in cool beer ;) ). Even at similar clock speeds (2 MHz for AMD vs 2.27 for Intel), a non-scientific benchmark converting a video with Avidemux gave me 3:00 on the HP, and 1:45 on the Dell, and that's only one core at use, there are 3 more idle.

Also, VLC works great with a Matroska 1080p video, wich was simply not possible on the HP.

Wireless is actually a Broadcom, which worked with the propietary drivers provided by Karmic. No problems with ATI either (but I'm not a PC gamer).

It surprised me to find an HDMI port, it's not advertised anywhere on the Inspiron's specs.

Don't know yet about battery life, I guess is somewhere between 4 and 6 hours (9 cell battery) but I've not made a controlled measurement.

Anything else, just ask.
Great, can you confirm to me that ati hd4330 works without problems?
Have you installed the restricted driver from ubuntu repository?
Compiz works?
Thanks a lot.

---

### Post by akand074 on 2010-03-04
> **luisg said:**
> The Inspiron has been great so far, no issues at all.

Coming from an HP Pavilion dv5z with a hot AMD Thurion X2 RM-70, the Intel Core i5 is really fast and cool (like in cool beer ;) ). Even at similar clock speeds (2 MHz for AMD vs 2.27 for Intel), a non-scientific benchmark converting a video with Avidemux gave me 3:00 on the HP, and 1:45 on the Dell, and that's only one core at use, there are 3 more idle.

Also, VLC works great with a Matroska 1080p video, wich was simply not possible on the HP.

Wireless is actually a Broadcom, which worked with the propietary drivers provided by Karmic. No problems with ATI either (but I'm not a PC gamer).

It surprised me to find an HDMI port, it's not advertised anywhere on the Inspiron's specs.

Don't know yet about battery life, I guess is somewhere between 4 and 6 hours (9 cell battery) but I've not made a controlled measurement.

Anything else, just ask.

HDMI ports come standard with most new laptops now. There is a significant difference between the core i5 and that AMD Turion though. The Core i5 chipset is much more advanced and has a technology that Intel calls "Turbo Boost" which takes power from your inactive cores and "turbo boosts" your active cores. So if only one core is in use, your frequency will be 2.53GHz (max turbo). As a result, it should be significantly faster. Not to mention that it also has hyper threading which makes it act as 4 cores (ubuntu should see it as 4 cores). Pretty cool.

---

### Post by luisg on 2010-03-04
> **Riot@ct said:**
> Great, can you confirm to me that ati hd4330 works without problems?
Have you installed the restricted driver from ubuntu repository?
Compiz works?
Thanks a lot.
Yes, it works with the restricted driver from karmic repository. Compiz is working fine.

I almost forget, there is one issue which tormented me the full 2 hours I spent on Windows 7: keyboard seems to "rreppeat some kkeys while ttypping ffast". Google revealed it happens with other Dell models too, it does not look like a manufacturing problem, but a design related one. I did not found a solution.

I was starting to regret my purchase, but after installing Karmic I found there are some settings in Keyboard Preferences that completely eliminate the problem :)

---

### Post by Riot@ct on 2010-03-04
> **luisg said:**
> Yes, it works with the restricted driver from karmic repository. Compiz is working fine.

I almost forget, there is one issue which tormented me the full 2 hours I spent on Windows 7: keyboard seems to "rreppeat some kkeys while ttypping ffast". Google revealed it happens with other Dell models too, it does not look like a manufacturing problem, but a design related one. I did not found a solution.

I was starting to regret my purchase, but after installing Karmic I found there are some settings in Keyboard Preferences that completely eliminate the problem :)
Greaaaaaat :)
I want buy the DELL Inspiron 1564 with ATI Radeon HD4330 512MB and mini wireless Dell 1397 (802.11 b/g).
Have you the mini wireless Dell 1397? Works?
Thank you for your replies.
And sorry for my english. :D

---

### Post by luisg on 2010-03-05
> **Riot@ct said:**
> Greaaaaaat :)
I want buy the DELL Inspiron 1564 with ATI Radeon HD4330 512MB and mini wireless Dell 1397 (802.11 b/g).
Have you the mini wireless Dell 1397? Works?
Thank you for your replies.

Well, I'm not sure how Dell is naming (or packaging) its wireless cards. It was advertised as a Dell 1397 at the package selection page at dell, then next page says it is a Dell 1520, and finally lspci on Ubuntu shows a Broadcom BCM4312. Anyway, it worked with restricted drivers from karmic.

> **Riot@ct said:**
> And sorry for my english. :D
Good, this way you can't notice I'm not an english speaker either...

---

### Post by tom957 on 2010-03-06
Thanks a bunch for the info. I've been looking for an Ubuntu-friendly laptop for a while now and will highly consider this one.

---

### Post by Riot@ct on 2010-03-06
> **luisg said:**
> Well, I'm not sure how Dell is naming (or packaging) its wireless cards. It was advertised as a Dell 1397 at the package selection page at dell, then next page says it is a Dell 1520, and finally lspci on Ubuntu shows a Broadcom BCM4312. Anyway, it worked with restricted drivers from karmic.

Thank you a looooooot! :D

> **luisg said:**
> 
Good, this way you can't notice I'm not an english speaker either...
:lol:

---

### Post by nortexoid on 2010-03-08
From what I've read, you might want to keep that copy of Windows 7 on the machine (e.g. by dual booting) if you really want to get the most out of your battery. And if you did so, I would be very interested in hearing some more of those non-scientific benchmarks, but this time comparing battery life in Ubuuntu vs. Windows 7.

---

### Post by luisg on 2010-03-09
> **nortexoid said:**
> From what I've read, you might want to keep that copy of Windows 7 on the machine (e.g. by dual booting) if you really want to get the most out of your battery. And if you did so, I would be very interested in hearing some more of those non-scientific benchmarks, but this time comparing battery life in Ubuuntu vs. Windows 7.

I'm dualbooting, but to be honest I've used it about four (non continuous) hours in two weeks, mostly applying updates, so I can't comment about battery.

I have a problem with battery tests on windows (vista, at least): there are lots of variables to control before performing a fair and reliable test. A vainilla windows have superfetches and autoindexes and autoupdates (and warnings "close everything because I will restart in 10..9..8.."), and autorecoveries, and mcafees, and dozens of auto-i-want-an-update-too programs, and then there are power profiles... In the end, Vista consistently gave me less battery life and more heat than Jaunty. I know, maybe I'm the problem and I need to do something about my neurosis... ](*,) 

I understand that could be different on win7, so I guess it's worth to perform some tests watching movies or listening to music, and repeat with karmic. I'll be back.

---

### Post by nortexoid on 2010-03-09
> **luisg said:**
> I'm dualbooting, but to be honest I've used it about four (non continuous) hours in two weeks, mostly applying updates, so I can't comment about battery.

When you actually do get around to some "ordinary" usage (browsing, document creation, etc.), it would be nice to see some figures showing battery life in Windows vs Ubuntu. If you can't be bothered, no biggie.

> I have a problem with battery tests on windows (vista, at least): there are lots of variables to control before performing a fair and reliable test. A vainilla windows have superfetches and autoindexes and autoupdates (and warnings "close everything because I will restart in 10..9..8.."), and autorecoveries, and mcafees, and dozens of auto-i-want-an-update-too programs, and then there are power profiles... In the end, Vista consistently gave me less battery life and more heat than Jaunty. I know, maybe I'm the problem and I need to do something about my neurosis... ](*,)

If you're running off battery, obviously you won't be doing things like virus scanning, indexing, etc. So it's only fair to have those things disabled. (They should automatically be disabled when running off battery.) I imagine the most fair comparison would be to *remove* all that Windows crap and compare a fresh (or equivalent) install of Windows with Ubuntu.

---

### Post by poision_heart on 2010-03-09
hi
i ve dell inspiron 14 with core i3 

its fast as well..i ve ubuntu 910 on it n working really nice with ATI 4330.
do share your experince

---

### Post by luisg on 2010-03-15
> **nortexoid said:**
> When you actually do get around to some "ordinary" usage (browsing, document creation, etc.), it would be nice to see some figures showing battery life in Windows vs Ubuntu. If you can't be bothered, no biggie.

If you're running off battery, obviously you won't be doing things like virus scanning, indexing, etc. So it's only fair to have those things disabled. (They should automatically be disabled when running off battery.) I imagine the most fair comparison would be to *remove* all that Windows crap and compare a fresh (or equivalent) install of Windows with Ubuntu.

I'm back.

Test: With battery fully charged, shutdown laptop. Unplug power cord.
Boot OS.
Connect laptop to 42" LCD TV via VGA, home theather via RCA.
Plug wireless keyboard, plug wireless mouse.
Set display properties to never turn off.
Start firefox, start media player (wmp, rhythmbox). Play mp3 continuously, browse, try to avoid videos and flash.
Stop test on 10% charge left according to OS battery indicator.

Results: Amazingly similar between karmic and win7, about 4 hours from 100% to 10% charge. Maybe karmic gave a bit more juice, but there are more significant factors to consider like indicator accuracy and my own behavior, so I'd say for all practical purposes it can be considered a tie.

---

### Post by nortexoid on 2010-03-15
> **luisg said:**
> I'm back.

Test: With battery fully charged, shutdown laptop. Unplug power cord.
Boot OS.
Connect laptop to 42" LCD TV via VGA, home theather via RCA.
Plug wireless keyboard, plug wireless mouse.
Set display properties to never turn off.
Start firefox, start media player (wmp, rhythmbox). Play mp3 continuously, browse, try to avoid videos and flash.
Stop test on 10% charge left according to OS battery indicator.

Results: Amazingly similar between karmic and win7, about 4 hours from 100% to 10% charge. Maybe karmic gave a bit more juice, but there are more significant factors to consider like indicator accuracy and my own behavior, so I'd say for all practical purposes it can be considered a tie.

Thanks, that's very helpful!

---

### Post by luisg on 2010-05-28
I'm back to report about 10.04 - Lucid Lynx.

For no particular reason - beyond the raving reviews about Lucid -, I decided to go for it, and did a clean install on my Inspiron.

Unfortunatly, this time I found several issues:

* ATI Open Source drivers, now installed by default, are perfectly functional enabling 3D compiz effects. However, laptop runs significantly hotter, and battery life is shorter (see [this thread]("http://ubuntuforums.org/showthread.php?t=1465791")).
* ATI propietary drivers manage temperature a lot better (in my case, anyway). However, now Power Managment Settings behaves strange, lcd brightness slider does not work at all, fixing it at 100%. Gnome Brightness applet does nothing at all. Fn+F4 y Fn+F5 keys work, but lucid resets brightness to 100% after reboot.
* ATI propietary drivers also lowered the resolution on splash boot screen, so Ubuntu logo looks ugly.  A minur issue, but strange.
* Sometimes Power Management forgets to turn off the screen.
* Touchpad feels strange no matter which settings I use, sometimes too sensitive, sometimes too slow. It's hard to describe, probably my own fault. Every now and then pointer seems to "hit a wall" and goes back to normal after a while.

Finally, something broke after trying to install some applications with apt-get. It's not hardware related and probably fixable, but I felt that was enough, so inserted my Karmic disk and downgraded.

Trying to give it a second chance, I' dual booting Linux Mint 9 (which is based on Lucid). Touchpad seems a lot better, but Power Management issues remain.

May be I'll try Lucid again on a couple of months.

-------
Update 2010-06-03:
* LCD brightness problem is solved in Lucid by installing ATI Catalyst Driver 10.5, downloaded from ATI page (Restricted Drivers Manager installs v10.3). Remember, you need build-essential if you want to install this version, and kernel updates will break the drivers, so you'll need to reinstall them every time.

---

### Post by Guitar John on 2010-05-30
> **luisg said:**
> <snip> keyboard seems to "rreppeat some kkeys while ttypping ffast". Google revealed it happens with other Dell models too, it does not look like a manufacturing problem, but a design related one. I did not found a solution.

I was starting to regret my purchase, but after installing Karmic I found there are some settings in Keyboard Preferences that completely eliminate the problem :)

Just out of curiosity, what settings did you have to change?

---

### Post by luisg on 2010-05-30
> **Guitar John said:**
> Just out of curiosity, what settings did you have to change?

System - Preferences - Keyboard - Accessibility

Check "Ignore Fast Duplicate keypresses" and adjust the "Delay" slider. I like it near to the "short" side.

---

