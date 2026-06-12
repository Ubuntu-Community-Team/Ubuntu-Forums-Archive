---
title: "All codecs installed, mp3 plays but still no sound in video.."
date: 2006-01-15
forum: Desktop Environments
---

### Post by peRosine on 2006-01-15
Dear readers,

I have installed all the codecs available (Automatix thanks!) and my sound works. I can hear system sounds and also play mp3's.

My only problem is that when I play a video I do see the video but there is no sound. I find this really strange because it should work!

Can anyone help me out with this and tell me how to get my sound in video's working?

(Have already tried all differend players, gxine, mplayer, totem, all the same... video, but no sound)

---

### Post by syklitengutt on 2006-01-15
what sound plugin do you use in the movie app?
try to reeboot and start a movie at once!

---

### Post by peRosine on 2006-01-15
In Mplayer I now use Alsa. I do here the sound now, but constantly shaking and getting the error:

alsa-control: unable to find simple control 'PCM, 0'.

---

### Post by peRosine on 2006-01-15
I found a way to fix it, but it is really strange.

I first open the video file, than I adjust the volume... Nothing happends yet.
Than I close, and re-open the file and the sound works this time.

When I close the file again withoud moving the volume control and re-open the sound is gone again.

How strange is this!

---

### Post by christhemonkey on 2006-01-15
thats well random!!!

---

### Post by peRosine on 2006-01-15
Ok, the sound now always plays. I disabled my onboard sound and that fixed it.

Also fixed the volume control of my keyboard with xbindkeys.

---

