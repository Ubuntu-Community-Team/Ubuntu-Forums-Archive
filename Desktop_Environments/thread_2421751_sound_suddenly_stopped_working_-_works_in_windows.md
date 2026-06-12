---
title: "sound suddenly stopped working - works in windows"
date: 2019-06-26
forum: Desktop Environments
---

### Post by holiday on 2019-06-26
Sound was working fine last night, ubuntu installation is several weeks old, last update yesterday morning. This morning I started a Ubuntu VM I use for testing and found I had no sound through earphones though speakers were fine. 

 I tried another pair of earphones.  No Sound. I then discovered that I had no sound from the speakers! 

I rebooted into Windows. Sound okay.

Rebooted into Ubuntu, no sound. 

I have a monitor attached through HDMI and the 

I have worked through the checklist given here

[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

Here's what I find :

- sound card found
- not muted
- alsa re-installed
- ```
/etc/default/speech-dispatcher
``` does not exist.

There's this  that I don't understand though:


 ```

pactl list sinks |egrep -e 'Sink|State|Mute'
Sink #2
	State: SUSPENDED
	Mute: no

```



Otherwise I'm  out of tries. Where can I look next?

---

### Post by DanPerecky on 2019-06-26
If your sound works in Windows.... then it 'sounds like' an ubuntu driver problem..

HTH

---

### Post by holiday on 2019-06-27
The driver has been working for months so... Are you thinking it has become corrupted.

---

