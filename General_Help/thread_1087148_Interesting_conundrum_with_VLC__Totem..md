---
title: "Interesting conundrum with VLC / Totem."
date: 2009-03-04
forum: General Help
---

### Post by noseforsharpies on 2009-03-04
Totem absolutely crashes when I load an .AVI file. VLC, on the other hand, will "play" the video - just with no video. So, I was digging around in my main folder ( "derek" ) and saw, literally, a .PNG for each part of the video that VLC "played." So what's going on?

---

### Post by Darkshade on 2009-03-04
VLC's video output is set to Image Video Output which creates one image for every X frames of the video. Change your output module to XVideo or X11 in your VLC preferences and it should be fine.

---

