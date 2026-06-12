---
title: "Strange ALSA problem with amaroK"
date: 2006-06-03
forum: Desktop Environments
---

### Post by _Petya_ on 2006-06-03
Hi!

I have Kubuntu dapper installed from the desktop cd, and i've encountered problems with mp3 playback. mplayer and vlc works OK, but amaroK just skips over the tracks in the playlist. At startup, amarok dumps this to the console, hope it may help: 

[http://pastebin.com/755095](http://pastebin.com/755095)

In amaroK, i'm using Xine, with alsa output plugin. I've tried oss, got the same problem. Choosing esd simply crashes amaroK. Selecting aRts instead of Xine also crashes amaroK.

Thanks for your help.

Petya

---

### Post by des~ on 2006-06-03
Have you installed libxine-extracodecs? Amarok requires those to play mp3-files. If not then > sudo apt-get install libxine-extracodecs You'll have to have universe or multiverse enabled to install those, not sure which one though :/

---

### Post by _Petya_ on 2006-06-03
Thanks! It works!
(it's in multiverse)

Petya

---

