---
title: "Video playback with Beryl running"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by quinnten83 on 2007-05-21
I've just noticed that when i try to play any videofile in any player (vlc or movieplayer) the screen stays black. When i drag the video window, while it is still playing, I see flashes of the movie it's playing, but then the image is not build up further and everything stays black.
Once I turn beryl window manager off, i can watch the video again, no problem, once it is turned back on, no more video.

Is this a know bug?
Is there a way around this? I don't want to turn off Beryl, since it is the reason i got interested in Linux to begin with.

I'm not desperate though, as a simple clik allows me to watch my videofiles.

lspci reveals that I am running 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
in my compaq Evo 610c

(I think I saw a sticky about ATi Radeon cards??)

---

### Post by Hellcom on 2007-05-21
Try chaning the output the module in vlc (not sure about moive player)

Preferences > Video > Output modules (Check &#8220;Advanced") > Change to another output

---

### Post by quinnten83 on 2007-05-21
Dude, 
that like totally worked (for VLC anyhow).
My gratitude is eternal...

I'm actually suprised it could be so easy...

---

