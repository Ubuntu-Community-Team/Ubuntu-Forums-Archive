---
title: "doom3 and ut2004 sound problems"
date: 2005-06-07
forum: Gaming &amp; Leisure
---

### Post by Napalmski on 2005-06-07
Hi all,

I have a SB live card and I have problems with the sound in UT2004 and Doom3. 

Doom3 has sound but it suffers from dropouts. I have experimented with the /etc/asound.conf file

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 8192
rate 48000
}
bindings {
0 0
1 1
}
}

But with this file I get a very distorted sound, or when I decrease the period-size or buffer_size I don't get sound at all. 

Second with UT2004 I have no sound at all. I have the following .openalrc file:

(define speaker-num 2)
(define devices '(alsa))
(define alsa-out-device "hw:0,0")
(define alsa-in-device "hw:0,0")

I have both doom3 and ut2004 working perfectly with Gentoo but Ubuntu gives me problems. Does anyone have a solution??

Thanks for any info.

Nap

---

### Post by Curlydave on 2005-06-07
For UT2k4 at least, you have to disable something in the sound menu of gnome, and do it again after every reboot. Sorry I can't be more specific, I don't remember exactly.

---

### Post by NeoChaosX on 2005-06-07
System -> Preferences -> Sound -> Untick "Enable Sound Server"

All you're really going to lose is sounds when GNOME starts up and for other GNOME events.

---

### Post by senkila on 2005-06-08
You should be glad you don't have sound in Doom 3.... i think it enhances the scaryness....i had nightmares for days after playing D3 in one sitting.

---

### Post by Napalmski on 2005-06-09
Thanks for the reply.

I do have sound in Doom3 but it skips sometimes. And I do have ESD disabled. Usually when something is blocking the soundcard you'll get a message in the terminal window where you start up the program.

Nap

---

### Post by dezgot on 2005-06-21
when i disable the sound server there my music (running from MusicPLayer) stops playing.  Is there a way to get it to play out of another server that won't interfere with ut2k4 or doom?

---

### Post by tristan on 2005-06-21
Make sure you select OSS as the sound backend in Doom3 (and not Best or Alsa). I've found that the sound is terrible using Alsa or Best in Doom3.

---

### Post by fig_jam_uk on 2005-08-13
[QUOTE=tristan]Make sure you select OSS as the sound backend in Doom3 (and not Best or Alsa). I've found that the sound is terrible using Alsa or Best in Doom3.[/QUOTE]

i had no sound at all till i swapped to OSS now all is well and im scared of the dark  :neutral:  oh good god what was that??? im turnin the soung off again   :razz:

---

