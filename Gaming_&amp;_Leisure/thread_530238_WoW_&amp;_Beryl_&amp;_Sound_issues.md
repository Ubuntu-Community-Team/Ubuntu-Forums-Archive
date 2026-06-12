---
title: "WoW &amp; Beryl &amp; Sound issues"
date: 2007-08-20
forum: Gaming &amp; Leisure
---

### Post by MemoryDump on 2007-08-20
hi all,

I just recently re-installed Ubuntu and successfully got my Nvidia 7800GS & WoW installed & running very well as far as I can see :D

anyways, couple of issues..

1) I got Beryl running with no issues, however when I start Warcraft it loads up in a kinda "windowed/desktop" mode.. it doesn't load full screen.. but if I change my window manager back to MetaCity (I think it is) WoW loads in full screen mode.
2) whenever I ALT-TAB back to my desktop and back to WoW I lose my game sound and have to restart WoW to get it going again. I have Wine setup to using ALSA and I have a Audigy2 ZS sound card. I can listen to music (cd/mp3) while WoW runs.

oh.. and another thing.. doesn't anybody know if you actually get 4.1 sound if you have your system configured in that fashion? (at least I think I have it setup that way for my system setup)

thanks

---

### Post by UbuntuniX on 2007-08-20
For the first problem; That happens under Windows and probably OSX, too.
Doesn't seem to be a fix.

---

### Post by MemoryDump on 2007-08-20
hmm.. strange.. I guess nobody else noticed this while using Beryl?

also for my second issue.. it seems to be a bug with the last Wine version: [http://bugs.winehq.org/show_bug.cgi?id=9087](http://bugs.winehq.org/show_bug.cgi?id=9087)

---

### Post by cogadh on 2007-08-20
1. Never run games through Wine with Beryl running. From the Wine FAQ:
> **I'm using Beryl/XGL/Compiz and get poor performance/odd messages/broken applications**

Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely which is why we recommend that you disable them and remove composite from XOrg entirely before trying to use Wine. If you are using one and experiencing slow performance then DO NOT FILE BUGS as this is not a Wine bug. Just because TuxRacer runs fine doesn't mean it is Wine's fault, Windows games normally require a little more umph than basic Linux native games. Also to make sure, run glxinfo and make sure that it says "Direct Rendering : Yes".

2. Supposedly if you turn on "Enable sound in background" in the WoW options, this problem will go away.

You can only get 4.1/5.1/7.1 sound in Linux if the sound source is already a surround sound file. You can create custom ALSA configuration that will replicate the stereo signal across the front and rear channels, but it isn't really surround sound. Check the ALSA Wiki for more info and instructions:
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

