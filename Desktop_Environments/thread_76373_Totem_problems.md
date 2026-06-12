---
title: "Totem problems"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Dillius on 2005-10-15
I'm trying to play some videos with Totem Movie Player, and I continue to get the following error:

Failed to play: Could not open resource for writing.

Anyone know what is wrong with it?

---

### Post by Dillius on 2005-10-15
Nevermind, I'm an idiot. I was trying to use Totem in KDE. How do I go about changing the default media player in KDE? The settings are saved so that Totem is the default, though I can't use it obviously.

---

### Post by doclivingston on 2005-10-15
The problem is that something else (probably arts) is using the sound card.

I'm not sure if it would be installed in KDE, but running the program "gstreamer-properties" and setting the default audio sink to arts, should fix the problem.

---

### Post by Dillius on 2005-10-15
Well from my past experiences, I'd really prefer not to use Arts and keep using ALSA. Maybe I can just find a way to disable Arts entirely.

---

### Post by Dillius on 2005-10-15
Though still, the main thing I simply want to change are the file associations. I used to know how to do this in KDE 3.2 but now I can't find the section for File Associations any more.

---

