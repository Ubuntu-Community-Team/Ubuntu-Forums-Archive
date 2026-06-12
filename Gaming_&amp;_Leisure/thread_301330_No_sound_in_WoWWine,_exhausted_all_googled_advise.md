---
title: "No sound in WoW/Wine, exhausted all googled advise"
date: 2006-11-16
forum: Gaming &amp; Leisure
---

### Post by montag451 on 2006-11-16
World of Warcraft is running without sound on Wine 0.9.6. I've gone through a lot of published advice but can't find a solution.

I'm relatively new to Linux, but I've managed to find a lot of information on my problem, yet none of it has fixed it. I'm currently trying to run World of Warcraft 1.12.1 on Wine 0.9.6 according to the following guide: [http://www.ubuntuforums.org/showthread.php?t=120615](http://www.ubuntuforums.org/showthread.php?t=120615)

I'm currently running Dapper on a laptop with an ATI Radeon Mobility x1600.

After installing WoW and Wine, I found I was having some graphical problems, so I fixed these by updating fglrx and using the DisabledExtentions key in regedit. WoW still had no sound, so I attempted adding the following to Config.wtf:
[INDENT]
SET SoundOutputSystem "1"
SET SoundBufferSize "70"
SET ffxDeath "0"
SET MusicVolume "0.5"
SET SoundVolume "1"
SET MasterVolume "1"
SET gxApi "opengl"
[/INDENT]
These were all things mentioned to hopefully fix sound issues. So far it hasn't worked. I've also tried different values for SoundOutputSystem according to this guide: [http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=7183](http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=7183)

Those values were -1 (autodetect), 1 (normal), 4 (OSS) and 6 (ALSA). I also tried 0 2 just for kicks. None of these worked.

I thought it might be a Wine problem, so I ran winecfg. Clicking on the Audio tab gave me an error that I couldn't find a fix to, but I was told by a friend that it probably wasn't the source of the problem anyway.

All the research I've done on sound problems in WoW with Wine points to editing Config.wtf, so I can't find anything else to go on. If anyone has any insight, it would be greatly appreciated.

---

### Post by p3d4l on 2006-11-17
I had a problem with sound when I was running enemy territory, what I did to resolve the problem was turn ESD off. Go to System, Preferences, Sound, Then the second tab (Sound) and turn ESD off. 
         Hope this works for you.

---

### Post by Ferrat on 2006-11-17
> **montag451 said:**
> World of Warcraft is running without sound on Wine 0.9.6. I've gone through a lot of published advice but can't find a solution.

I'm relatively new to Linux, but I've managed to find a lot of information on my problem, yet none of it has fixed it. I'm currently trying to run World of Warcraft 1.12.1 on Wine 0.9.6 according to the following guide: [http://www.ubuntuforums.org/showthread.php?t=120615](http://www.ubuntuforums.org/showthread.php?t=120615)

I'm currently running Dapper on a laptop with an ATI Radeon Mobility x1600.

After installing WoW and Wine, I found I was having some graphical problems, so I fixed these by updating fglrx and using the DisabledExtentions key in regedit. WoW still had no sound, so I attempted adding the following to Config.wtf:
[INDENT]
SET SoundOutputSystem "1"
SET SoundBufferSize "70"
SET ffxDeath "0"
SET MusicVolume "0.5"
SET SoundVolume "1"
SET MasterVolume "1"
SET gxApi "opengl"
[/INDENT]
These were all things mentioned to hopefully fix sound issues. So far it hasn't worked. I've also tried different values for SoundOutputSystem according to this guide: [http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=7183](http://appdb.winehq.org/appview.php?iVersionId=5606&iTestingId=7183)

Those values were -1 (autodetect), 1 (normal), 4 (OSS) and 6 (ALSA). I also tried 0 2 just for kicks. None of these worked.

I thought it might be a Wine problem, so I ran winecfg. Clicking on the Audio tab gave me an error that I couldn't find a fix to, but I was told by a friend that it probably wasn't the source of the problem anyway.

All the research I've done on sound problems in WoW with Wine points to editing Config.wtf, so I can't find anything else to go on. If anyone has any insight, it would be greatly appreciated.

tried running with wine 0.9.24 or 0.9.25?

---

### Post by simplyw00x on 2006-11-17
> Clicking on the Audio tab gave me an error that I couldn't find a fix to, but I was told by a friend that it probably wasn't the source of the problem anyway.
It probably is. Please post the error.

---

### Post by montag451 on 2006-11-18
To note, I did try killall esd, and that didn't fix the problem.

However, I found the source of the problem. It was not the Audio tab, as I had thought. I've found that WoW only plays sound when SoundOutputSystem is set to 1. It will not play sound at all, however, when I have Quod Libet running at the same time. It also does this with VLC, but those are the only two pieces of software I've tried. Not a huge problem, it just means I can't play music while running WoW.

If I can figure out a way to get WoW to play sound without taking over ALSA, I'll post it.

**Edit:** I did try 9.25. Unfortunately, I got an error saying wine could not get 3D acceleration to work, so I reverted to 9.6. I'm considering trying 9.24 with patches, since most people seem to have success with it.

---

### Post by jammersplace on 2009-05-29
ok this is what i did just to let you know to start i copied my wow folder from my external after i formatted and went with linux so... auto started with direct3d fixed that -opengl runs smoother i do have the nvidia card so.. but for sound i checked all the sound options i could think of alsa oss jack nas esound all that hardware emulation driver emulation still nothing then i went to application and ran it as it was in xp and the sound started so don't quote me but basically messed with it till it worked.

---

### Post by Sef on 2009-05-29
Closed for Necromancing.

---

