---
title: "Super-key not working in XGL"
date: 2006-08-15
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-08-15
Hey, I've followed this amazing [guide (see "Turning up the graphics")]("http://tazforum.thetazzone.com/viewtopic.php?t=2189") to setting up XGL/Compiz on my dapper installation...

the "rain" effect doesnt work, and the tutorial says that the rain effect is supposed to be shift+f9.

also, I cant set my own picture as the cube dome... i set the path to the picture in the gconf-editor, but nothing happens when i restart xgl..

---

### Post by BitTorrentBuddha on 2006-08-15
Hey, by default my install didn't have the water plugin added to the active plugins. Go into gconf-editor under /apps/compiz/general/allscreens/options and make sure 'water' is on the list somewhere. Also about the skydome, I frequently have issues using jpegs so try and make sure whatever you're using is a png and make sure to give the full file path. Hope that helps.

---

### Post by stiankarlsen on 2006-08-15
SOLVED THE WATER PROBLEM
 - turns out the plugin wasn't activated, to activate it, i went to /apps/compiz/general/allscreens/options and added "water" to active_plugins


I also tried with a PNG and the full path, but no go on that one (so far).

thanks for your response.

---

### Post by BitTorrentBuddha on 2006-08-16
Are you applying the image path to /apps/compiz/plugins/cube/screen0/options/skydome_image or some other area, that's where mine is with compiz quinn29 also make sure that /apps/compiz/plugins/cube/screen0/options/skydome is enabled.

---

### Post by stiankarlsen on 2006-08-18
Thanks for your replies

turns out I just needed the right resolution of my dome image.

1024x1024 or 2048x2048 or 2048x1024 works for me.

---

