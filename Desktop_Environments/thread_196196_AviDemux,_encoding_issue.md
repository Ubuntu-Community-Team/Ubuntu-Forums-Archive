---
title: "AviDemux, encoding issue"
date: 2006-06-13
forum: Desktop Environments
---

### Post by jISh on 2006-06-13
Not entirely sure where to post this, but this seemed like the most logical place...

Anyways, I've been attempting to learn a good way of converting AVIs to DVDs on Linux. I seem to have found a way that is comfortable for me, using AVIDemux and DVDStyler. 

Every step I went through (I originally used the guide from Videohelp.com, but this software was very easy to figure out and I went my own way after a bit, because that guide is outdated) worked out right up to the DVD burning, and the disc played back in my player. There is one exception to this, which I didn't realize before I burned the disc (should have mounted and tested..). 

Problem:
**My finished MPG file (both before and after multiplexing with the audio streamI  plays way too fast. The movie is 2 hours and 21 seconds long, but in Totem and on my DVD player the MPG file is only 1 hour and 26 seconds long. The Audio is far behind the video, of course. Iused the DVD(lavcodec) option, used the bitrate calculator to figure out my bitrate. I set the min bitrate and max bitrate to the required number the calculator gave to me(is it here that I went wrong?) Two pass encoding, TMPGenc matrix, progressive interlacing.**

Any ideas?

---

### Post by damir on 2006-06-14
Same problem here (for 1.5 year). I read something on avidemux forum, but didn't find solution. Only mplayer shows right time.

My .mpg file is always showing bad duration time, but when I make DVD structure (qdvdauthor -> VIDEO_TS), I always test it and it shows right time. And this is confusing.

It's something with ffmpeg and how it writes bitrate into .mpg file, I think. Than player calculates duration time using bitrate, not using framerate. Maybe... I don't know.... But it's annoying!

---

### Post by blknit on 2006-06-14
A good alternative could be tovid :

[http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)

---

### Post by jISh on 2006-06-14
damir:
The thing is, when I build the DVD structure, it's still playing too fast. On my DVD player, it would play all jumpy, and on the computer it played way too fast so the audio can't keep up with it. This is a problem with the MPG, and it's the ONLY thing stopping me from a very easy method of burning DVDs on Linux :(

blknit:
Thanks, but I'd like to make sure there is absolutley no solution to this before moving on to a different program.

---

### Post by jISh on 2006-06-14
Update: Seems that the bug is resolved in version 2.1.2. It was a problem with writing pulldown flags. However, only 2.1.1 is available in the multiverse. 

Added debian-multimedia.org unstable to my repository list, 2.1.2 is there, but it's dependancies are not installable...ugh,

```

avidemux:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
 Depends: libdirectfb-0.9-24  but it is not installable
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24-0.3 is to be installed
  Depends: libfaad2-0 (>=2.0.0+cvs20060416) but 2.0.0-0.5 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
 Depends: libmozjs0d  but it is not installable
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

```

:O *doesn't know what to do now...

---

### Post by blknit on 2006-06-24
[QUOTE=jISh]Update: Seems that the bug is resolved in version 2.1.2. It was a problem with writing pulldown flags. However, only 2.1.1 is available in the multiverse. 

Added debian-multimedia.org unstable to my repository list, 2.1.2 is there, but it's dependancies are not installable...ugh,

:O *doesn't know what to do now...[/QUOTE]

Try this link :

[Avidemux2.2_preview2_dapper]("http://prdownload.berlios.de/avidemux/avidemux_2.2_preview2_ubuntu.deb")

Hope it helps

---

