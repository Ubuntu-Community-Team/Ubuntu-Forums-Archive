---
title: "Totem audio crackling on PCM sound"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Douglas Royds on 2006-08-18
Before upgrading to Ubuntu Dapper, Totem was able to play every video file that I had thrown at it. I'm now getting badly munged sound on .avi files, notably those from our own digital camera. It is crackling badly, though some of the sound can be heard in the background.

The audio codec in question is Linear PCM (not exactly challenging) at 88kbps. Seems to be a codec problem.

Audio playback is fine from .mpg (a Sony digital camera) using MPEG audio layer 2 codec, and audio playback is fine from DVD.

MPlayer plays the same .avi file just fine, no crackle.

---

### Post by glennric on 2006-08-18
I have had this same problem ever since installing Dapper on my wifes computer.  Totem sound works fine on my computer.  That computer was dist-upgraded from Breezy.  Anyone have any ideas?

---

### Post by Douglas Royds on 2006-08-20
Should add that I'm running totem-xine, not the default totem-gstreamer (totem-xine plays DVDs nicely). I assume this is some sort of breakage in the xine codecs, especially since mplayer plays the .avi files fine.

---

