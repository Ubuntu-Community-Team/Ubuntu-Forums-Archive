---
title: "Odd sound problem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Fridericus on 2005-10-17
Hey all.

I installed Breezy today and I am now experiencing some very weird sound problems. I'm using ALSA for audio (followed all the different HOWTOs, I used ALSA in Hoary also with no problems). 

The sound works, but it sounds really bad especially when playing MP3s. You hear the music but you get some sort of weird audio artifacts it sounds almost as if your streaming some slow Realplayer video hosted in Japan, you know how weird the audio can sound? High pitch sounds and some different, almost like an electric whip. ;) Hard to describe, but something like that.

The sound problem is in all players I've tried, Rhythmbox, VLC, Totem etc. I havent heard any similar sound errors when playing Video (XVID), the audio seems fine there.

So what could it be? Codec problems? Please help!

---

### Post by KingBahamut on 2005-10-17
hmmm, sounds like a codec issue. Have you installed all the gstreamer stuff? 

apt-get install gstreamer0.8-plugins

---

### Post by Fridericus on 2005-10-17
[QUOTE=KingBahamut]hmmm, sounds like a codec issue. Have you installed all the gstreamer stuff? 

apt-get install gstreamer0.8-plugins[/QUOTE]

Yep. I followed the Guide in Help->Ubuntu 5.10 Starter Guide->Applications->Music and Movies

---

### Post by Fridericus on 2005-10-17
Hmm, I am playing some OGG files, no sound problems here. No problem streaming internet music either.


It MUST be a codec problem.

---

