---
title: "A couple isues"
date: 2009-03-25
forum: General Help
---

### Post by SpitfireSMS on 2009-03-25
Iv had Ubuntu 8.10 for around a couple months and recently my sound has stopped working somewhat.
Its interesting because it works 100% through headphones, but when switched to the laptop's speaker it cuts out occasionally, sometimes for hours.
It always seems to come back on restart, and then goes out pretty quickly.


The second issue I have occurs when I try to bring up the shutdown/restart/suspend menu.
It pops up telling me that vlc is playing a media file so it cannot shut down, even though I have not used vlc and theres no vlc process running.

Any ideas?

---

### Post by mb_webguy on 2009-03-25
The two could be related, particularly if VLC is using the wrong audio output plugin.  Go into the VLC preferences and change the audio output plugin.  If you don't see one for Pulse, open Synaptic and install "vlc-plugin-pulse".

How are you checking for VLC processes?  When you're having problems with the sound, try "killall vlc" in the terminal.

---

### Post by SpitfireSMS on 2009-03-25
i did not have pulse, I installed it and enabled it.
I can't tell you if it worked yet, but my sound has been working for now so it seems ok.

I was using the system monitor, but I will try the killall next time.

---

