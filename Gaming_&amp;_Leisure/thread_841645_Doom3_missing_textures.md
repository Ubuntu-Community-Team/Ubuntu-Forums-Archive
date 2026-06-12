---
title: "Doom3 missing textures"
date: 2008-06-26
forum: Gaming &amp; Leisure
---

### Post by grossaffe on 2008-06-26
I recently decided to install Doom3 on my ubuntu box, but I had noticed that the game was much darker than I had remembered.  after looking more carefully, i realized that there were textures just flat out missing, which accounted for the darkness.  when I open up the console, I see a bunch of errors:
```

------------- Warnings ---------------
during game/mars_city1...
WARNING: Couldn't load image: addnormals( textures/base_door/jumbodoor_local, heightmap( textures/base_door/jumbodoor_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/base_floor/stectile1quad2_local, heightmap( textures/base_floor/stectile1quad2_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_floor/stefloormat1_local, heightmap( textures/base_floor/stefloormat1_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/base_floor/stetile4_local, heightmap( textures/base_floor/stetile4_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_light/striplight2_local, heightmap( textures/base_light/striplight6break_b, 2))
WARNING: Couldn't load image: addnormals( textures/base_light/striplight3_local, heightmap( textures/base_light/striplight3break_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_trim/sfltrim3_local, heightmap( textures/base_trim/sfltrim3_bmp, 5))
WARNING: Couldn't load image: addnormals( textures/base_wall/gotendo1_local, heightmap( textures/base_wall/gotendo1_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_wall/lfwall22_local, heightmap( textures/base_wall/lfwall22_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_wall/lfwall3a_local, heightmap( textures/base_wall/lfwall3_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/base_wall/skpanelt2_local, heightmap( textures/base_wall/skpanelt2_b, 3))
WARNING: Couldn't load image: addnormals( textures/base_wall/sopanel23_local, heightmap( textures/base_wall/sopanel23_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/decals/pipecap2a_local, heightmap( textures/decals/pipecap2_bmp, 1))
WARNING: Couldn't load image: addnormals( textures/decals/pipecap4_local, heightmap( textures/decals/pipecap2_bmp, 1))
WARNING: Couldn't load image: addnormals( textures/decals/wheel_local, heightmap( textures/decals/wheel_h, 6))
WARNING: Couldn't load image: addnormals( textures/morgue/floorvent01_local, heightmap( textures/morgue/floorvent01_h, 3))
WARNING: Couldn't load image: addnormals( textures/object/bluetex4e_local, heightmap( textures/object/bluetex4ebmp, 6))
WARNING: Couldn't load image: addnormals( textures/object/gendesk1flat_local, heightmap( textures/object/gendesk1flat_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/object/hoser5_local, heightmap( textures/object/hoser5_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/object/modgobflat1_local, heightmap( textures/object/modgobflat1_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/object/modsidesbackflat_local, heightmap( textures/object/modsidesbackflat_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/object/sopbox2_local, heightmap( textures/object/sopbox2_bmp, 3))
WARNING: Couldn't load image: addnormals( textures/object/sopbox2_local, heightmap( textures/object/sopbox2_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/object/tecpipebraid1_local, heightmap( textures/object/tecpipebraid1_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/outside/outfactory_new4_local, heightmap( textures/outside/outfactory_new4_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/outside/outfactory_new5_local, heightmap( textures/outside/outfactory_new5_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/outside/outfactory_new7_local, heightmap( textures/outside/outfactory_new7_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/rock/lanrock1_local, heightmap( textures/rock/lanrock1_h, 8))
WARNING: Couldn't load image: addnormals( textures/rock/sharprock_local, heightmap( textures/rock/newdarkrock_bmp, 10))
WARNING: Couldn't load image: addnormals( textures/rock/skysand1_local, heightmap( textures/rock/skysand2_bmp, 4))
WARNING: Couldn't load image: addnormals( textures/washroom/rfceilingtile01_local, heightmap( textures/washroom/rfceilingtile01_h, 10))
WARNING: Couldn't load image: addnormals( textures/washroom/rfcorner01_local, heightmap( textures/washroom/rfcorner01_h, 5))
WARNING: Couldn't load image: addnormals( textures/washroom/rfwallpanel02_local, heightmap( textures/washroom/rfwallpanel02_h, 5))
WARNING: Couldn't load image: addnormals( textures/washroom/rfwallpanel03_local, heightmap( textures/washroom/rfwallpanel03_h, 5))
WARNING: Couldn't load image: addnormals( textures/washroom/rfwallpanel04_local, heightmap( textures/washroom/rfwallpanel04_h, 5))
WARNING: Couldn't load image: heightmap( textures/base_trim/a_sfltrim3yel_b02b, 2)
WARNING: Couldn't load image: heightmap( textures/base_trim/elec_box1_bmp, 2)
WARNING: Couldn't load image: heightmap( textures/base_trim/elec_box1s_bmp, 2)
WARNING: Couldn't load image: heightmap( textures/base_trim/elec_box2_bmp, 2)
WARNING: Couldn't load image: heightmap( textures/base_trim/yelhaz2bmp, 6)
WARNING: Couldn't load image: heightmap( textures/decals/biohazard_b, 1)
WARNING: Couldn't load image: heightmap( textures/decals/dang

```
any ideas?

---

### Post by Sockerdrickan on 2008-06-26
maybe a .pak is missing, check them

---

### Post by mrrsx2006 on 2008-06-26
Make sure all parts of the game are there. I would try looking up one of those files on google then see if the whole pack is available for download.

---

### Post by grossaffe on 2008-06-27
> **Tux0r said:**
> maybe a .pak is missing, check them

yeah, i actually decided to check the .pk4 files to see that they were all there.  turned out that I was missing pak004.pk4.  I think i may have left it out on purpose because the installation instructions I followed, if I remember correctly, didn't say to copy that one over.  oh well, its working now and that's what matters.

---

