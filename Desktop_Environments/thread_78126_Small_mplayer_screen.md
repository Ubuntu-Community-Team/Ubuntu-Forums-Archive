---
title: "Small mplayer screen ?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dbee on 2005-10-17
Hi,

Whenever I play my bittorrents on my computer the movies work fine, but the screen area is tiny ... about 3inches by 2inches.

I use mplayer ... what do you think the problem might be ?
I have tried adjusting the screen resolution etc... but no luck.
Is there some way that I can find out what the error is ??

thanks

---

### Post by neutro on 2005-10-17
It just plays at the original resolution. Hit F to expand it to fullscreen. This can be the default behavior if you set fs=yes in ~/.mplayer/config or in /etc/mplayer/mplayer.conf. You may have to set zoom=yes, too, I don't remember well.

---

### Post by Murgle on 2005-10-18
you will have to set zoom=yes or use the -zoom and -fs options on the command line.  the other alternative is to set vo=xv and then you will not need the zoom

---

### Post by Ugeek on 2005-10-22
inctsll libxv1 then in gui mode go to settings and make video driver as xv. or in text mode use (-vo xv) option

---

### Post by Luggy on 2005-10-24
You can also edit /etc/mplayer/mplayer.conf and change the default video mode to xv to get the non-GUI version to work.

---

### Post by ykpaiha on 2005-10-27
I however prefer to use codeine for my avi-file
Kaffeine is too fragile actually for me.

---

