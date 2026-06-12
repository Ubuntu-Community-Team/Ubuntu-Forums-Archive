---
title: "WoW flickering screen"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by milamber on 2006-06-12
Recently installed Ubuntu 6.06 and very pleased so far. The last thing i need now is to get my WoW working on Ubuntu so i can leave Windows behind. So far i got a long way with the guides from:

[https://wiki.ubuntu.com/WorldofWarcraft](https://wiki.ubuntu.com/WorldofWarcraft)
and
[https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

I managed to get the log in screen and char selection screen of WoW with sound and perfect graphics (i was very pleased with myself about this )

When i got to the actual game however i was (and still am) faced with a problem. The screen keeps flickering at a very annoying rate so that the game becomes unplayable. I tried to play around with the video setting some but that does not seem to help.

I think its something with my video card (nvidia Geforce 2). I installed the drivers and my 3d rendering is ok. I also tried to run the game with: wine WoW -d3d
but then i get black areas everywhere where an object is on the ground.

Does anyone have any suggestions? Else i still have to go to windows everytime to be able to play WoW :S

I also played around with my Config.wtf file. Here is how it longs now:

```


SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "85"
SET hwDetect "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET farclip "237"
SET particleDensity "0.600000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readScanning "-1"
SET readContest "-1"
SET mouseSpeed "0.55000001192093"
SET realmName "Stormreaver"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET mouseInvertPitch "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "67.5"
SET cameraYawSmoothSpeed "270"
SET cameraDistanceMaxFactor "1.5"
SET gameTip "22"
SET AmbienceVolume "0.60000002384186"
SET cameraBobbing "1"
SET cameraTerrainTilt "1"
SET minimapInsideZoom "0"
SET guildMemberNotify "1"
SET gxCursor "0"
SET Gamma "1.000000"
SET uiScale "1"
SET baseMip "1"
SET M2UseShaders "0"
SET weatherDensity "1"
SET SoundOutputSystem "1"
SET gxApi "OpenGL"
SET spellEffectLevel "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET lastCharacterIndex "1"
SET renderer "d3d"
SET gxVSync "0"
SET ffx "0"
SET SoundBufferSize "70"


```

Any help would be VERY welcome!

---

### Post by milamber on 2006-06-13
Anyone?

---

### Post by Adamant1988 on 2006-06-13
are you using an ATI card by chance?

---

### Post by milamber on 2006-06-13
hmm.. you mean like a Radeon card?

Then no i guess, i'm using a nVidia GeForce 2 graphical card with
a AMD Athlon 1800+ processor on a Asus motherboard.

I hope that answers your question...

---

### Post by sgtBiafra on 2006-06-13
I would create a backup of the Config.wtf file and pare it down to the most bare essentials. Once you've resolved your issues you'll be able to restore any of the settings in there from the in-game Options menu.

Also, check within winecfg's Display tab and see if you've enabled hardware shader support if it's available on your card.

---

### Post by eqisow on 2006-06-13
You could also try deleting the Config.wtf file altogether. WoW will simply generate a new one using default settings. I'm not really sure that this would help though.

Can you be more specific about what you mean by flickering?

Also, are you using Wine or Cedega?

---

### Post by Adamant1988 on 2006-06-13
if you're using wine this is a known bug.  Could you show some of the console output using a pastebin?  If you're getting a lot of d3d errors and such you're experiencing the same bug as I... If you're using wine you can try playing it inside of a virtual desktop, but you'll find that this changes the problem from screen flickering to perfect graphics at about 1-3 fps.   I haven't been able to find a fix on the WINE wiki.

---

### Post by milamber on 2006-06-14
hmm.. tx all for the replies :)

not home atm so i will try to delete the config.wtf file later on at home and see what it does.

I am indeed using WINE and i had hardware shader enabled.

I will also look at the errors later on and post them here.. see of there are any d3d errors there.

And by flickering i mean flashes of the whole screen at about..lets say 10 times per second. Just enough to recognize everything barely.

Sounds like Adamant1988 and I share the same problem..
Hope someone has another suggestion.. will first try the above though.

---

### Post by eqisow on 2006-06-14
Try the following:

```
rm '~/.wine/drive_c/Program Files/World of Warcraft/WDB/Survey.MPQ'
chmod 555 '~/.wine/drive_c/Program Files/World of Warcraft/WDB'
```

ALso, set 'gxVSync' in your Config.wtf to 1.

Let us know how it goes!

---

### Post by milamber on 2006-06-14
tx for your reply eqisow,

Here is what i managed to do so far:

I don't have a 'Survey.MPQ' file in my 'WDB' folder so i could not delete that file. I did the 'chmod 555' on that folder. Don't know what it was suppose to do but it gave nothing back (also no errors) just got back to the prompt, so i don't know if that is good.

Furthermore i first tried my old 'Config.wtf' file (like posted above in my first post) with 'gxVSync' set to 1 (it was set to 0). This seemed to reduce the flickering somewhat. So now the flickering begins to resemble tearing of the screen more.
So i will try some more settings for this later on.

I also tried deleting the 'Config.wtf' and let WoW make a new default one. This resulted in a black screen except the toolbars/hotbars so i guess that wasn't a success.

Will try to post my terminal error messages as soon as possible.

Tx all for your help so far!

---

### Post by NinjitsuStylee on 2006-06-14
Guys.  Listen up.

I'm using the Nvidia Ti4200 and I had WoW running nicely but I too had the flickering screen problem. 

It usually doesn't have to do with Config.wtf.

If you compiled from source, go to your source directory/dlls/opengl32 folder.

Look for a file called "wgl.c" and comment out line 591


```
 glDrawBuffer(GL_FRONT_LEFT);
``` 
Then compile wine and install just like they tell you to on the appdb website: 

[http://appdb.winehq.org/appview.php?versionId=4031]("http://appdb.winehq.org/appview.php?versionId=4031")

Good luck!

---

### Post by milamber on 2006-06-15
tx NinjitsuStylee!

Hope thats it.. I didn't compile from source so i will have to look into that... will get back to you how it went.

---

### Post by buppi on 2006-08-23
I had the same problem, the screen always flickered a lot and you could see inside things. seemed like there was not even double buffer but a single buffer in use. :) the line to comment out had moved about 100 lines down on this cvs version of wine but the fix worked anyhow, now it is playable and no bugs. Even the special characters (öäÖÄ) work (new to me.) I still wonder if there was a way to get a hardware accelerated mouse pointer somehow? it seemed to work only in d3d mode and you know how buggy that is.

---

### Post by DraeLee on 2006-10-23
GNU nano 1.3.10                           File: Config.wtf

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET accountName "draelee"
SET realmList "us.logon.worldofwarcraft.com"
SET doodadAnim "0"
SET specular "1"
SET pixelShaders "1"
SET lastCharacterIndex "1"
SET realmName "Khaz'goroth"
SET gameTip "4"
SET gxCursor "0"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET SoundOutputSystem "OSS"
SET SoundBufferSize "100"


This is my setup and I too have the flickering issue.  I also have no sound.  Idont know how to compile wine I tried to do what it said but I dont think I did it right so I might have to uninstall wine again and redo it. (or can I do it without uninstalling?

---

