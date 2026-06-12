---
title: "UT 2004 Input Not Supported :["
date: 2008-09-28
forum: Gaming &amp; Leisure
---

### Post by guitarbum93 on 2008-09-28
ok so i had windows and wanted to dual boot it with ubuntu but i screwed it up and now i only have ubuntu ;D

but anyway, i installed unreal tournament 2004 and it installed flawlessly. now when i try to play, the "splash" screen thing (thats what i think its called) pops up, then turns gray, then my screen goes black and says "Input Not Supported"

i tried reinstalling it, then i tried running it in wine, still the same problem

has anyone else had this problem?

does anyone know how to fix it?

thank you 
-sean :]

---

### Post by Brebs on 2008-09-28
After doing a little bit of [googling](http://www.google.co.uk/search?hl=en&as_q=ut2004&as_epq=input+not+supported&as_oq=&as_eq=&num=30&lr=lang_en&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=off), the problem is that your monitor doesn't support whatever resolution UT2004 is defaulting to.

If ~/.ut2004/System/UT2004.ini exists, then set the X and Y values appropriately for your monitor, in the section:
```
[SDLDrv.SDLClient]
...
FullscreenViewportX=1280   <--- Change this 1280
FullscreenViewportY=1024   <--- Change this 1024
```

---

