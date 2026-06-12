---
title: "WOW woes"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by gantww on 2007-06-12
Hello all,
I've been trying to get WOW working again. Now it's trying to download a patch to go from 2.1.0.6692 to the next version. Anyway, it just sits there. It's been an hour and the 16kb file isn't downloaded. Any ideas as to what could be breaking the downloader?

---

### Post by Big Bear on 2007-06-12
> **gantww said:**
> Hello all,
I've been trying to get WOW working again. Now it's trying to download a patch to go from 2.1.0.6692 to the next version. Anyway, it just sits there. It's been an hour and the 16kb file isn't downloaded. Any ideas as to what could be breaking the downloader?

I had the same problem... I just launched wow.exe and let the game take care of the rest... don't need the launcher, gtg.

---

### Post by gantww on 2007-06-12
I downloaded the patches manually. Seems to be working. It's close, but I still have a couple of issues:
1) Video is choppy. The intro video only plays on part of the screen. Movement is choppy in-game.
2) Can't change video settings. The game just locks up. It's stuck on 1024x768, which it wouldn't even do on windows. I had it at 800x600 there.
3) It alters my desktop resolution and doesn't put it back. I think I can probably fix this with a clever shell script, though.

---

### Post by Big Bear on 2007-06-12
> **gantww said:**
> I downloaded the patches manually. Seems to be working. It's close, but I still have a couple of issues:
1) Video is choppy. The intro video only plays on part of the screen. Movement is choppy in-game.
2) Can't change video settings. The game just locks up. It's stuck on 1024x768, which it wouldn't even do on windows. I had it at 800x600 there.
3) It alters my desktop resolution and doesn't put it back. I think I can probably fix this with a clever shell script, though.

Are you running in OpenGL mode?  Have you read this guide? 
[http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

It has some things that boosted my performance because I pretty much had the same problems as you...

---

### Post by Filipek on 2007-06-13
> **gantww said:**
> I downloaded the patches manually. Seems to be working. It's close, but I still have a couple of issues:
1) Video is choppy. The intro video only plays on part of the screen. Movement is choppy in-game.
2) Can't change video settings. The game just locks up. It's stuck on 1024x768, which it wouldn't even do on windows. I had it at 800x600 there.
3) It alters my desktop resolution and doesn't put it back. I think I can probably fix this with a clever shell script, though.

For those who don't know the locations of patches for manual download, here is the superb WoWWiki.com page that summarize them.

[http://www.wowwiki.com/Patch_mirrors]("http://www.wowwiki.com/Patch_mirrors")

---

### Post by gantww on 2007-06-13
Hmm. It's running now, with reasonable performance, except for the following:
1) Can't adjust the gamma, so the screen is very dark. Any idea how to tweak the config to make that happen?
2) Game crashed with the following error after a few minutes.

Error #132 fatal exception

It's an access violation of some sort. No idea how to fix it though.

---

### Post by sonicborg on 2007-06-14
mine freezes as soon as it logs in, and tries to draw my char on screen, it loads the scene, and the NPC at the start, but my char stays as ghost and almost instantly just freezes

---

### Post by gantww on 2007-06-15
Here's my config. Does your character stay invisible or are you actually a ghost? You might try the settings like I have for ffxDeath and gxAPI. Also, did you do the little registry hack thing where you set the disabled modes to improve performance? Finally, are you having any sound issues - I found out the hard way that soundcards can cause problems with WOW too. You may need to run winecfg and make sure you are using the ALSA mixer.

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Korgath"
SET gameTip "8"
SET timingTestError "0"
SET mouseSpeed "0.94999998807907"
SET Gamma "1.000000"
SET profanityFilter "0"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET AmbienceVolume "0.60000002384186"
SET ffxDeath "0"
SET gxApi "OpenGL"

---

