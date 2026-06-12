---
title: "Weird texture wine WoW ATI card and low FPS"
date: 2013-12-29
forum: Gaming &amp; Leisure
---

### Post by nick.arinze on 2013-12-29
Hey, So I thought I'd try out WoW on wine I installed via the Battle.net app and I'm seeing weird textures with really low fps in dungeons. Outside I'm seeing 14-15 FPS. I'm running Ubuntu 12.04 on an ATI 5450 card.

Here's my current WTF
> SET coresDetected "2" 
SET hwDetect "0" 
SET gxApi "D3D9" 
SET videoOptionsVersion "5" 
SET unitDrawDist "300.000000" 
SET textureFilteringMode "0" 
SET DesktopGamma "1" 
SET ffxGlow "0" 
SET ffxDeath "0" 
SET fullAlpha "1" 
SET lodDist "100.000000" 
SET SmallCull "0.070000" 
SET weatherDensity "0" 
SET Sound_EnableEmoteSounds "0" 
SET lod "1" 
SET ffx "0" 
SET alphaLevel "0" 
SET environmentDetail "1.5" 
SET Sound_MasterVolume "0.5" 
SET targetNearestDistance "80.000000" 
SET CombatLogRangeParty "200" 
SET CombatLogRangePartyPet "200" 
SET CombatLogRangeFriendlyPlayers "200" 
SET CombatLogRangeFriendlyPlayersPets "200" 
SET CombatLogRangeHostilePlayers "200" 
SET CombatLogRangeHostilePlayersPets "200" 
SET CombatLogRangeCreature "200" 
SET doodadAnim "0" 
SET shadowLOD "0" 
SET MaxLights "1" 
SET mapShadows "0" 
SET anisotropic "0" 
SET Gamma "1.000000" 
SET showGameTips "0" 
SET farclip "617" 
SET pixelShaders "1" 
SET scriptMemory "131072" 
SET M2Faster "0" 
SET uiScale "1" 
SET useUiScale "1" 
SET locale "enGB" 
SET installLocale "enUS" 
SET enterWorld "1" 
SET gxWindow "1" 
SET gxMaximize "0" 
SET maxAnimThreads "3" 
SET mouseSpeed "1" 
SET lastCharacterIndex "3" 
SET readTOS "1" 
SET lastReadTOS "50402" 
SET readEULA "1" 
SET lastReadEULA "50402" 
SET readTerminationWithoutNotice "1" 
SET lastReadTerminationWithoutNotice "50402" 
SET accounttype "MP" 
SET ChatMusicVolume "0.29999998211861" 
SET ChatSoundVolume "0.39999997615814" 
SET ChatAmbienceVolume "0.29999998211861" 
SET VoiceActivationSensitivity "0.39999997615814" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 


---

### Post by jeffreyjensen1989 on 2013-12-30
Wow renders openGL natively although it's not a choice in the settings. Change gxapi to ```
 SET gxApi "openGL" 
```
EDIT: Also, Once in game turn all of the graphics down as low as they go and use that as a base so you know how fast you run like that. Personally, I like to turn everything to low besides View Distance which I max and Projected Textures on as well

---

