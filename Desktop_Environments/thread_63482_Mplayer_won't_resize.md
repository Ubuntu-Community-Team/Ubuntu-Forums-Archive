---
title: "Mplayer won't resize"
date: 2005-09-08
forum: Desktop Environments
---

### Post by last1 on 2005-09-08
When I play a video in mplayer on this old laptop, it plays in this tiny box, and when I try to resize it or go fullscreen, the video stays the same size and the rest of the screen is black.
Ends up playing video looking like this
[IMG]http://static.flickr.com/25/41370730_0dfba6f590.jpg[/IMG] 

Anybody know how I fix it?
It's a Toshiba Satellite 4030CDT.

---

### Post by foxy123 on 2005-09-08
[QUOTE=last1]When I play a video in mplayer on this old laptop, it plays in this tiny box, and when I try to resize it or go fullscreen, the video stays the same size and the rest of the screen is black.
Ends up playing video looking like this
[IMG]http://static.flickr.com/25/41370730_0dfba6f590.jpg[/IMG] 

Anybody know how I fix it?
It's a Toshiba Satellite 4030CDT.[/QUOTE]
change a video codec in video preferences...

---

### Post by Hairy_Palms on 2005-09-08
launch it with 
gmplayer -zoom
and u can resize it.

---

### Post by last1 on 2005-09-08
[QUOTE=Hairy_Palms]launch it with 
gmplayer -zoom
and u can resize it.[/QUOTE]
 Well it worked with the zoom option, but the video was dropping lots of frames and not keeping up with the audio. I guess maybe it's just too slow to play video fullscreen. Oh well, thanks for the help  :)

---

### Post by foxy123 on 2005-09-09
[QUOTE=last1]Well it worked with the zoom option, but the video was dropping lots of frames and not keeping up with the audio. I guess maybe it's just too slow to play video fullscreen. Oh well, thanks for the help  :)[/QUOTE]
right-click on the MPlayer, go to Preferences,click Video tab and change video codec to xv. Restart MPlayer and it will be ok.

---

