---
title: "Compizfusion video problems"
date: 2007-09-09
forum: Desktop Environments
---

### Post by xprinceps on 2007-09-09
I am running Compizfusion in Feisty Fawn on a T2400 dual-core with Mobile 945GM Express Integrated Graphics Controller. Compiz seems to be working fine; I can rotate the workspace cube, and I even have the Atlantis plugin working. However, when Compiz is enabled, I can't watch videos. They open in Mplayer or VCLmediaplayer, show the first frame, then go blank. The audio continues playing, though. Without Compiz enabled, everything works fine; I even have quicktime working as a Firefox plugin.
"glxinfo | grep direct" tells me "yes", and "glxgears" shows me rotating gears, so I don't think this is a driver problem.
Does anyone have an idea what may be happening here (and how to fix it!)?

---

### Post by Happy_Man on 2007-09-09
Have you enabled the "video playback" plugin in the Compiz Settings Manager?

---

### Post by edd07 on 2007-09-09
I have the same problem on an Intel GMA 950, and I do have the video plugin enabled. Every video app starts, and suddenly crashes when it should start playing.

---

### Post by xprinceps on 2007-09-09
Happy,
I didn't have video enabled (and I got my hopes up for a simple solution), but now I do and nothing has changed. Some possible clues I should have included in the original post: The 'show first frame and then go black' behavior is in MoviePlayer and VLC media player (the file continues to play in both cases, and I can hear the audio). Mplayer gives a fatal error: "Error opening/initializing the selected video_out (-vo) device."

---

### Post by ryno519 on 2007-09-09
Here's the workaround for VLC.

Go to;

Settings -> Preferences -> Video -> Output modules

and select X11 Video Output. That should fix the problem. You can do the same thing with most any video player, I just don't know how to do it with anything besides VLC. Hope that helps.

---

### Post by xprinceps on 2007-09-09
ryno519,
That worked great for VLC! I found a similar setting in mplayer, and now it works, too. Thanks so much for the help.

---

### Post by Happy_Man on 2007-09-09
Hmmm.... I didn't know about that. Thanks for that tip. I'll have to file it away in the dusty cobwebbed back alleys of my brain.

---

### Post by FrooziE on 2008-07-23
> **ryno519 said:**
> Here's the workaround for VLC.

Go to;

Settings -> Preferences -> Video -> Output modules

and select X11 Video Output. That should fix the problem. You can do the same thing with most any video player, I just don't know how to do it with anything besides VLC. Hope that helps.


This fixed the problems i had with videos in compiz as well as streaming videos on sites such as youtube. Video files would lag for about 3 seconds every now and then even though the sound kept playing without interruption. After changing the settings in VLC as you suggested it stopped happening. Next i installed the vlc plugin for mozilla and that fixed all my streaming related issues. thanks again.

---

