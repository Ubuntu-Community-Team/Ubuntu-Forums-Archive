---
title: "Choppy PLayback on DVD's despite DMA enabled"
date: 2006-03-14
forum: Desktop Environments
---

### Post by khalidmian on 2006-03-14
I have i/o as 32 bit and DMA enabled but my DVD's are still choppy, Can anyone suggesta remedy

---

### Post by super on 2006-03-14
is this in all media players or just a particular one?
and what do you mean by choppy? is the sound lagging, is the picture tearing or is it just dropping too many frames?

---

### Post by steevc on 2006-03-14
I found my DVD playback was bad in some players (Totem, Xine), but VLC plays them fine and CPU usage was not too high. This was after I enabled DMA.

---

### Post by khalidmian on 2006-03-15
The picture is tearing the sound is fine. the picture seems to be jumping up and down. Re VLC when i choose VLC for download it suggested i get XMVLC or something like that instead of VLC player . I have not been able to find the new VLC version under any repositories. Kindly suggest

---

### Post by dicecca112 on 2006-03-15
have your video card drivers installed

---

### Post by super on 2006-03-16
[http://www.videolan.org/vlc/download-debian.html]("http://www.videolan.org/vlc/download-debian.html")

the above is the site to get the latest vlc install instructions if you haven't found it already.

picture tearing could be you deinterlace settings, make sure it is turned on.

and it think 'dicecca112' makes a good suggestion. if you video is bouncing it could be your video drivers. make sure you have the latest anf greatest drivers available. also, check your video output settings in your media player. use the 'xv' output if it is possible on your card.

---

