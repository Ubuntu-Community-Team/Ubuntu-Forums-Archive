---
title: "Compiling BlobWars: Strange SDL error"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by Lego Dragon Rider on 2008-02-03
When I compile the latest BlobWars:MetalBlobSolid using make, I get most of the way through, but when it gets to creating the executable, I get an error the the SDL/libpng libraries: 
```

<...>
g++ `sdl-config --libs` -lSDL_mixer -lSDL_image -lSDL_ttf -lz
 aquaBoss.o bosses.o bullets.o cutscene.o CAudio.o CBoss.o CCollision.o CCutscene.o CData.o CEffect.o
 CEngine.o CEntity.o CFileData.o CGame.o  CGameData.o CGameObject.o CGraphics.o CHub.o CKeyboard.o
 CJoystick.o CLineDef.o CList.o  CMap.o CMath.o CObjective.o CPak.o CParticle.o CPersistant.o
 CPersistData.o CRadarBlip.o CSpawnPoint.o CSprite.o CSwitch.o CTeleporter.o CTrain.o CTrap.o CWeapon.o
 CWidget.o droidBoss.o effects.o enemies.o entities.o explosions.o finalBattle.o galdov.o game.o graphics.o
  hub.o info.o init.o intro.o items.o lineDefs.o loadSave.o map.o mapData.o mias.o  mission.o objectives.o
 obstacles.o options.o particles.o player.o resources.o spawnPoints.o switches.o tankBoss.o teleporters.o title.o
 trains.o traps.o triggers.o weapons.o widgets.o main.o -o blobwars

/usr/lib/libSDL_image.so: undefined reference to `png_read_info@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_tRNS@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_packing@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_read_update_info@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_create_read_struct@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_read_image@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_gray_to_rgb@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_IHDR@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_strip_16@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_expand@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_io_ptr@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_destroy_read_struct@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_read_fn@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_create_info_struct@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_sig_cmp@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_valid@PNG12_0'
collect2: ld returned 1 exit status
make: *** [blobwars] Error 1

```I tried reinstalling all of my SDL libs ( especially the dev ones ), but it says they are already the latest version. The same happens with libpng. What am I doing wrong/not doing? ( And is this the wrong place? ) Thanks.

---

### Post by Perfect Storm on 2008-02-03
How's your ./configure looks like?

---

### Post by Perfect Storm on 2008-02-03
Okay I took a look. Delete the folder and start a new;

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev


cd ~/Desktop
tar zxfv blobwars-1.08-1.tar.gz
cd blobwars-1.08
make 
sudo checkinstall
blobwars
```

---

### Post by Lego Dragon Rider on 2008-02-03
> **Artificial Intelligence said:**
> How's your ./configure looks like?

There's not a configure file. :? Do I need to create one?

I followed your instructions, but I still get the same error when I type "make".


---

### Post by Perfect Storm on 2008-02-03
Which version of Ubuntu do you have?

---

### Post by Lego Dragon Rider on 2008-02-03
7.10 Gutsy. I'm starting to regret upgrading from Edgy...

---

### Post by Lego Dragon Rider on 2008-02-03
Solved my problem! :D The reason I was getting an error is because I had installed the MONO .NET framework. The compiler was accessing the MONO version of libpng instead of the system one. I uninstalled MONO and not the compile works just fine! Yay! :D

---

