---
title: "GStreamer problem"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Alienist on 2006-07-04
I booted up Ubuntu and out of the blue GStreamer is apparently broken. None of the apps that use it will play back. In Amarok I get an error regarding "gstosssink." Any ideas? So frustrating...

---

### Post by thasheep on 2006-07-04
Press <Alt>F2 and the run dialogue will open. Type in "gstreamer-properties" (without the quotes) and press enter.
Now, choose different options for the audio default output plugin. With each one click "test" and you should hear a sound. For me, Auto and ALSA work - the others do not.

If this still doesn't fix your problem, are you sure it's only gstreamer? Install mplayer, totem-xine or xmms (using synaptic/apt-get) and see if you can hear things now (with mplayer, totem or xmms in Applications>Sound and Video).

---

### Post by Alienist on 2006-07-04
[QUOTE=thasheep]Press <Alt>F2 and the run dialogue will open. Type in "gstreamer-properties" (without the quotes) and press enter.
Now, choose different options for the audio default output plugin. With each one click "test" and you should hear a sound. For me, Auto and ALSA work - the others do not.

If this still doesn't fix your problem, are you sure it's only gstreamer? Install mplayer, totem-xine or xmms (using synaptic/apt-get) and see if you can hear things now (with mplayer, totem or xmms in Applications>Sound and Video).[/QUOTE]

Thanks for replying. I did as you recommended and when I test all the plugins I get a message saying [COLOR="Red"]Could not open resource for writing.[/COLOR] Also, the xine engine *is* working as gXine and Amarok with the xine engine work fine. Any more thoughts?

---

