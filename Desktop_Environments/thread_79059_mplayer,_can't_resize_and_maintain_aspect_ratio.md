---
title: "mplayer, can't resize and maintain aspect ratio?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by dudinatrix on 2005-10-19
I changed the mplayer video driver to xv and am now able to resize videos with no problem. However, it does nothing to maintain the aspect ratio. When I go full screen, it stretches out the image to fill the screen, making everything look stretched. (I have a widescreen monitor).

Any ideas on how to resize while maintaining the aspect ratio?

---

### Post by Hairy_Palms on 2005-10-19
run gmplayer -zoom

---

### Post by dudinatrix on 2005-10-19
[quote=Hairy_Palms]run gmplayer -zoom[/quote]
Tried that.. doesn't work.  It always stretches to fit the window size no matter what I try.

---

### Post by Donza on 2005-10-24
Same problem here too with a 16:9 monitor. I'm using totem-xine player now. Works as well as mplayer but keeps the aspect ratio correct.

---

### Post by Bitmastro on 2005-10-24
You can also try this
```
sudo gedit /etc/mplayer/mplayer.conf
```
and set 
monitoraspect=16:9

---

### Post by Pablo_Escobar on 2005-10-24
Why don't You use the "gl" driver for video playback ?

---

