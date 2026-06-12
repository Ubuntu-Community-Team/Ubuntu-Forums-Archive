---
title: "I &quot;love&quot; pulseaudio"
date: 2008-06-10
forum: Desktop Environments
---

### Post by Phristen on 2008-06-10
When I watch Youtube and a movie (doesn't matter which player I use) at the same time, I only have sound in one of them - whichever was launched first.

Needless to say, I would like to fix this, but I don't know how :confused:

---

### Post by FuturePilot on 2008-06-10
The solution is to use libflashsupport which fixes this behavior since Flash still doesn't work well with PulseAudio. However the version in the repos is buggy and was removed as a dependency of flashplugin-nonfree. You can still install it however I won't guarantee you will have a pleasant browsing experience because it will most likely cause extremely frequent browser crashes.

---

### Post by sdennie on 2008-06-10
I believe you may also be able to bypass pulseaudio and go directly to alsa (if I understand how pulseaudio works) by going to System->Preferences->Sound and changing everything to use ALSA instead of pulseaudio.  If you are using a non-gstreamer based player, you may have to do something similar in that player.

---

