---
title: "winecfg crashes when selecting 'audio' tab"
date: 2006-05-30
forum: Desktop Environments
---

### Post by QuacoreZX on 2006-05-30
username@computer:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/gtanaka/.kde/socket-gtanaka.
can't create mcop directory
username@computer:~$

And that's all I get.  obviously a problem with ALSA, but how would I go about fixing it?

---

### Post by Sam Lars on 2006-05-30
Hey, thanks, I didn't know about this winecfg...
But unfortunately I have the same problem, except I get this error in front of the rest:
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

---

### Post by drprofessor on 2006-05-31
For me this was related to the arts library used in wine and not having a seq device setup in /dev.   Removing /usr/lib/wine/winearts.drv.so and adding snd-seq to /etc/modules fixed it for me.  It may or not be the arts driver in your case, try removing some of the other sound libraries if removing arts does not work.  Removing the arts lib probably isn't the most elegant sollution though.  Hope this helps.

---

### Post by digitalhav0c on 2006-07-15
How did you do that im having the same problem also crashes when i open the audio tab

---

### Post by DavidFL on 2006-07-15
Just wanted to note the same thing happens for me.

---

### Post by tigrez on 2006-08-12
Good news! I've partially solved this problem.

$ mkdir ~/.kde/socket-tigre-desktop

Now you can change the audio settings.
I've installed arts too, but I think is not usefull.

---

