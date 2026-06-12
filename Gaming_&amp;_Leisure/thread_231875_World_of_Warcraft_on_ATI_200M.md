---
title: "World of Warcraft on ATI 200M?"
date: 2006-08-07
forum: Gaming &amp; Leisure
---

### Post by snowpalmer on 2006-08-07
I have been trying to get World of Warcraft working well on my laptop for about a month now with little success. I don't have any problems installing or getting into the game. The problem that I find is that it is very very slow. About 1/3 of what I can do in windows on the same machine. Is this expected? I thought people here had WoW working in wine with comparable speeds?

**My Machine**
Compaq R4000
Ati Xpress 200M 128Meg Sideport (used with 128 shared ram using the 8.24.8 drivers)
1.25 Gigs of ram
4200 60 Gig hard drive.

**Software**
Ubuntu Dapper 6.06
Wine 0.9.18 (I have tried the patched 0.9.17 as well.)

The only thing I have under windows now is WoW and I'd like to remove it if possible.  Any ideas?  Is this expected?

Snowpalmer

---

### Post by sgtBiafra on 2006-08-08
Perhaps you are attempting to run it in Direct3d mode. Have you tried starting the game like so?

"wine WoW.exe -opengl"

You might also be running sound without hitching it into something native to Linux (i.e. OSS or ALSA). You should do a search here for "warcraft" as well as on the Ubuntu Wiki. A lot of folks have done some good research on this.

---

### Post by snowpalmer on 2006-08-08
> **sgtBiafra said:**
> 
"wine WoW.exe -opengl"


The opengl mode works much worse than Direct3D. The mouse is really really choppy and the FPS is about the same.

> **sgtBiafra said:**
> 
You might also be running sound without hitching it into something native to Linux (i.e. OSS or ALSA). You should do a search here for "warcraft" as well as on the Ubuntu Wiki. A lot of folks have done some good research on this.

I have tried several different ways with the sound, ALSA, OSS, No Sound, nice -n 19. Sound doesn't seem to be the reason why it's slow.  I have read through pages and pages of posts here along with the information that is written on the wiki about it. Most of the information seems to relate to just getting it installed and working, which I don't have a problem with.

---

### Post by snowpalmer on 2006-08-08
Just for some more information. My 3D seems to be working just fine. Other than the fact that Warcraft III (wine) and Quake 3 (native) work fine here are some other tests.

glxgears
```
8303 frames in 5.0 seconds = 1660.490 FPS
8304 frames in 5.0 seconds = 1660.788 FPS
8304 frames in 5.0 seconds = 1660.689 FPS
8304 frames in 5.0 seconds = 1660.655 FPS
8289 frames in 5.0 seconds = 1657.657 FPS
```

fgl_glxgears
```
1366 frames in 5.0 seconds = 273.200 FPS
1355 frames in 5.0 seconds = 271.000 FPS
1353 frames in 5.0 seconds = 270.600 FPS
1361 frames in 5.0 seconds = 272.200 FPS
1363 frames in 5.0 seconds = 272.600 FPS
```

Quake 3
```
timedemo 1
demo four
---
result: 126 fps
```

glxinfo | grep rendering
```
direct rendering: Yes

```

---

### Post by dantum on 2006-09-19
Hi, I too have a similar spec laptop with 200M card. The card seems to work fine and the latest drivers have improved and solved some previous issues. But the game crashes the moment i get into the world.

I have latest wine build from source and i tried it on a nvidia desktop i have at home. It works great. Perfomance is better than on Cedega. 

I was wondering what xorg.conf you are running and what is your wow config.wtf file looks like.

Post them here and we can compare notes.

Config.wtf

SET gxApi "opengl"
SET anisotropic "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET movie "0"
SET hwDetect "0"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET farclip "350.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET readTOS "1"
SET readEULA "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET doodadAnim "0"
SET lastCharacterIndex "2"
SET MusicVolume "0"
SET SoundVolume "0"
SET SoundOutputSystem "7"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET EnableMusic "0"
SET realmName "Aszune"
SET gameTip "23"
SET AmbienceVolume "0.60000002384186"
SET gxCursor "0"
SET spellEffectLevel "0"
SET M2UseShaders "0"
SET Gamma "1.000000"
SET weatherDensity "0"
SET useWeatherShaders "0"
SET ffx "0"
SET ffxDeath "0"
SET ffxGlow "0"
SET uiScale "1"
SET readScanning "-1"
SET readContest "-1"
SET gxWindow "1"
SET fullAlpha "1"
SET trilinear "1"
SET frillDensity "12"
SET MasterSoundEffects "0"


xorg.conf:

Section "Device"

#       Driver      "ati"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:5:0"

---

### Post by gabrielsaldana on 2006-10-17
Dude! Your Config.wtf worked like a charm for me. I have the patched Wine 0.9.22 and have the same card ATI Radeon Xpress 200m and in my xorg.conf i have this:

```

Section "Device"
    Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
    Driver      "fglrx"
    Option        "ForceMonitors" "lvds,crt1"
    Option        "DesktopSetup" "clone"
    BusID       "PCI:1:5:0"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "no_accel" "no"
Option "no_dri" "no"
Option "DynamicClocks" "on"
Option "mtrr" "on"
Option "DesktopSetup" "Single"
Option "ScreenOverlap" "0"
Option "Capabilities" "0x00000000"
Option "CapabilitiesEx" "0x00000000"
Option "CenterMode" "off"
Option "PseudoColorVisuals" "off"
   Option  "Stereo" "off"
   Option  "StereoSyncEnable" "1"
   Option  "FSAAEnable" "no"
   Option  "FSAAScale" "1"
   Option  "FSAADisableGamma" "no"
   Option  "FSAACustomizeMSPos" "no"
   Option  "FSAAMSPosX0" "0.000000"
   Option  "FSAAMSPosY0" "0.000000"
   Option  "FSAAMSPosX1" "0.000000"
   Option  "FSAAMSPosY1" "0.000000"
   Option  "FSAAMSPosX2" "0.000000"
   Option  "FSAAMSPosY2" "0.000000"
   Option  "FSAAMSPosX3" "0.000000"
   Option  "FSAAMSPosY3" "0.000000"
   Option  "FSAAMSPosX4" "0.000000"
   Option  "FSAAMSPosY4" "0.000000"
   Option  "FSAAMSPosX5" "0.000000"
   Option  "FSAAMSPosY5" "0.000000"
   Option  "UseFastTLS" "0"
   Option  "BlockSignalsOnLock" "on"
   Option  "UseInternalAGPGART" "no"
   Option  "ForceGenericCPU" "no"
   Option  "KernelModuleParm" "agplock=0"
   Option  "PowerState" "1"
   Option  "RenderAccel" "false"
   Option  "backingstore" "true"
   Option  "AllowGLXWithComposite" "true" 
EndSection

```

Using fglrx 8.29.6

I havent tested entering the world because Im at school behind a firewall, but I'll post the results tonight.

Before I had trouble with the -opengl option, running on -d3d with the image displaced and a black square at the top, and then it froze while playing. 

I hope this time I can play and ditch windows forever.

---

### Post by Juzz on 2006-10-19
So what's the verdict?

Does it work properly - or?

---

### Post by Juzz on 2006-10-19
To fix game crash on load:

```
SET mapShadows "0"
```

---

### Post by gabrielsaldana on 2006-10-27
Yes, it works with that config file. A little slow, but that might be the driver's fault. But its playable :)

---

### Post by snowpalmer on 2006-12-14
> **gabrielsaldana said:**
> Yes, it works with that config file. A little slow, but that might be the driver's fault. But its playable :)

Glad to hear it worked for you.  I just tried it today.  Used the config file as well as what you had in your xorg.conf.  It started up and almost looked like it was going to play (about 4-6 fps) but then hard locked.

What kind of system do you have?

---

### Post by gabrielsaldana on 2007-01-10
> **snowpalmer said:**
> Glad to hear it worked for you.  I just tried it today.  Used the config file as well as what you had in your xorg.conf.  It started up and almost looked like it was going to play (about 4-6 fps) but then hard locked.

What kind of system do you have?

I have a Gateway MX6450 laptop with ATI Radeon Xpress 200m, AMD Turion 64 running 32bit Ubuntu Edgy.

Now I upgraded my driver to the 8.32.5 and it still works. A bit slow, but playable.

I'm going to look for some Wine tweaks I saw the other day for ATI cards

---

### Post by Sammi on 2007-01-10
Are you still using an old version of Wine? The newest one(0.9.28 ) works fine  out-of-the-box for most when running WoW.

---

