---
title: "gaim notification sound"
date: 2005-05-02
forum: Desktop Environments
---

### Post by forcotton on 2005-05-02
I just figured out why my gaim sound, I need to change the default driver in /etc/libao.conf to alsa (which I am using). Now gaim does make a sound when my buddies go online. But hey... when I was playing a song, gaim can't let the sound go until the end of the song. This makes rhythmbox complain about failed to open device or something, and refuse to go on with the next song. 

My question is, why is gaim behaving like this? Since the notification sound is meaningless after such a long time, if gaim can't play the sound, it can just keep silent. That would be more sane.

---

### Post by Nis on 2005-05-03
What you're describing is a common problem.  You'll need to set Gaim to output sound to esd.  Since your soundcard cannot do hardware mixing getting multiple sounds to play at the same time requires software mixing.  esd is the GNOME way to do software mixing.  You must have it enabled in System/Preferencs/Sound and set System/Preferences/Multimedia Output to esdsink.  Log out and back in and see if you can play multiple sounds at once.  Unfortunately software mixing is much slower than hardware mixing and sometimes there is lag.  Soundcards that can do hardware mixing are getting pretty cheap nowadays so check [here](http://www.alsa-project.org/alsa-doc/index.php?vendor=All) to find one that does.

---

### Post by forcotton on 2005-05-03
[QUOTE=Nis]What you're describing is a common problem.  You'll need to set Gaim to output sound to esd.  Since your soundcard cannot do hardware mixing getting multiple sounds to play at the same time requires software mixing.  esd is the GNOME way to do software mixing.  You must have it enabled in System/Preferencs/Sound and set System/Preferences/Multimedia Output to esdsink.  Log out and back in and see if you can play multiple sounds at once.  Unfortunately software mixing is much slower than hardware mixing and sometimes there is lag.  Soundcards that can do hardware mixing are getting pretty cheap nowadays so check [here](http://www.alsa-project.org/alsa-doc/index.php?vendor=All) to find one that does.[/QUOTE]
 Thanks for the reply, but esd.. sucks. There is a noticeable latency when playing games. The alsa dmix software mixing is hard to get right , or is it just impossible? I always have audio-video sync problem when playing wmv file using mplayer, through alsa dmix. Maybe a good sound card is the only way to go...

---

