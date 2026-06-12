---
title: "World of Warcraft - Radeon 9550 Success Stories"
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by scifi76 on 2007-02-13
I have an ATI Radeon 9550 and I've just managed to get world of warcraft up and running, which I'm fairly impressed with (after all this is not supposed to run on linux). However I still get a REALLY low, unplayable FPS (~5fps outdoors, but up to 30 indoors). I know the drivers are notoriously bad for ATI on linux, so I'm wondering whether to just put it down to a bad combination of card and drivers that just isnt supported that well.

So I'm wondering, is there anyone out there who has a Radeon 9550 (or very similar) who has managed to make WoW work on ubuntu as well as or better than in windows, or at least so it is playable? If so, please post your hardware specs and anything you needed to do to get it working.

It would be interesting to work out whether the Radeon 9550 categorically does not work well based on the responses to this post...

---

### Post by Slychilde on 2007-02-13
I do not have a Radeon 9550, but I do have a x1400 in my laptop, which plays WoW just fine.  It took a little work to get it stable, though.  I'm not entirely sure how much better my card is than yours, if at all.  These two links have info that proved invaluable to me, hopefully they will help you.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  - you MUST do the regedit trick, or your fps will be 5, like yours.  Mine went from 5-10 to 30.

[http://ubuntuforums.org/showthread.php?t=156841](http://ubuntuforums.org/showthread.php?t=156841) - has a helpful tip if  your game keeps crashing the second you log in.

My laptop is a Dell: dual 1.6's, 1Gig of ram, ATI x1400.  I really, really wish I would have upgraded to a hard drive with a higher RPM.  Stupid bottleneck.  What are the full specs of your pc, and what kind of FPS were you getting in windows?

Oh, fps was measured using the monitor in bongos.

---

### Post by scifi76 on 2007-02-13
Thanks for replying sly. Would you be able to post the contents of your Config.wtf file? I think im down to fiddling with the settings within wow to get it working nicely, but it crashes whenever I use the in-game settings (in both OpenGL and d3d mode) so I have to edit the config.wtf file manually

I have done the regedit tweak btw

As for my spec I have a 2.8Ghz P4, 1GB Ram and Radeon 9550 card. I think the graphics card is the one thing that lets my PC down. I'm running off a SATAII HD so that shouldnt be a problem either. In windows I get a stable FPS of about 25-30 while playing WoW. Thats not an FPS to brag about but at least it's playable.

In Ubuntu I can get up to 40FPS (fantastic!) if im indoors, but as soon as I go outside it grinds to a horrible 3-5fps. 

Since making the original post I have changed some of the settings and taken the draw distance down to minimum and also put it in windowed mode. This seems to bring it closer to my windows performance, if a little choppy, but I would really like to turn the draw distance up a little. I would be happy if I could get performance near-on par with windows, with more or less the same settings.

FPS was just measured using an ingame addon, so I'm not sure how accurate it is.


Edit: Also, could you post whether you are using the proprietory ATI driver (from the ATI website), or the Open Source driver? I'm using the prorietory one.

---

### Post by Slychilde on 2007-02-13
Here's my config.wtf info.  I intially copy/pasted the whole wow directory from my desktop pc, then edited it with some tweaks.  Usually I have all sound off, but I was messing with settings, so it's on partially in this file.  And yes, I definitely agree, it has to be your video card holding you back, hehe.  Also, I think changing: SET particleDensity "1.000000" to 0 would help me out even more, but I likes eye candy (think I read that somewheres).

```
SET locale "enUS"
SET timingTestError "0"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET MusicVolume "0.5"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmList "us.logon.worldofwarcraft.com"
SET realmName "Kirin Tor"
SET gameTip "48"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET profanityFilter "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET readScanning "-1"
SET readContest "-1"
SET expansionMovie "0"
SET checkAddonVersion "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET EnableMusic "0"
SET EmoteSounds "0"
SET SoundListenerAtCharacter "0"
SET lastCharacterIndex "5"

```

---

### Post by scifi76 on 2007-02-13
Excellent, this gives me something to refer to when im messing about with my settings. At least here I have a working config to compare to.

First thing I did notice is that farclip on my config file was originally set to 777, where your's is 477. This might explain why it's killing my frame rate

Also could you let me know which driver you are using? ATI's or the Open Source one?

I'll have a mess about and post back with my results, for anyone who's interested.

---

### Post by Slychilde on 2007-02-13
I'm using the latest proprietary ATI drivers, which I installed manually (method 2) by following [these]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") instructions.

---

### Post by scifi76 on 2007-02-14
Yeah me too.

I managed to get decent performance by using the settings listed in the suggested linux config file found here: 

[http://appdb.winehq.org/appview.php?iVersionId=6482]("http://appdb.winehq.org/appview.php?iVersionId=6482")

I've managed to turn some of the settings UP from whats listed on this page, so now I have most of the special shader options on, but I still have to keep the draw distance fairly low, but I can live with that. I also noticed that there is a slight stutter in graphics, every 5 secs or so, but it is barely noticeable.

I will continue to mess with the config file until I get the best results I can

---

### Post by Toxicity999 on 2007-02-15
Hey ,I was playing fine with the open source drivers on my Radeon 9000 Mobility 32mb, trick is, lowest possible options, and tons of xorg.conf tweaking, look into it. It all depends on your card.

---

### Post by zachws on 2007-02-17
Turn off that full screen glow!

---

### Post by scifi76 on 2007-02-23
Yes! I've finally got it working quite nicely, with more or less the same settings I was using in windows and im probably getting better performance, most of the time

Full screen glow works fine for me, but there are some other options I had to turn off
I had to turn the draw distance down a bit, and antisotrophic filtering is off (but only cos I cant work out the config.wtf value to switch it on). Everything else is on full.

---

