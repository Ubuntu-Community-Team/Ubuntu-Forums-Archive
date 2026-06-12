---
title: "WoW, Wine"
date: 2005-10-09
forum: Gaming &amp; Leisure
---

### Post by nerdman on 2005-10-09
World of warcraft.

when I run it "wine WoW.exe -openGL"... "cannot start 3D acceleration".
when I run it "wine WoW.exe" ... gives me the error sending program.

...is Cedega a better choice?

I have the World of Warcraft folder from when I installed it on an actual windows system, so I figured I should be good off. is this an openGL issue then?

---

### Post by seethru on 2005-10-10
can you post your Config.WTF for me? it's located in your WoW folder, under WTF.

---

### Post by nerdman on 2005-10-10
```
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "477"
SET particleDensity "1.000000"
SET movie "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET realmName "Blackhand"
SET readTOS "1"
SET readEULA "1"
SET profanityFilter "0"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET EnableMusic "0"
SET cameraPitchMoveSpeed "135"
SET cameraYawMoveSpeed "270"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceLast "16.447069"
SET cameraPitchLast "-39.724995"
SET cameraDistanceMaxFactor "2"
SET AmbienceVolume "0.60000002384186"
SET EnableAmbience "0"
SET minimapZoom "0"
SET uiScale "1"
SET useUiScale "1"
SET guildMemberNotify "1"
SET minimapInsideZoom "0"
SET cameraWaterCollision "0"
SET ChatBubblesParty "1"
SET statusBarText "1"
SET accountName "I'mnotgoingtopostthisonpublicforums"
SET trilinear "1"
SET frillDensity "32"
SET specular "1"
SET pixelShaders "1"
SET unitDrawDist "300.000000"
SET checkAddonVersion "0"
SET gxWindow "1" 
```

Now I **am** getting the error window... I thought that was good sign as its actually running just not working >.o Are there drivers I would need? *shivers*

---

### Post by KingBahamut on 2005-10-10
Nerdman , are you using a properly accelerated Video card? and if so, what type and what driver are you using?

---

### Post by nerdman on 2005-10-10
I got my nVidia drivers all up to date, using the HOWTO in the forum a bit under this one, mere minutes ago >.o

...I'm thinking Cedega is a bit more easily implemented?

---

### Post by KingBahamut on 2005-10-10
Cedega, DirectXWine, and cvscedega are yes....a little easier implemented. I use factory developed Cedega, but the others have thier merits too.

---

### Post by nerdman on 2005-10-10
I cannot apt-get or search in synaptic for any of the three things there... Would you know which repository they are on? :smile:

---

### Post by KingBahamut on 2005-10-10
**cedega** - [http://www.transgaming.com](http://www.transgaming.com) - pay site, but worth it. 

**cvscedega and directXwine ** -
[http://directxwine.sourceforge.net/](http://directxwine.sourceforge.net/)
[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

---

### Post by seethru on 2005-10-10
does glxgears work? and if it does, what kind of performance are you getting from it? If glxgears doesn't work, it's quite likely you don't have 3D acceleration setup correctly.

---

### Post by nerdman on 2005-10-10
glxgears....

again, I find my list of repositories anything but complete... apt-get For the lose? sigh~

---

### Post by nerdman on 2005-10-10
[QUOTE=KingBahamut]**cedega** - [http://www.transgaming.com](http://www.transgaming.com) - pay site, but worth it. 

**cvscedega and directXwine ** -
[http://directxwine.sourceforge.net/](http://directxwine.sourceforge.net/)
[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)[/QUOTE]

o.o;; I thought Linux was supposed to be free

---

### Post by seethru on 2005-10-10
Linux is, but those guys at TG have to pay their programmers. What they do is amazing.

---

