---
title: "Quake Live sound trouble"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by weasel fierce on 2009-11-02
Tested out Quake Live and while I sucked badly, it's a lot of fun. After a few minutes the sound will disappear though. Other app's will still provide sound just fine. Any idea what gives?

---

### Post by 5nak3 on 2009-11-02
You never mentioned what version of Ubuntu you are using. 

In any case I have no idea if this will work, as I've not had any experience of the problem you have mentioned.

But maybe you should try and install libsdl1.2debian-pulseaudio. Doing this removes the default libsdl1.2debian-alsa which is installed. This solved a freezing problem that I was having with other games.

Maybe it works with quakelive. Failing that there is a lot of talk of actually removing pulseaudio altogether and installing alsa instead. I can't say whether or not this is going to solve the problem. But it may help. There are a number of threads in the forums that discuss the problems of pulseaudio, you might want to check them out.

---

### Post by basotl on 2009-11-05
Try putting:

s_mixahead 0.3 

in the in-game commandline (you can get it by pressing ~).

It helped my sound when it first came out for Linux.

---

### Post by 5nak3 on 2009-11-06
Also again something that may or may not help, but maybe turn doppler sound off. I found that that did upset my sound setup when it was enabled.

---

### Post by Bölvaður on 2009-11-06
I found this command helped me: s_alsa_pcm plughw:0
(I might have used something else than 0 as a parameter)

it is from [this thread ]("http://www.quakelive.com/forum/showthread.php?t=31897")



the only probolem that rose was that I was unable to hear any sound from any other source. so I couldnt use mumble (voip) any more

---

