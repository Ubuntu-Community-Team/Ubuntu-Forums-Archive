---
title: "amarok engines"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Vlatko on 2006-09-29
i have amarok 1.4.3 installed and the only engine i can select is the xine engine. can i try out different engines? in 1.3 versions i could select multiple engines. xine plays everything but i don't like the output i get. i have 5.1 speakers and only the front two are used, no matter what i select in the preferences/engine/output. in all other programmes all channels are working; xmms, mplayer, totem...

i love the output i get from xmms, much like winamp, but amarok is just...wow! i really like it's options but i can't use a audio program that doesn't give me the correct sound.

it'd be best if i could somehow use xmms output engine in amarok.

---

### Post by asimon on 2006-09-29
Currently the only supported engine is xine. Amarok used to support a gstreamer engine too, but it had some problems which never got fixed and an API which changed every other week didn't helped either, thus it's no longer supported.

You definitely can't use xmms' output mechanism with amarok.

---

### Post by Vlatko on 2006-09-29
> **asimon said:**
> Currently the only supported engine is xine. Amarok used to support a gstreamer engine too, but it had some problems which never got fixed and an API which changed every other week didn't helped either, thus it's no longer supported.

You definitely can't use xmms' output mechanism with amarok.
i figured as much. i don't understand why i get output from only 2 channels in amarok. every other programme works well, all 6 channels working. in amarok i can change the settings of the speakers but to no avail, whichever setting i use makes no difference.

---

### Post by asimon on 2006-09-29
> **Vlatko said:**
> i don't understand why i get output from only 2 channels in amarok. every other programme works well, all 6 channels working.
Yes, I can't help you here, sorry. I only have 2 speakers and thus never had this kind of problem. But if I remember correctly I read somewhere that you need to configure the speaker config to "pass through" in Amarok instead of 5.1 (mp3s and most oggvorbis have only 2 channels, thus the front channels need to be duplicated to the rear ones).

There are also some threads like [ Configuring 5.1 sound channels for mp3 playback](http://www.ubuntuforums.org/showthread.php?t=184814) which edit the ~/.asoundrc config file.

---

