---
title: "Help, low framerate with WoW and WIne"
date: 2007-06-19
forum: Gaming &amp; Leisure
---

### Post by Beattech on 2007-06-19
Hello, 
      In an effort to further concrete my switch from windows, I am trying to get WoW working on Ubuntu Feisty. Though when I go into the game, I get a frame rate of 2-30FPS (avg is usually below 10) Even with the graphic settings i still only manage a frame rate of 12 (avg). Needless to say, this isn't fast enough to honestly play. I have entered the Key in Regedit, and made sure it was correct and case sensitive. I have downloaded the addon that allows me to edit the video settings in game, as well as disabled all other addons. I open it with the -opengl. I have the latest Nvidia drivers (probably from Envy). Using latest wine (from the repositories). Only other program open was Mozilla Firefox (one window, 2 or 3 tabs). 

Computer specs:
HP Pavilion A822n
Amd Athalon 64 3400+
1g Ram
256MB Ge Force 6600 AGP 8X
200Gb HDD
5.1 Surround sound speakers
    (through on-board sound card)
Fiber Optic Internet (15MB/s DL/ 2MB/s UP) (is that T1?)

Partitions:
Windows XP Recovery (Fat32
Windows XP home editition (NTFS (or whatever))
Shared Partition (Fat32)
Ubuntu Fiesty 7.04 x86 (Logical)
Linux Swap (Logical)


Copied complete "World of Warcraft" folder from old Windows partition to Fat 32 partition (could that be the problem? Or that its not on the same partition as my Home folder) 

I don't know exactly what else I should include for you guys to troubleshoot meh with.. so heres what I can think off.

Here is my config.wtf File 
(settings on high, but have tried on the lowest possible without changing Resolution)
```
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x720"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "537"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTOS "1"
SET soundMaxHardwareChannels "12"
SET soundSoftwareChannels "128"
SET locale "enUS"
SET gxMultisampleQuality "0.000000"
SET Gamma "0.800000"
SET readEULA "1"
SET MusicVolume "1"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmName "Smolderthorn"
SET gameTip "77"
SET AmbienceVolume "0"
SET uiScale "0.70999997854233"
SET mouseSpeed "1.2000000476837"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET ShowTargetCastbar "1"
SET statusBarText "1"
SET minimapZoom "0"
SET ffxGlow "0"
SET profanityFilter "0"
SET ChatBubblesParty "1"
SET minimapInsideZoom "0"
SET useUiScale "1"
SET EnableSoundWhenGameIsInBG "1"
SET readScanning "-1"
SET readContest "-1"
SET SoundNumChannels "128"
SET SoundZoneMusicNoDelay "1"
SET spamFilter "0"
SET cameraView "3"
SET expansionMovie "0"
SET ShowVKeyCastbar "1"
SET checkAddonVersion "0"
SET EnableErrorSpeech "0"
SET patchlist "us.version.worldofwarcraft.com"
SET EnableAmbience "0"
SET accountName "shpickyguitarguy"
SET showToolsUI "1"
SET autoDismountFlying "1"
SET gxApi "opengl"
SET gxMultisample "1"
SET ffxDeath "0"
SET shadowLOD "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET doodadAnim "0"
SET gxCursor "0"
SET lod "1"
SET weatherDensity "3"
SET timingTestError "3"
SET shadowLevel "0"
SET trilinear "1"
SET frillDensity "48"
SET anisotropic "8"
SET SoundUseHardware "0"
SET ffx "0"
```

I would like to try putting it on another xserver (ctrl+alt+#) but cant figure out how. 
I know that my computer (while not THAT great) can do better, and on windows I could get a FR of 40-50. Nothing else is wrong (such as; mouse, tearing, glitching, or any other graphical issues), it just has an impossibly slow FPS. (I actually think the game's graphics in general look ALOT sharper, clearer, and just plain better on linux than windows for some reason. IMO....)
The launcher and login screens are fine, and I installed the Gekko thing for the launcher. 

Please, help!

---

