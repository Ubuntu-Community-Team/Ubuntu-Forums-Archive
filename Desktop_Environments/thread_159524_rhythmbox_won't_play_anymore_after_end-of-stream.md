---
title: "rhythmbox won't play anymore after end-of-stream"
date: 2006-04-13
forum: Desktop Environments
---

### Post by droefs on 2006-04-13
Radio streams can give an "unexpected end of stream"; when this happens, rhythmbox sometimes crashes. 

When relaunching it, it is impossible to play any music with it, I get "Couldn't stop playback - Failed to close audio output sink" and a second error pop-up telling me "Stream error - Unexpected end of stream!". But there is nothing streaming anymore... when I # ps -aef, nothing rhythmbox-wise shows up. 

So far the only thing I've been able to do to get my music back is rebooting the whole system ](*,) .

---

### Post by matthinckley on 2006-05-16
I had the same problem, I went to System -> Preferences -> Multimedia Systems Selector and changed the Default Sink to ALSA and now it works great

---

### Post by droefs on 2006-06-27
Well, lucky you, I gave that a try but for me it doens't change a thing. I noticed just logging in and out of my X-session gets my music playing again too. But surely there must be a more graceful way of solving this. Anyone?

---

