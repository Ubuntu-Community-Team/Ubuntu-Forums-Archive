---
title: "Remove Black Border Starterbar"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Stambo00 on 2006-01-11
Is it possible to change or remove the black border for starterbar in gdesklets? I'm trying to get it to look like a Mac. Thanking you in advance for any help.

---

### Post by jasay on 2006-01-11
There doesn't seem to be a place to configure the border.  However, you can edit the source code (yay open source!!:) )  Right click on the starterbar and select view source.  Find this spot:```
  <!-- the panel with borders -->

  <frame watch="x=iconbar:panel-x, y=iconbar:panel-y,
                width=iconbar:panel-width, height=iconbar:panel-height"
         border-width="4, 4, 4, 4"
         border-uris="gfx/bg-w.png, gfx/bg-n.png, gfx/bg-e.png, gfx/bg-s.png,
                      gfx/bg-nw.png, gfx/bg-ne.png,
                      gfx/bg-se.png, gfx/bg-sw.png">
    <group id="panel" bg-color="#3a416ba0" width="100%" height="100%"
           watch="bg-uri=iconbar:background"/>
  </frame>


```If you delete this section and restart the desklet you will no longer have the border or background.  You could also edit the graphics in ~/.gdesklets/Displays/starterbar-desklet-*/gfx if you just want it to look different.

---

### Post by Stambo00 on 2006-01-11
Thankyou works great

---

