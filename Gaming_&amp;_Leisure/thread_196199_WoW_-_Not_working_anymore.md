---
title: "WoW - Not working anymore"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by simon50508861 on 2006-06-13
Help.

I've had WoW working with Ubuntu for some time now, but as of yesterday it doesn't work at all. It get to the login screen ok and you can enter a password, but then it just hangs at the downloading screen and then goes black.

It was working before and i've made no changes to the system whatsoever (Really)

I tried to upgrade from breezy to dapper, and no difference except the mouse doesn't lag anymore on the wow login screen. Other than that the upgrade worked fine except for some texem? program not updating

Has something changed? guess i'll have to go back to windows if i cant get this working as its the only reason i went fully Ubuntu was that i can still play WoW

---

### Post by eqisow on 2006-06-13
I've heard of a few similiar problems today. I think there was some kind of hardware survey after today's maintenance that borked things up. I got mine working by running it in Cedega once and then going back to Wine.

I'm not sure what to tell you, except that you could try replacing your config files with mine and see if it skips the hardware surbey. The config files should be located in the WTF folder of your World of Warcraft directory.

RunOnce.wtf:
```
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET checkAddonVersion "1"

```

Config.wtf:
```
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET frillDensity "32"
SET farclip "477"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET SoundBufferSize "100"
SET gxMultisampleQuality "0.000000"
SET readScanning "-1"
SET readContest "-1"
SET realmName "Stonemaul"
SET gameTip "27"
SET gxCursor "0"
SET Gamma "0.700000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET useUiScale "1"
SET gxRefresh "85"
SET gxVSync "0"
SET spellEffectLevel "0"
SET mouseSpeed "1"
SET scriptMemory "32768"
SET profanityFilter "0"
SET weatherDensity "1"
SET ffx "0"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET EnableErrorSpeech "0"
SET minimapInsideZoom "0"
SET lod "0"
SET shadowLevel "0"
SET alphaLevel "0"
SET checkAddonVersion "0"
```

Hope this works for you. If not, perhaps you should let Blizzard know that you hate stupid intrusive non-optional hardware surveys. :(

---

### Post by NinjitsuStylee on 2006-06-13
Hi guys.  Ooh, a fresh thread.

I just upgraded from breezy to dapper too.  However my WoW still works.

Wanna know my secret?  

I have a specially compiled "version" of WINE just for WoW.  It's not really a necessary thing...I just got lazy and didn't want to recompile.

What's all this compile business?  Well, my guess is that simon50508861 installed WINE using synaptic (am I right?).

I don't know about the synaptic install for WoW.  The main reason is because you need to apply a special patch to your WINE install in order to get certain things to work right in WoW.  The best way to get WoW to run on Ubuntu is to compile from source by following the guide over on their appdb exactly.  

Also, before you do this, make sure you've got the drivers for your graphics card properly installed (ie if you're using nvidia, install the nvidia packages from synaptic and change the device in your xorg.conf to "nvidia" instead of "nv"....there are guides to do this).

After that just follow the directions on the link.
([http://appdb.winehq.org]("http://appdb.winehq.org") and search for World of Warcraft...note, as of this posting, winehq was down...will update as soon as I can get the link)

One thing to note:  If after starting up you notice some crazy spastic screen flickering, let me know.  There's a certain OpenGL file you have to modify before you compile.  I can't quite remember which one it is but if anyone really needs to know, I can dig through my files and find out. 

Good luck!

---

### Post by eqisow on 2006-06-13
I don't think that's the problem, as Wine was running fine before. But, just for future reference, compiling is unnecessary. There's an up-to-date version of Wine with the WoW patch on the [Wine wiki]("https://wiki.ubuntu.com/Wine").

---

### Post by simon50508861 on 2006-06-13
Cool, im not the only one to have this problem. I'm not alone!

Actually i used a source based version of Wine as per doco in the ubuntu forums somewhere. 0.9.13. I also applied some mouse patch because i couldn't get the mouse to work at first with the apt-get version (or synaptic). Having said that if i needed to upgrade wine to some later version to fix this issue i would probably be lost as the mouse patch would probably be different again i guess

I currently use an nVidia card and have a script that loads the nVidia config first as WoW was always too dark without it on my monitor. At least this happened on maintenance day and i didnt have too much withdrawal symptons

I will try to modify the configs as per eqisow suggestions and see how i go.

---

### Post by eqisow on 2006-06-13
If that doesn't work, try installing 0.9.15 via the [Wine wiki]("https://wiki.ubuntu.com/Wine"). Follow the directions under the "Latest version of Wine with WoW Patch" section. No compiling necessary!

---

### Post by sgtBiafra on 2006-06-13
I found a way around this. Blizzard suggested playing with the file permissions to the Survey.mpq file in the WDB but that didn't do it. So I took things to the next level.

I deleted the Survey.mpq and made the WDB folder read-only for span of the login process. Since it could not download the survey file to populate and send back it zipped by and let me into the game.

If Blizzard wants to know my system specs I'll tell them this much... Ubuntu.

---

### Post by eqisow on 2006-06-13
This works perfectly for me. Good job. :)

Edit: Unfortunately, it seems that after running once, you still cna't change the file permissions back. The folder has to stay read only. Hopefully this won't cause problems down the road.

---

### Post by eqisow on 2006-06-13
Updated the [World of Warcraft wiki]("https://wiki.ubuntu.com/WorldofWarcraft") to reflect the new problem, and the solution.

---

### Post by sgtBiafra on 2006-06-14
For now, I'm afraid we're stuck with this inconvenient workaround. Do note though that there are several threads in the WoW Tech Support forum concerning problems between the survey and firewalls. Perhaps they will redesign this and remove this hassle.

---

### Post by Tnarg on 2006-06-14
Just for refrence, last night when I went to bed WoW was having the same proble, hanging on the downloading screen, but when I got home from work today everything worked fine:D , first go, no problems. Got no idea what has happened. Any ideas?

---

### Post by simon50508861 on 2006-06-14
Well the WDB folder security and delete/rename file fix worked for me. Thanks heaps. I can now get back to satisfying my addiction once more.

/ty

---

### Post by spitball on 2006-06-14
[QUOTE=Tnarg]Just for refrence, last night when I went to bed WoW was having the same proble, hanging on the downloading screen, but when I got home from work today everything worked fine:D , first go, no problems. Got no idea what has happened. Any ideas?[/QUOTE]

I think the WoW servers were down for some unscheduled maintenance.

---

