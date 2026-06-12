---
title: "Special problem with running WoW it only wants to run at 3360x1050"
date: 2007-06-26
forum: Gaming &amp; Leisure
---

### Post by Gizim on 2007-06-26
Ive changed it in the Config.wtf file but it will only run at that res which is the size of my duel 22inch monitor setup... any ideas?

---

### Post by Falcorian on 2007-09-15
Well, I know it's late, but maybe someone else will find it helpful. Here's my Config.wtf, I have 2 monitors, but this keeps it on one (windowed):

```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET gxWindow "1"
SET shadowLevel "0"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET mouseSpeed "1"
SET Gamma "0.900000"
SET showToolsUI "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.43999999761581"
SET patchlist "us.version.worldofwarcraft.com"
SET weatherDensity "3"
SET realmName "Kil'jaeden"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET gameTip "12"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET SoundNumChannels "128"
SET EnableSoundWhenGameIsInBG "1"
SET SoundZoneMusicNoDelay "1"
SET DesktopGamma "1"
SET checkAddonVersion "0"
SET profanityFilter "0"
SET autoSelfCast "1"
SET minimapInsideZoom "1"
SET timingTestError "0"
SET minimapZoom "4"
SET lastCharacterIndex "1"
SET gxApi "opengl"
SET gxCursor "0"

```

The file is also not writable, because it kept rewriting it as 3360x1050 when I let it do so.

---

