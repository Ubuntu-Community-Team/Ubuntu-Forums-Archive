---
title: "mplayer problems in edgey"
date: 2006-10-23
forum: Desktop Environments
---

### Post by irish rebel on 2006-10-23
Guys I installed rc of edgey on Thursday everything seems to work ok except mplayer there are no mplayer /firefox plugins and even though I installed codecs there does not appear that mplayer can play anything at all .Any ideas would be great.

---

### Post by Dr. Nick on 2006-10-23
Is the package mplayer-mozilla installed? I had a bit of trouble with mplayer after a update, just had to mark it for reinstallation and it fixed it.

If mplayer-mozilla is insatalled check to make sure that totem-mozilla (or similar) isnt installed.

Type ```
about:plugins
``` into the FF address bar and see what plugin is used for video, mine defaulted to totem which didnt work, removing the totem package and installing the mplayer one worked

---

