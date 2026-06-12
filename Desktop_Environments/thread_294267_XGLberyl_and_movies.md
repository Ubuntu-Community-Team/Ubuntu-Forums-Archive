---
title: "XGL/beryl and movies"
date: 2006-11-06
forum: Desktop Environments
---

### Post by kishe on 2006-11-06
every time i try watch videos with totem, gxine, mplayer, vlc...i get green haze all over the video...

---

### Post by Kateikyoushi on 2006-11-06
Try to change the output of the video from xv to X11. In mplayer right click, preferences and video.

```
-> if you have totem-gstreamer :
launch gstreamer-properties and select on default video playback &#8220;XWindow (NoXv)&#8221; in video tab.

-> if you have totem-xine :
edit ~/.gnome2/totem_config and replace this line :

#video.driver:auto

by

video.driver:xshm


```

[LINK]("http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/")

---

