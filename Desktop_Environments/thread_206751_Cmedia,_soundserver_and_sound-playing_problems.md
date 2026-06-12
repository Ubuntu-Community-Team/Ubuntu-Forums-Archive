---
title: "Cmedia, soundserver and sound-playing problems"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Pawel on 2006-06-30
Hi!

I have a various problems with sound playing in the last Ubuntu release (6.06 LTS).

In short:
When soundserver system is enabled - i can play music via xmms but he can't use skype or mplayer (sound doesn't work).
When soundserver is disabled - i can listen and watch video via mplayer and use the skype but not use the xmms. At the best case - xmms can play but can't set the volume.

I trying all of capabilities in mplayer (ALSA, OSS, ESD) and XMMS but it doesn't work for me. i think that sth is wrong in one of configuration file of suondsystem but i don't know what it is.
Maybe sb is knowing what is it ?

Sound Device: CMedia 8078

Best regards 
Pawel

P.S. Sorry for my english ;)

---

### Post by darkpark on 2006-06-30
Czesc Pawel!

Witam z USA!  

What does xmms have its output set for?  ALSA?

Try running 'gstreamer-properties'  from a terminal and set the default sound output to alsa.  also, be sure to set mplayer to use alsa for sound output.


-slawek (Wroclaw, Polska)

---

### Post by shrift on 2006-06-30
Skype does not support software audio mixing.  Mplayer I believe should work, but I could be wrong.

Basicly if skype is running, then it will take over the soundserver, instead of sharing it properly. It's a known problem with Skype.

---

### Post by Pawel on 2006-07-08
Hello!

Witam i pozdrawiam :)

Dzi&#281;kuj&#281; za odpowiedzi! :)

Thanks for all replies :)

This thread in general sloved my problem:

[http://ubuntuforums.org/showthread.php?t=44753&highlight=dmix](http://ubuntuforums.org/showthread.php?t=44753&highlight=dmix)

Anyway:
I think that i will buy old good sound card like soundblaster 128 PCI. It's just works :) (cause its "real" sound card, although it doesn't have hardware midi support).

Best regards
Pawel

---

