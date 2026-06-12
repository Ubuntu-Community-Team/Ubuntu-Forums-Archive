---
title: "Doom 3 Problems."
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by [Mikolan] on 2007-06-15
So yesterday I felt like playing som FPS. And of course I wanted to play ID Software's games, since they have native linux support :)

But I'm having some trouble getting Doom 3 to work.

Installation went fine, and I copied over the .pk4 files and verified their md5sums.

But when I try to start a new game I get the following errors:
```
   1.
      --------- Map Initialization ---------
   2.
      Map: game/mars_city1
   3.
      glprogs/heatHaze.vfp
   4.
      glprogs/heatHaze.vfp
   5.
      glprogs/heatHazeWithMask.vfp
   6.
      glprogs/heatHazeWithMask.vfp
   7.
      ----------- Game Map Init ------------
   8.
      collision data:
   9.
         421 models
  10.
       30823 vertices (722 KB)
  11.
       54551 edges (1917 KB)
  12.
       22257 polygons (1564 KB)
  13.
        4068 brushes (556 KB)
  14.
       12449 nodes (340 KB)
  15.
       43444 polygon refs (339 KB)
  16.
       14219 brush refs (111 KB)
  17.
       18352 internal edges
  18.
        1461 sharp edges
  19.
           0 contained polygons removed
  20.
           0 polygons merged
  21.
        5551 KB total memory used
  22.
      259 msec to load collision data.
  23.
      map bounds are (19640.0, 22168.0, 29496.0)
  24.
      max clip sector is (1227.5, 1385.5, 1843.5)
  25.
          2 KB passage memory used to build PVS
  26.
          3 msec to calculate PVS
  27.
         56 areas
  28.
        110 portals
  29.
          9 areas visible on average
  30.
        448 bytes PVS data
  31.
      [Load AAS]
  32.
      loading maps/game/mars_city1.aas48
  33.
      done.
  34.
      [Load AAS]
  35.
      loading maps/game/mars_city1.aas96
  36.
      [Load AAS]
  37.
      loading maps/game/mars_city1.aas_guardian
  38.
      [Load AAS]
  39.
      loading maps/game/mars_city1.aas_mancubus
  40.
      [Load AAS]
  41.
      loading maps/game/mars_city1.aas_sabaoth
  42.
      [Load AAS]
  43.
      loading maps/game/mars_city1.aas_cyberdemon
  44.
      Entering doom_main()
  45.
      Exiting doom_main()
  46.
      Spawning entities
  47.
      WARNING: Couldn't load model: 'models/mapobjects/base/misc/fireext.ase'
  48.
      loaded collision model models/mapobjects/base/misc/fireext.ase
  49.
      WARNING: Couldn't load model: 'models/mapobjects/base/chairs/chair2.ase'
  50.
      loaded collision model models/mapobjects/base/chairs/chair2.ase
  51.
      WARNING: Couldn't load model: 'models/mapobjects/com/platguistand/mc_platguistand.lwo'
  52.
      loaded collision model models/mapobjects/com/platguistand/mc_platguistand.lwo
  53.
      TODO: Sys_SetClipboardData
  54.
      --------- Game Map Shutdown ----------
  55.
      --------------------------------------
  56.
      ********************
  57.
      ERROR: Unable to load 'models/md5/cinematics/marscity/receptioncin1_camera_c.md5camera' on 'marscity_recep_cam_c'
  58.
      ******************** 
```

And I get booted to console.

Anyone experienced this before? Really weird problem to me, should be working fine :/

I used the doom3-linux-1.3.1.1304.x86.run installer.

---

### Post by [Mikolan] on 2007-06-15
Ok nvm this, after a reinstall to ~/doom3 instead of /usr/local/games/doom3 it now works fine :)

---

### Post by slider0 on 2008-02-15
Hello gave me the same error you could tell me the exact configuration steps and what you did because the probe above and nothing gives me the same error .:(

---

### Post by BlueKoala on 2008-02-15
He fixed it by re-installing doom3 to /home/[username]/doom3 folder and it fixed it for him. 

The error to me suggests that the files are either missing/corrupt on may not have sufficient access to them. (Read access denied maybe? )

---

