---
title: "Two random video problems/questions"
date: 2005-06-27
forum: Desktop Environments
---

### Post by biffurt on 2005-06-27
First, divx - how the devil do I install it? I downloaded their installer and ran it (./install.sh) from the terminal, but divx files still won't play in totem - it still doesn't know how to handle them. I can't find any documentation on their website on how to install either.

Second, a video problem - playback of even low resolution movies is pretty choppy and out of synch. Is there an easy fix for this?

---

### Post by Lunde on 2005-06-27
[QUOTE=biffurt]First, divx - how the devil do I install it? I downloaded their installer and ran it (./install.sh) from the terminal, but divx files still won't play in totem - it still doesn't know how to handle them. I can't find any documentation on their website on how to install either.

Second, a video problem - playback of even low resolution movies is pretty choppy and out of synch. Is there an easy fix for this?[/QUOTE]
 [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Maybe this will help, and do look around a bit, this page is excellent

---

### Post by biffurt on 2005-06-28
I did everything on that page re: codecs, and a bunch of other stuff besides. No dice. To try to fix the divx thing, i installed the libdivx4linux package via apt-get, but it's still not working. Do I have to do anything to totem to point it to the codecs or something? Specify which codec to use for each file? I'm really lost here.

---

### Post by tread on 2005-06-28
If you are in Hoary, try installing wxvlc. I think its a better player than totem and may even sort out your problem.

---

### Post by biffurt on 2005-06-28
Wow, holy crap wxvlc is kicking totem's ass in terms of video quality and speed. The codecs are working now, which is great - problem is, the sound isn't. Running it from the terminal, I get this error:

VLC media player 0.8.1 Janus
[00000241] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:160
[00000244] oss audio output error: cannot open audio device (/dev/dsp)
[00000244] main audio output error: couldn't find a filter for the conversion
[00000244] main audio output error: couldn't set an output pipeline

Any ideas?

---

### Post by tread on 2005-06-28
Check the output plugin in wxvlc, if you are running esd, it should be set to esd else alsa.

---

### Post by biffurt on 2005-06-28
I think I'm running oss, but I'm not sure. How do I find out? Sorry, I'm completely new to this.

---

### Post by biffurt on 2005-06-29
Bump. Can anybody help me out?

---

### Post by Lunde on 2005-06-29
[QUOTE=biffurt]Bump. Can anybody help me out?[/QUOTE]
 does none of them work, no sound at all?

System -> Preference -> Sound

This shouls get you going. 

Howto: about sound in Hoary & Linux
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Hear multiple sounds in Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Index of howto's
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

If it still won't work, you have a special soundcard that requires drivers. Then we need to know the full name and model to help you further

Hope thsi fixed your problem

---

### Post by biffurt on 2005-06-29
First off, thank you for the links, Lunde. Very informative. I figured it out - I didn't have a esd plugin installed for wxvlc. #-o Everything's working grand now, thanks so much for your help.

---

### Post by Lunde on 2005-06-29
Glad everything is OK for you. I learnt something myself to in this tread, the VLC is a better player then Totem, had a problem with sound sync in Totem earlier

---

