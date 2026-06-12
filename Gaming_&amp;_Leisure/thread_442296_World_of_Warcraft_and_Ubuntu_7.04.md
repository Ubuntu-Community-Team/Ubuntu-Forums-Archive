---
title: "World of Warcraft and Ubuntu 7.04"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by tipalm73 on 2007-05-13
Well I have made some progress getting wow running, but cant *actually* play...

**[Story so far]**

Notebook
2.4 ghz AMD64 3700+
1 gig ddr2 ram
128 Ati Mobiity Radeon AGP GFX card
60 Gig WD 7200 rpm HDD
(playing Burning Crusades)

I have updated/upgraded ATI Drivers/Wine

in winecfg I have turned on OSS.

Here is my Config.wtf file from WoW:

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET specular "1"
SET pixelShaders "1"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET gxMultisampleQuality "0.000000"
SET expansionMovie "0"
SET realmName "Gilneas"
SET gameTip "1"
[B]
[Present][/B]

Wow starts i use: $ sudo wine Wow.exe -opengl

The blue bar goes across the wow screen. I dont see myself, initially.  Things slowly load in. Then, like clock-work, the audio skips, the screen freezes and I have to reboot system cause I cant break wow.

Help!

Thanks in advance.

---

### Post by justin whitaker on 2007-05-13
Try modifying the Alsa settings. 

The directions are here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also, I noticed the past couple of days that the big patch is slowing the game down, and playing havok with Alsa on my system. Disable the automatic download.

---

### Post by ShadowFlar3 on 2007-05-27
If you'll follow the steps in the link above you should get your framerate up noticeably with the registry tweak.

Also, add SET gxApi "opengl" in your config.wtf so you don't have to run WoW with -opengl every time.

And of course, make sure your ATI drivers are working correctly (ATI drivers are sometimes tricky to get working) by doing:

glxinfo | grep rendering

You should get Direct rendering: Yes.

---

