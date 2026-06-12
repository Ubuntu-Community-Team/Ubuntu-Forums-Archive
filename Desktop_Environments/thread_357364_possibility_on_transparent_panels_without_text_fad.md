---
title: "possibility on transparent panels without text fading???"
date: 2007-02-09
forum: Desktop Environments
---

### Post by headlice on 2007-02-09
Is it possible to get the panels to become transparent, yet have the text remain visible?  Possibly even make the text white (using black wallpaper)?

ETA: using 6.10

---

### Post by mcduck on 2007-02-10
Real transparency is not possible without fading everything in panels, but you can get fake transparency that shows your desktop through the panel. There are 2 ways to do this, easier one is to right-click on the panel, select 'properties' and then adjust transparency on the background tab. The nicer way is to use some transparent .png or .svg picture as your panel's background pic. You can do it in same place, or simply by drag&dropping some pic to your panel.

If you use a transparent pic you should make the pic's size as close to your panel's size as possible, and you may also want to enable image scaling for panel backgrounds in gconf-editor.

I'm using transparent .png-backgrounds together with Beryl's setting of 80% opacity for panels. It gives nice backgrounds, easy-to-read text and still shows enough of windows behind panels to look real..

---

