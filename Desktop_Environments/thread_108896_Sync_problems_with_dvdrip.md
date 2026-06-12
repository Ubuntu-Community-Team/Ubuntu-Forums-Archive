---
title: "Sync problems with dvd::rip"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Mastodront on 2005-12-27
This christmas Santa brought a couple of music-DVD's and because I want all my videos in a playlist and don't want to swap discs I thought I could rip and compress them (never done something like this before).

I found dvd::rip to be very competent and intuitive but I have some really annoying sync problems. I've tried both 1 and 2 pass coding, Xvid and Xvid4, "Use PSU core" both enabled/disabled and so on but it always gets the same result;
Great video/audio quality but really bad sync :(. When the clips start they're almost correct but then it gets worse and worse the longer the clip runs :(.

Anyone who has this problem who knows a good solution to my problem?

---

### Post by Ampersand on 2005-12-27
Have you tried playing them back using xine, mplayer or vlc? The version of gstreamer installed by default in Breezy (0.8) seems to have occasional problems with syncing, so it might be a problem with the playback rather than the encoding.

Another option would be trying Acid rip (also available through the repositories) which uses a different encoder to dvd::rip, and might have better results.

---

### Post by Mastodront on 2005-12-27
[QUOTE=Ampersand]Have you tried playing them back using xine, mplayer or vlc? The version of gstreamer installed by default in Breezy (0.8) seems to have occasional problems with syncing, so it might be a problem with the playback rather than the encoding.

Another option would be trying Acid rip (also available through the repositories) which uses a different encoder to dvd::rip, and might have better results.[/QUOTE]


Now I tried to play the clip using xine and actually it looks alot better :).
Both Totem (gstreamer) and mplayer still has some bad sync though. Now I don't have the original rips left so I can check but in the last rip I also passed -M 3 to transcode and that might have made some difference to but that's something I can check later. :)

Thanks for suggestions... :)

---

### Post by Mastodront on 2005-12-27
Hmm, now I've got another little question. Some of the videos has a couple of minutes of "crap" in the end that hasn't to do with the song. What would be the easiest way to cut the clip? I've seen kino mentioned in several threads to be a good video editor but when I tried it the last time it complained about every video format I tried to open :/.

Has anyone got any suggestions?

---

