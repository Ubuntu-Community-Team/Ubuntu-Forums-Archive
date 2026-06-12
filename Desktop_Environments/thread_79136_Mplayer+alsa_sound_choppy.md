---
title: "Mplayer+alsa sound choppy"
date: 2005-10-19
forum: Desktop Environments
---

### Post by 3david on 2005-10-19
When i run "mplayer -ao alsa file.avi" i get choppy sound,
and i get these messages:

```
alsa-space: xrun of at least 0.064 msecs. resetting stream?,?% 0 0 85%
alsa-space: xrun of at least 0.065 msecs. resetting stream0.6% 0 0 82%
alsa-space: xrun of at least 0.062 msecs. resetting stream0.6% 0 0 81%
alsa-space: xrun of at least 0.068 msecs. resetting stream0.6% 0 0 80%
alsa-space: xrun of at least 0.068 msecs. resetting stream0.6% 0 0 80%

```
but when i run "mplayer -ao oss file.avi" the sound is perfect

I used the instructions from this thread to install the win32codecs: [http://ubuntuforums.org/archive/index.php/t-22160.html](http://ubuntuforums.org/archive/index.php/t-22160.html)

any ideas?

---

### Post by Murgle on 2005-10-19
run it with oss... Why do you need alsa?

---

### Post by 3david on 2005-10-19
i need alsa, because if i use oss, then i have to close every other program that uses the sound card (gaim sound notifications, ...), and i have to stop my music player (happens both beep and mpd), because oss can't use the soundcard if someone else uses it.

---

### Post by Murgle on 2005-10-19
have you tried esd?

---

### Post by 3david on 2005-10-20
10x for that, I've just tried mplayer -ao esd, and there's no problem with the A/V sync, it's perfectly synchronized.

But why doesn't it work well with alsa?

Edit: when i use mplayer with esd then moving backwards and forwards in a movie becomes much slower, so this solution isn't exactly a full solution.

---

### Post by metoo on 2005-10-20
Newer ALSA uses dmix as default on hardware without hardware mixer. (Mixing sound from different sources at real time).

Test if the entry:

ao=alsa:device=plug=dmix

in ~/.mplayer/config
makes a difference.
With that you don't have to specify the -ao option:
mplayer file.avi
should do it.

---

### Post by 3david on 2005-10-20
once i added "srate=48000" to ~/.mplayer/config the choppy sound and the alsa-space error messages disappeared, but now there's an a/v sync problem (which is solved by using ao=esd, but moving forward/backwards in a movie is slower than with alsa and oss)

i've tried "ao=alsa:device=plug=dmix" (while commenting srate=48000) and it doesn't fix the choppy sound.

to sum things up:
- choppy sound is solved by adding "srate=48000" to ~/.mplayer/config
- but now there's a new problem: no a/v sync when using alsa, the synchronization improves when i use "autosync=...", but still, the sync is not as perfect as with esd.

---

