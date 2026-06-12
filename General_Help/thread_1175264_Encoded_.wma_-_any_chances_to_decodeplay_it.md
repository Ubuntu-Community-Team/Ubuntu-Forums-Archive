---
title: "Encoded .wma - any chances to decode/play it ?"
date: 2009-05-31
forum: General Help
---

### Post by ActiveFrost on 2009-05-31
```
Input #0, asf, from 'kill_soft.wma':
Duration: 00:06:34.45, start: 1.579000, bitrate: 129 kb/s
Stream #0.0(eng): Audio: wmav2, 44100 Hz, stereo, s16, 128 kb/s
```

w32codecs, non-free-codecs, etc. - they all have been installed .. still no luck in opening this file ( song ) :(
Any ideas/advices ?

---

### Post by jonathanysp on 2009-05-31
what program are you trying to play it with? vlc sometimes works better than totem for me

---

### Post by ActiveFrost on 2009-05-31
> **jonathanysp said:**
> what program are you trying to play it with? vlc sometimes works better than totem for me

Rythmbox, Audacious, VLC ..

---

### Post by mc4man on 2009-06-01
As far as wma2, wma in general
vlc won't play unless dmo loader is enabled in the build - eliminates the repo versions

gstreamer apps (rhythmbox, banshee, ect. will play if w32codecs is installed and some of the gstreamer plugins (gstreamer 0.10-pitfdll in particular) - you may want the bad and ugly for other things, search in synaptic, install the first and fourth listed for bad and ugly, the pitfdll and the ffmpeg one
gstreamer apps may only play wma2 and wmal, not wma3(pro)

amarok will play all wma (wma2,wma3(pro), wmal (with w32codecs and libxine1-ffmpeg
mplayer will play all wma
totem-xine will play all (with w32codecs and libxine1-ffmpeg

I don't think audacious supports wma
Edit: actually audacious **will** play wma2

---

### Post by ActiveFrost on 2009-06-01
> **mc4man said:**
> As far as wma2, wma in general
vlc won't play unless dmo loader is enabled in the build - eliminates the repo versions

gstreamer apps (rhythmbox, banshee, ect. will play if w32codecs is installed and some of the gstreamer plugins (gstreamer 0.10-pitfdll in particular) - you may want the bad and ugly for other things, search in synaptic, install the first and fourth listed for bad and ugly, the pitfdll and the ffmpeg one
gstreamer apps may only play wma2 and wmal, not wma3(pro)

amarok will play all wma (wma2,wma3(pro), wmal (with w32codecs and libxine1-ffmpeg
mplayer will play all wma
totem-xine will play all (with w32codecs and libxine1-ffmpeg

I don't think audacious supports wma
Edit: actually audacious **will** play wma2

MPlayer did the trick - thanks again :)

---

