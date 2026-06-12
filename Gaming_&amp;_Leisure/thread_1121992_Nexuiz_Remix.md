---
title: "Nexuiz Remix"
date: 2009-04-10
forum: Gaming &amp; Leisure
---

### Post by ahaslam on 2009-04-10
I've made a light-weight version of the 2.5 release suitable for netbooks & old rigs. It offers almost double the performance on old/underpowered hardware & weighs in at only 66MB which is a far cry from the original 636MB.

The main difference is compressed textures, re-encoded sound & a custom cfg. Gone are the external lightmaps, some demos, Netradiant (along with the rest of the Windows stuff) & the new player sounds. It retains support for 32bit Linux only as NetBooks are the main target.

Download: [http://omploader.org/vMWk4Mg/nexuiz-remix-25.zip](http://omploader.org/vMWk4Mg/nexuiz-remix-25.zip)
md5sum: 9848e7e6ac08a21c1d5a89a4cc77b8e4

Screenshot:

[img]http://omploader.org/vMWh6OQ/nexuizremix.jpg[/img]

Enjoy. :)

---

### Post by CharmyBee on 2009-04-10
Although the textures are minimal at best, it _still_ wouldn't be suitable for 'old rigs', as there is alot of polygons on models and such and there is no Hardware T&L pipeline used in the engine, so it'd still be slow from all the heavy vertex transformations. To get around this is to remodel everything low poly.

---

### Post by ahaslam on 2009-04-10
You have a point, tho I suppose that depends on your definition of old. It should be able to run on the average laptop at least (say 1GHz Celeron, GMA 950 & 512MB as a minimum).

Standard Nexuiz returns an average of 16fps on my AAO (at its lowest settings), this returns an average of 29. I left 'demo1' in the release so you can run your own benchmarks. The main reason for the performance difference is the rendering setting 'r_showsurfaces 3' - If you set this to 0 you'll regain simple textures at the expense of half the gain.

If your rig can't run this, maybe try: [http://www.alientrap.org/forum/viewtopic.php?t=4508](http://www.alientrap.org/forum/viewtopic.php?t=4508) - They've gone a step further by practically removing textures altogether, using 2d sprites & having hit-boxes instead of models, you'll also save another 10MB.

---

### Post by detrate on 2009-04-10
Nice!

Someone on the [Alientrap Forums](http://alientrap.org/forum/viewtopic.php?t=4508) just made a similar one! :)

---

### Post by ahaslam on 2009-04-10
I see an edit button & I gotta use it.

---

### Post by detrate on 2009-04-10
whoooops, sorry, missed that I got so excited about your first post :-P

---

### Post by RichardLinx on 2009-04-12
That's awesome. I found this page by searching Google for "Nexuiz on Netbook". I should just searched Ubuntu Forums instead:)

Has anyone here run this on a netbook? If you have could you post which model netbook, the specs, and what OS you're running on it.

---

### Post by ahaslam on 2009-04-15
Acer Aspire One, 1.5GB RAM, Arch Linux.

tdem demos/demo1.dem = 29fps av. Or did until mesa 7.4...

If you want lighter try the above link to the AT forums, they're working on making it better too, while I'm happy with mine. The more you mod, the less Nex remains imo...

---

### Post by wolfyking2 on 2009-04-18
Ah, thank you so much!!!!!!

---

### Post by barnex on 2010-01-24
Absolutely fabulous! Thanks a lot.

---

