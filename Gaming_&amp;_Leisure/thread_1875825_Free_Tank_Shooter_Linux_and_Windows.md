---
title: "Free Tank Shooter Linux and Windows"
date: 2011-11-05
forum: Gaming &amp; Leisure
---

### Post by PaulInBHC on 2011-11-05
Spotted this today. Arcade type modern tank shooter, single and multi player. Video and screens at site. Low sys reqs.

[http://www.tankatwar.com/](http://www.tankatwar.com/)

---

### Post by Matti L on 2011-11-05
Here's another free tank game:
[URL="http://worldoftanks.com/"]World of Tanks
[/URL]

And instructions for Linux:
[WoT under Linux]("http://forum.worldoftanks.com/index.php?/topic/7289-wot-under-linux/")

---

### Post by TheCheggs on 2011-11-06
very nice find guys. i am gonna have to check these out :)

---

### Post by sffvba[e0rt on 2011-11-06
> **Matti L said:**
> Here's another free tank game:
[URL="http://worldoftanks.com/"]World of Tanks
[/URL]

And instructions for Linux:
[WoT under Linux]("http://forum.worldoftanks.com/index.php?/topic/7289-wot-under-linux/")

Cool, was not aware WoT can run under Linux.


404

---

### Post by PaulInBHC on 2011-11-08
Anybody get tankatwar to install?

---

### Post by Perfect Storm on 2011-11-09
> **PaulInBHC said:**
> Anybody get tankatwar to install?

It doesn't need to be installed. Extract the package, go into the folder and double-click on start_client.sh
Click either 'run in terminal' or 'run'.

If you're running 64-bit System make sure to install ia32-libs

---

### Post by PaulInBHC on 2011-11-09
Thanks. I'm 32 bit and downloaded the only file that was shown. The Windows version works on XP. I extracted the zip to its own folder in my home folder. I tried the run last night and just now the run in terminal. Both just make the desktop wiggle for a second and nothing else happens.

---

### Post by Perfect Storm on 2011-11-09
Open the terminal and drag start_client.sh into it, hit <enter>

Please post the output.

---

### Post by PaulInBHC on 2011-11-09
I ctrl alt t to get a terminal, open the folder, drag the file and release. It now shows the location and file in the terminal. I press enter, the popup asks if I want to open, run, run in terminal, I click run in terminal, and what looks like a terminal flashes twice and that is all. Nothing is showing in the launcher. This is with 11.10 and unity.

---

### Post by PaulInBHC on 2011-11-09
I closed the folder window, pressed enter in the terminal, clicked run instead and got this

```



```

I can't figure out how to copy and paste from terminal. sigh

---

### Post by Perfect Storm on 2011-11-09
Press <alt>+<F2>

Type:
```
gnome-terminal
```

Drag the start_client.sh into terminal, press enter <enter>.
When the client closes, you can mark the output with the mouse (drag the mouse key on text while holding the left-click mouse button), then right click and choose copy.

---

### Post by PaulInBHC on 2011-11-09
I didn't know about the right click. Thanks a bunch.

```
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_1/tank_turret.b3d
read ChunkTEXS
read Texture: camouflage_0.png
Flags: 1
Blend: 2
read Texture: normal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: Material::camouflage
Blend: 1
FX: 0
Layer: 0
using texture: camouflage_0.png
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: barrel_exit
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_1/tank_barrel.b3d
read ChunkTEXS
read Texture: camouflage_0.png
Flags: 1
Blend: 2
read Texture: normal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: Material::merkava
Blend: 1
FX: 0
Layer: 0
using texture: camouflage_0.png
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: barrel_mount
read ChunkBONE
read ChunkNODE: secondary_weapon_mount
read ChunkBONE
read ChunkNODE: camera
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_2/tank_turret.b3d
read ChunkTEXS
read Texture: camouflage_0.png
Flags: 1
Blend: 2
read Texture: normal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: Material::merkava
Blend: 1
FX: 0
Layer: 0
using texture: camouflage_0.png
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: barrel_exit
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_2/tank_barrel.b3d
read ChunkTEXS
read Texture: metal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: BlackGun
Blend: 1
FX: 0
Layer: 0
using texture: metal.png
read Material: wire_198224087
Blend: 1
FX: 0
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/models/tank_parts_0/metal.png
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: weapon_end
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_0/secondary_weapon.b3d
read ChunkTEXS
read Texture: metal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: BlackGun
Blend: 1
FX: 0
Layer: 0
using texture: metal.png
read Material: wire_198224087
Blend: 1
FX: 0
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/models/tank_parts_1/metal.png
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: weapon_end
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_1/secondary_weapon.b3d
read ChunkTEXS
read Texture: metal.png
Flags: 1
Blend: 2
read ChunkBRUS
read Material: BlackGun
Blend: 1
FX: 0
Layer: 0
using texture: metal.png
read Material: wire_198224087
Blend: 1
FX: 0
read ChunkNODE: Skeleton
read ChunkMESH
read ChunkVRTS
read ChunkTRIS
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/models/tank_parts_2/metal.png
read ChunkANIM
Unknown chunk found in node chunk - skipping
read ChunkNODE: weapon_end
read ChunkBONE
Loaded mesh: ./media/models/tank_parts_2/secondary_weapon.b3d
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_next.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_previous.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_up.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_down.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_camouflage0.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_camouflage1.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_camouflage2.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_camouflage3.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/btn_camouflage4.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/menu/customise_your_tank.png
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
Loaded texture: /home/paulm/TANK@WAR-1.1.1-linux/media/textures/cursor.png
irrKlang sound library version 1.3.0
Loaded plugin: ikpMP3.so
Loaded plugin: ikpFlac.so
Could not load libasound.so
Segmentation fault

```

I have an ATI HD5670 1gig running whatever the default driver is.

---

### Post by Perfect Storm on 2011-11-09
> ```
From call : X_GetGeometry
X Error: BadDrawable (invalid Pixmap or Window parameter)
From call : X_GetGeometry
GL_OUT_OF_MEMORY
Could not glTexImage2D
```

I have an ATI HD5670 1gig running whatever the default driver is.

That may be the problem, check if there's a driver available in 'additional drivers', you need restricted drivers.
Check and see if your card support restricted drivers.

---

### Post by PaulInBHC on 2011-11-10
That fixed it.

I assumed that since unity was working in 3d and Warzone 2100 seemed ok that the driver was good.

---

### Post by Perfect Storm on 2011-11-10
> **PaulInBHC said:**
> That fixed it.

I assumed that since unity was working in 3d and Warzone 2100 seemed ok that the driver was good.

The Open driver both for Nvidia and ATI works well with 3D Desktop effects etc, but when it come to games you can't go wrong with the restricted drivers.

---

### Post by Dlambert on 2011-11-12
Zero Ballistics is also good!

---

### Post by mastablasta on 2011-11-14
aha seems good will give it a try, but probably is not as good as World of Tanks. from screenshots this one seem a bit more limited.

---

