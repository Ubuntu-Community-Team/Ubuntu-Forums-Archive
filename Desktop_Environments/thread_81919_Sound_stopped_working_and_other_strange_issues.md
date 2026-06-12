---
title: "Sound stopped working and other strange issues"
date: 2005-10-25
forum: Desktop Environments
---

### Post by gaz514 on 2005-10-25
Hey, I'm using Breezy and sound's been working perfectly, until now. I've installed Gentoo on another partition to experiment with that and attempting to get sound working, and while I don't see how that can be related at all, my sound on Ubuntu is going dodgy. When I open XMMS and try to play an MP3, I hear the first half-second or so of the song, then it just stops playing and refuses to play anything else, and no other sound works anymore. I tried quitting XMMS and trying to play again, and I get this message:

Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard.

Another thing, not so much related to sound... I also have Windows XP installed, and I started it up because I wanted to listen to music, but now Windows seems to be randomly restarting the computer a couple of minutes or so after starting up whenever I use it. Again I'm not sure if the Gentoo install affected it or it's just coincidence.

---

### Post by Moonbuzz on 2005-10-25
It seems that XMMS has problem sharing the sound card. I've been having a similar issue with that application. If it plays, no other sound can be heard. If you try playing a song, and a system sound is played, you'll get that sound card warning. I used to have those issues with Winamp on Win98, almost forgot about this till now, I think it has to do with drivers, or with some input plugin to XMMS, but I'm not really sure :)

---

### Post by Moonbuzz on 2005-10-25
I think this might help:

[http://forum.xmms.org/viewtopic.php?t=1153](http://forum.xmms.org/viewtopic.php?t=1153)

---

### Post by gaz514 on 2005-10-25
That link didn't help, I had already tried killing esd with no luck. It just seems strange how it was working perfectly fine until now.

---

